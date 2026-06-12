---
title: "apache issue?"
date: 2008-05-22
forum: Server Platforms
---

### Post by esseacca on 2008-05-22
Hi all.

I installed gutsy server base, then ssh, then I went through the following [https://help.ubuntu.com/community/Joomla?highlight=%28joomla%29](https://help.ubuntu.com/community/Joomla?highlight=%28joomla%29) 


My server is a vmware VM, with a 192.168.1.30 IP (bridged IP on my workstation with IP 192.168.1.20) behind firewall - ISP router

Install process was fine. I go to [http://192.168.1.30/joomla](http://192.168.1.30/joomla) from my workstation and get to Joomla Front Page.... good!!

Now I want my Joomla site to be visible to my friends. Go to router admin page, set port forwarding for port 80 to 192.168.1.30 and go back to firefox, [http://mypublicIPaddress/joomla](http://mypublicIPaddress/joomla) and it doesn't work.

I can see [http://mypublicIPaddress/](http://mypublicIPaddress/) with Index of and apache2-default and joomla directories (how can I hide this/redirect to Joomla Front page?)
From here If i click on joomla directory I get my browser stuck saying " Redirection to [http://mypublicIPaddress](http://mypublicIPaddress) and waiting forever....

Any ideas how to fix this? Need more details?

Thanks all

---

### Post by freebeer on 2008-05-22
It sounds like your router isn't redirecting -- most don't.  Can your friends access yourpublicipaddress/joomla from outside your LAN?  From within your lan, if you want to access the web server, you can use the local IP addy, or add the domain name into your /etc/hosts file.

On the computers within my LAN, I've edited my /etc/hosts file to include the line:

192.168.1.103  mydomainname.org

^^ the above IP being the static IP address of my web server machine on my LAN.

---

### Post by esseacca on 2008-05-26
I solved this...

I tried to simulate my friend's access to the webserver with a different public IP address as source. I set a proxy for firefox ( proxy found with google quickly) and it works; I can access my joomla test install !!! And my friends as well.

Still I get FF to hung for ever on a "Redirection to..." if I go out directly

Problem is on SOURCE_IP=DESTINATION_IP , both being my public IP address

---

