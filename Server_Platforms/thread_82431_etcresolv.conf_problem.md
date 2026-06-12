---
title: "/etc/resolv.conf problem"
date: 2005-10-26
forum: Server Platforms
---

### Post by Amen on 2005-10-26
I've just installed ubuntu and the instalation went out just fine :)

My problem (besides not playing mp3's :P) is with my internet connection. I connect to the internet via an ethernet router using dhcp. It did ping everything, but i couldn't open webpages or resolve ftp adresses...! So i figured i had to edit /etc/resolv.conf with my ISP nameservers. 

Once I did, it all worked fine! 

The thing is... 5 minutes later /etc/resolv.conf got re-written with my local ethernet router nameserver and i couldn't resolve adresses again :( my idea is to make up a cron job for that... but it somehow looks like a stupid thing to do.

Any ideas?

---

### Post by sanjose on 2005-10-26
edit your **/etc/dhcp3/dhclient.conf**

add :[INDENT]**prepend domain-name-servers** [I]"IP address"
  
IP address your ISP nameservers
  
[/I]if you have two ISP nameservers
make another line
  
  **prepen domain-name-servers ***"IP address"*
 [/INDENT]

---

### Post by joselin on 2005-10-26
Try [this]("http://www.ubuntuforums.org/showthread.php?t=19510&highlight=resolv.conf+chattr").

Regards

---

### Post by Amen on 2005-10-26
thx! problem solved! :)

---

