---
title: "how to regulate ip addresses and bandwidth/resources to my server?"
date: 2010-07-13
forum: Server Platforms
---

### Post by krack3rz on 2010-07-13
So I run my server from my PC and I don't yet have many people viewing my web site so before I am raped with lots of people trying to connect to me and DL all my stuff I wanna make some restrictions on who I let access them,

firstly, by maximum resources I dedicate to my server per IP and overall

secondly, by which IP I let to connect to me.

It isn't possible to implement both at the same time, I can see that but I really need to be able to have both options because I have random people connecting to me from all over the world and I have no idea how they found me...and I dont need more people I dont know

Help! ](*,) and Thank you!

---

### Post by tyleruk on 2010-07-13
You can set-up your Ubuntu firewall to only allow access from certain IP Addresses, see [https://help.ubuntu.com/10.04/serverguide/C/firewall.html]("https://help.ubuntu.com/10.04/serverguide/C/firewall.html")

As for allocating resources to people that depends on what services you are running, For example with [PureFTPd]("http://www.pureftpd.org/project/pure-ftpd") you can limit each users data?

---

