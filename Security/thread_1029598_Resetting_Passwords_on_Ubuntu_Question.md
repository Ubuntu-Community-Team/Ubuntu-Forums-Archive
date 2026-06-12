---
title: "Resetting Passwords on Ubuntu Question"
date: 2009-01-03
forum: Security
---

### Post by ronbravo on 2009-01-03
Hi, I am pretty new to ubuntu, using it for about a year now, and I was reading through the psychocats resources page on Ubuntu. I happened to come across this article on resetting your Ubuntu passwords:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

I'm not sure but doesn't this mean that anyone could essentially reset my admin user password while Ubuntu is booting up? If this is the case this seems like a pretty easy way to get into someone's system.

---

### Post by Dave_Connor on 2009-01-03
With loading you can go into grub menu and still put in int=/bin/bash and go into a passwordless shell and be able to change your password that way or use a boot disc. But there a lot of ways messing with root account if someone really wanted to. Bios and grub password along with full disc encryption password would stop someone with physical use but they could just format your partition.

---

### Post by ronbravo on 2009-01-03
Ok, that's good to know. I've been selling friends and family on the idea of switching to Ubuntu and I thought that was a pretty simple and unsecured way of resetting the password of an admin account. It's good to know there is a way to lock that reset point up if need be. Thanks for the info.

---

### Post by 2hot6ft2 on 2009-01-03
You can also put a password on your grub with Start-Up Manager "sum" in synaptic. Then it will be in
System>Administration>Start-Up Manager

---

