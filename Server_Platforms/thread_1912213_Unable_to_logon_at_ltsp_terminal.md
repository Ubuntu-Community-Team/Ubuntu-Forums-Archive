---
title: "Unable to logon at ltsp terminal"
date: 2012-01-20
forum: Server Platforms
---

### Post by ITJeff on 2012-01-20
Hi
 
I have just built my first Ubuntu server with LTSP installed. All has gone fine up to booting first terminal.
 
It boots to the login screen, has an IP from DHCP (bottom right of screen), you enter user name and password. After a pause I get the message 'response from server, restarting' and the client duly restarts.
 
sudo ltsp-update-image
 
and
 
sudo ltsp-update-sshkeys
 
and
 
/var/log/auth.log 
 
has no indication of an attempt to login
 
I am using edubuntu 11.10
 
Any thoughts plaese, I am very new to this so I will need explaniations.
 
Thanks

---

### Post by ITJeff on 2012-01-21
Ok, so I started again, and rebuilt the server from the DVD, and it works, terminals boot and I can login.
 
But then I want to change the IP of the server from the default so edit
  /etc/network/interfaces
Change settings to give new IP and run
 /etc/init.d.networking restart
Networking restarts and binds to eth0 again and ifconfig gives the corect results
 
Next DHCP, so edit
 /etc/ltsp/dhcpd.conf
Run
 /etc/ltsp/isc-dhcp-server restart
 ltsp-update-sshkeys
 
All appears fine, restart terminal, boots, get IP from new range and get to login screen
 
I have now broken it, same as above !!!!!
 
Reversing all the config changes brings it back working
 
I must have missed something important in IP change process but cannot find out what.
 
Any thought would be appreciated.
 
Thanks

---

### Post by ITJeff on 2012-01-21
SOLVED :KS
 
I was missing 
 
ltsp-update-image

---

