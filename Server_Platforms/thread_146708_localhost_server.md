---
title: "localhost server"
date: 2006-03-18
forum: Server Platforms
---

### Post by griz on 2006-03-18
Hi,
I'm thinking of setting up a LAMP server in my local network (1xDapper Drake box and 1xWinXP laptop connected to ADSL) for testing purposes.  Questions are: Can I setup a local mail system that does not go out to the internet?  Can the server be given an internal fixed IP address even though my ISP provides dynamic IP address through the modem?

TIA 
Griz.

---

### Post by maddog39 on 2006-03-18
I use LAMPP on my Linux box and my Mac. You can have a local mail server that does not go out to the internet and you wont be able to setup the server to be public with a dynamic IP and most ISPs, for the cheaper accounts like ADSL, DSL, and Cable block incoming port 80 so you might not be allowed to make any public server without a T1/T3 connection.

---

### Post by adamkane on 2006-03-18
Simplest method is to get a router/firewall. The router will use the dynamic external IP address, and then you are free to assign yourself a static internal IP address.

You can run an internal mail server with IP like 192.168.0.10. Use the router to limit access from the external internet, ie allow/block access to ports according to internal/external IP address.

---

### Post by griz on 2006-03-18
Thanks maddog.  I don't intend to put the server on the net at this stage (still have way too much to learn :p ).  I was looking at the howto at [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) and wondering if I could use that to set up my internal mail server.  I'm just using this system to learn how all this is done, so, if I'm being too much of a pain, just let me know.

Griz.

---

### Post by adamkane on 2006-03-18
Also see:
[http://www.howtoforge.net/perfect_setup_ubuntu_5.10](http://www.howtoforge.net/perfect_setup_ubuntu_5.10)

---

### Post by griz on 2006-03-18
Thanks adamkane.  A very comprehensive howto and a good site in general.  Wished I'd known about it before.

Griz.

---

### Post by gmclachl on 2006-03-19
[QUOTE=adamkane]Also see:
[http://www.howtoforge.net/perfect_setup_ubuntu_5.10](http://www.howtoforge.net/perfect_setup_ubuntu_5.10)[/QUOTE]

 I am afraid that tutorial breaks slightly with Dapper. I did use it to set up my own web/mail server it's fairly straightforward.

George

---

