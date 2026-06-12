---
title: "VPN on Ubuntu Server 10.04"
date: 2010-05-04
forum: Server Platforms
---

### Post by computerman88 on 2010-05-04
I am trying to setup a VPN on Ubuntu Server 10.04 with Webmin installed but I can't get the PPTP VPN Server installed. I am not sure what to do now. Is there a better way to configure an VPN on Ubuntu if so please post. Thanks for the help. Is Ebox a good option?

---

### Post by 1234dran on 2010-05-05
pptp is the easiest  vpn to set up, however it is not the most secure. To set up the point to point protocol on ubuntu for the server enter a terminal and type:
 
**sudo apt-get install network-manager-pptp **
 
**sudo gedit /etc/ppp/chap-secrets**
 
enter the username for the client under the word client
 
enter **pptpd** under the word server
 
enter the password for the client under the word secret
 
and enter ***** under IP address or the ip address of the client if the client's ip address is static
 
re-enter terminal and type:
 
**sudo apt-get install pptpd**
 
**sudo gedit /etc/pptpd.conf**
 
scroll down until you see the first #localip: 192.xx.xx.xx (it won't show this ip address but simply for the sake of anonymity bear with me) and change the ip address to the ip address of the ubuntu machine you want to be the server and remove the pound sign. On the next line, change the remote ip address to the ip address of the client/clients and remove the #
 
 
Back in the terminal type:
 
**sudo /etc/init.d/pptpd restart**
 
Do you need help with the client?

---

### Post by noway2 on 2010-05-05
OpenVPN works well, is easy to setup, and is secure (the hand shaking and packet exchange are encrypted).  It also has some good documentation regarding a how to.  See these two threads: [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN) and [http://ubuntuforums.org/showthread.php?t=1021592](http://ubuntuforums.org/showthread.php?t=1021592).  I followed them and had openVPN working as a bridge connection in an hour with a minimum of fuss.

There is also a newer GUI based edition, but you are limited to two simultaneous clients under the 'free' version.  The charge for additional client licenses is modest, though.

---

### Post by noway2 on 2010-05-05
computerman88, by the way, what part of NC are you from?

---

