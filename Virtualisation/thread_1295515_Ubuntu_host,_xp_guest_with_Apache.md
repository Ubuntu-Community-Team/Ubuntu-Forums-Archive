---
title: "Ubuntu host, xp guest with Apache"
date: 2009-10-19
forum: Virtualisation
---

### Post by sesl on 2009-10-19
I have Ubuntu 8.10 as my main OS. I have Virtualbox installed with XP Pro SP2 as a guest. I have installed Apache 2.2, Mysql, PHP 5 on XP. It all works tickety boo. What I would like to do next is access the localhost on XP from the host Ubuntu. How do I set that up? I think I have to open up a port or 2, but I don't know how to do that.

Thanks in anticipation.

---

### Post by sesl on 2009-10-21
Well, nobody replied, so off I went looking around as you do. And I've sorted it myself. Not from this forum, but from another very helpful straight forward one. So if you want to know how I did it, tough.

---

### Post by n3v3r on 2009-11-25
HI, I'm in a similar situation. I'm using VirtualBox with Ubuntu as the Guest OS and Windows Vista the Host. The network type is NAT. 

I have Apache running in the Guest OS at port 80 and able to connect to apache with in the Guest OS. The issue is that I am unable to connect to Apache running in the Guest OS through Host Browser. Can you help!

---

### Post by Cheesemill on 2009-11-26
You need to set up your VM with bridged networking instead of NAT.
This way it will pick up it's own IP address instead of sharing one with the host machine.

---

