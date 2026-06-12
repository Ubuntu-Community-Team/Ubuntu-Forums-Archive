---
title: "can i use multiple lan cards in ubuntu server 8?"
date: 2008-09-12
forum: Server Platforms
---

### Post by machinakias on 2008-09-12
hello everyone..i'd like to ask this: i installed ubuntu server 8 and i 'd like to use two or more lan cards at the same time...is it possible and how can i do this? i want to use this server as dhcp and dns server for linux and winblows clients...any help appreciated...

---

### Post by windependence on 2008-09-12
Of course you can. Just add cards and boot. You'll have to go in and configure them then.

Any reason you think you need a DNS server? You have more than 10 machines?

-Tim

---

### Post by machinakias on 2008-09-12
> **windependence said:**
> Of course you can. Just add cards and boot. You'll have to go in and configure them then.

Any reason you think you need a DNS server? You have more than 10 machines?

-Tim

dear Tim, i have 4 pc's (linux and win) and i want to set up a server to be a dhcp , file and web server...as i know from win2003,i need two cards..one for inbound and one for outbound...thats my thought....there's also a wireless modem-router..so my thought is this...use my router only as modem,use the server for dhcp and also a dns for a domain (just for test....).if i was clear and you think you can help do my thing from the command line,please be my guest!!

---

### Post by erwall on 2008-09-12
> **machinakias said:**
> dear Tim, i have 4 pc's (linux and win) and i want to set up a server to be a dhcp , file and web server...as i know from win2003,i need two cards..one for inbound and one for outbound...thats my thought....there's also a wireless modem-router..so my thought is this...use my router only as modem,use the server for dhcp and also a dns for a domain (just for test....).if i was clear and you think you can help do my thing from the command line,please be my guest!!
You definitely don't NEED 2 nics to do what you want.  Just disable dhcp on your router and install dhcp, bind9, and apache2 on your server.

---

### Post by windependence on 2008-09-12
OK. will catch up with you in about 7 hours. I work nights and have to sleep!

-Tim

---

### Post by machinakias on 2008-09-12
well..ok! and how can i do this hole thing happen? to get my pc's get ip's from my server etc? any ideas whould be a great help....can you give me some steps?  thanx for your time...

---

### Post by cariboo on 2008-09-12
To get a start on things while Tim snoozes have a look at this dhcp server howto:

[http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html)

Jim

---

