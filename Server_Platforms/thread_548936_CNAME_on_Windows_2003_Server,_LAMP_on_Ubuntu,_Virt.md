---
title: "CNAME on Windows 2003 Server, LAMP on Ubuntu, VirtualHosts, no remaing hair..."
date: 2007-09-11
forum: Server Platforms
---

### Post by kpm on 2007-09-11
Hi, I have been struggling with configuring an Ubuntu 6.06 LAMP server in an all Windows environment for a couple of days now... 
The goal is to get the Drupal CMS up and running using clean urls and virtual hosts.  Drupal CMS is up and running, but clean urls and virtual hosts are only working on the local server box, not on clients in the LAN.
I have a Windows 2003 server set up with clean urls and virtual hosts.  The LAN domain controller is a Windows 2003 server, so I created a CNAME Alias for the drupal site and pointed it to the Ubuntu LAMP server but cname alias does not seem to work like it does for WAMP installs on the network.  I am using Samba to bring the Ubuntu server into the domain, but still am getting no where with having the CNAME alias resolve to the urls when entered in browsers on other computers besides the server it self.  Any one out there have any success with such a thing in such an environment??  Please help.

Thanks

---

### Post by kpm on 2007-09-14
ID10T error... this is sorted out.  The ahost was not created... sigh

---

