---
title: "VMware server error 503"
date: 2010-09-26
forum: Virtualisation
---

### Post by ani0079 on 2010-09-26
Hello Guys I've got a strange problem. I've recently installed vmware server 2.0.2 x64 on ubuntu 10.04 x64 but it succeded after making some google search and finding solution of applying ubuntugeeks patch which was mentioned here [http://hmontoliu.blogspot.com/2010/04/installing-vmware-server-202-in-ubuntu.html](http://hmontoliu.blogspot.com/2010/04/installing-vmware-server-202-in-ubuntu.html) but after success of installation the remote console of web access doesn't work so again i searched and found out that i have to use older version of firefox so i installed firefox 3.5.9 with ia32libs it worked but after rebooting it gave me error "503 service unavailable" and in my vmware log i found reason that "connection refused" by vmware server so i've to reconfigure vmware server by running ./vmware-config.pl after that i was able to access vmware server as well as remote console but again after rebooting it gave me same error "503 service unavailable"
I really dont know how to solve this problem permanently.
Any help will be more than welcome..
Thanks in advance

Aniruddh Katkar

---

### Post by curioshop on 2010-10-01
you may want to try enabling ssl v2 in firefox's about:config page.

---

