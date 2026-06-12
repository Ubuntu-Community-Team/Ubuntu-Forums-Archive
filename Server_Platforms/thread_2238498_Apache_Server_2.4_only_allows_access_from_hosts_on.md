---
title: "Apache Server 2.4 only allows access from hosts on the local network"
date: 2014-08-08
forum: Server Platforms
---

### Post by Chuong_Pham on 2014-08-08
Hi guys, I am using Ubuntu 14.04 on Virtual Box with Bridged network mode(Window 8 is host). I am trying to configure my Apache server so that any devices connect to my network (wifi) would be able to access my website. My attempt using outer IP "Require ip xx.xxx.xxx.xxx" is successful. However, it is a dynamic IP. I tried to make my other laptop with an internal IP of 192.168.2.2 by "Require 192.168.2.2" but in vain. My Ubuntu's internal IP is 192.168.2.6.
Thank you.

---

### Post by TheFu on 2014-08-08
Make the ubuntu system have a static ip.
Either access the website using that IP or put it into the equiv of the /etc/hosts file on all the client machines.

If going by IP fails, perhaps there is a firewall enabled or apache is limited to localhosts-only connections?  Might be useful to post the config file inside the sites-enabled/ directory to get more help. Please use "code tags"

---

