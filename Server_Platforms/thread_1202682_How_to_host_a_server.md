---
title: "How to host a server"
date: 2009-07-02
forum: Server Platforms
---

### Post by xusword on 2009-07-02
Hi

How do I host a server?

We have a few computer under the same router and it seems they can't ping each other.

I have installed firestarter and allow Ubuntu to accept incoming connection from another computer's IP (i.e. 192.160.0.102) and I guess that's not the solution. I still cant ping my computer from that machine.

I have no idea what I am doing, please help.

thanks

---

### Post by WRDN on 2009-07-02
I would recommend installing LAMP (Linux, Apache, MySQL, PHP)- this is for websites.
For sharing files, look to [SAMBA]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by xusword on 2009-07-02
thanks

How about Oracle

How would I make allow Oracle listener visible to the entire network?

---

### Post by wojox on 2009-07-02
Sounds like you need port forwarding switched on your router.

---

### Post by xusword on 2009-07-02
Port forwarding... that sounds about right. Even I have never used it before

Too bad I don't have my router here... My landlord's got it...
I think I will try it in the future

---

### Post by Celauran on 2009-07-02
You shouldn't need port forwarding for machines connected to the same router, only for connections coming in from the outside. How are you pinging; by IP or by hostname? Have you tried with your firewall(s) turned off? Are you able to ping the router?

---

### Post by philcamlin on 2009-07-02
install pache and port forward and then get dndns for free and host your ip:popcorn::popcorn:

---

