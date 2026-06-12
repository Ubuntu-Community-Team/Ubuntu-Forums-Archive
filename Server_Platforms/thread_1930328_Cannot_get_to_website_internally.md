---
title: "Cannot get to website internally"
date: 2012-02-23
forum: Server Platforms
---

### Post by dan40 on 2012-02-23
Hi, my ISP just upgraded my internet service to the next higher level, but in order to take advantage of this, I had to get a new modem/router.  They supplied me with the **SMCD3GN** wireless modem with built-in router.  I installed Ubuntu 11.10 server with all of the updates on a spare workstation and opened these ports using NAT: 80 for WWW, 21/22 for FTP & SSH, and 25/110 for mail.  I have the firewall service set to OFF (I will be using the internal firewall later).  My problem lies here... for the life of me, I cannot get my FQDN to resolve internally.  For example, if I go to my [www.domainname.com]("http://www.domainname.com") using Firefox or IE, in theory I should see the "It Works!" index page coming from /var/www.  It will not resolve.  However, if I enter the internal 192.168.x.x address, I can see it.

When I had my last modem using the old internet service, it worked just fine.  I can ping my IP address or my domain and get successful results, so I really don't have a clue what's preventing me from seeing my site internally.  Given it's a new modem, there might be something I'm forgetting to set up but I just can't put my finger on it.  I had a friend try it from outside my home and he can get to my site with no problem.

Might anyone have this same modem that can perhaps assist me in getting this thing working internally?  It's driving me up the wall.  Could it be that I likely have something in my /etc/hosts file that's not set correctly?  I can't find any good instruction on setting this file up.  If anyone can help in this area and help me get it configured correctly, I owe you a Coke.  :)

Thanks a million.
Dan

---

### Post by nsnidanko on 2012-02-27
It seems like you are having DNS issues. Can you please resolve  [www.domainname.com]("http://www.domainname.com/") on the workstation you are having trouble accessing your webserver by domain name?

to resolve name issue the following command:

 [nslookup www.domainname.com]("http://www.domainname.com/")

Post results as well as what DNS server your workstation using.

---

