# Vpn Theory
## A different approach to OSMC VPN Usage
#### First of all, how was this not possible before?
  1. The system does not use any native autostart other than, of course, systemd.
  2. The scripts in /etc/network/if-up/ aren't executed, as init.d doesn't run on OSMC
  
  **Clearly the only way to go about this is to create a system service**
  
  Technically, this was always possible -- I have no idea why this wasn't put into use earlier. Simply put, we're
  going to create a systemd service to control the VPN on the system
  
  **First**, let's ssh into our box and download our .ovpn files.
  
  `ssh osmc@myosmcboxaddress`
  
  `sudo apt-get update && sudo apt-get install openvpn`
  
  `cd /etc/openvpn/`
  
  `sudo wget https://nordvpn.com/api/files/zip` (**For NordVPN**)
  
  ###### Now, Let's test.
  
  `sudo openvpn /etc/openvpn/ca12.nordvpn.com.tcp443.ovpn`

   Note how the script will always ask you for your user & pass, we can bypass this by creating a file
   'auth' in the same directory (/etc/openvpn/)
   
   `sudo nano auth`
  
   Enter your NordVPN credentials; your **User Email** on the first line and your **Password** on the second.
    
   CTRL+X and set the file permissions with
    
   `sudo chmod 666 auth`
    
    # To Be Continued...
