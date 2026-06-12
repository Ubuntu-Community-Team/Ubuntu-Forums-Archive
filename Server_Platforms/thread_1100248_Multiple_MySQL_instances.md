---
title: "Multiple MySQL instances"
date: 2009-03-19
forum: Server Platforms
---

### Post by jennyw on 2009-03-19
I was wondering if there's a best practice for installing multiple MySQL instances. My understanding from reading the MySQL manual is that for 5.0, the best way is to use mysqlmanager. Both the MySQL manual and Ubuntu's manpage for mysqlmanager say that you the init script normally defaults to using mysqld_safe, but can be changed by making changes to my.cnf (particularly adding a section called [mysql.server] and adding use-manager to it). However, this doesn't work and, looking through the init script, I don't see any reference to mysqlmanager. So ... I could go ahead and edit the init script, but first I thought I'd check and see if someone had any other ideas. I would guess that this would be a common enough issue.

Thanks!

---

### Post by windependence on 2009-03-19
Any particular reason why you want multiple instances?

-Tim

---

### Post by jennyw on 2009-03-19
Setting up a backup server for multiple MySQL servers. Since an instance can replicate only one other instance, we'll need multiple instances on the backup server. Unless there's a better way to do this?

---

### Post by windependence on 2009-03-19
Sure there is. Virtualization. Set up a VMware ESXi box and run as many MySQL servers as you want. Then, replicate to them.

You could also use chroot jails to run each instance of MySQL, but I have never done that on Linux, just on FreeBSD.

-Tim

---

### Post by SteveClement on 2009-03-20
Well spawning more Virtual Machines is a bit overkill.

There is a MySQL config Parameter:

[mysqld_multi]

which runs the program:

mysqld_multi


and there you can have multiple instances on seperate TCP ports and seperate DB'dirs.

An advanced warning, this doesn't work out of the box on Ubuntu* Flavors.

cheers

---

### Post by jennyw on 2009-03-20
Thanks, Steve! I'll check that out. I saw mysqld_multi mentioned in the docs, but it looked like mysqlmanager had replaced it (as far as MySQL was concerned, at least; Ubuntu/Debian seems to have different ideas).

I might just have to rewrite the init script. I do find it odd that if Ubuntu/Debian changed the way multiple instances are setup that they didn't update the documentation ... aren't Debian man pages typically updated to reflect the changes made in packaging?

---

### Post by windependence on 2009-03-20
> **SteveClement said:**
> Well spawning more Virtual Machines is a bit overkill.

There is a MySQL config Parameter:

[mysqld_multi]

which runs the program:

mysqld_multi


and there you can have multiple instances on seperate TCP ports and seperate DB'dirs.

An advanced warning, this doesn't work out of the box on Ubuntu* Flavors.

cheers

I don't know why? It wouldn't be overkill on my ESXi box, I just clone the vm and change the IP and viola, I have another server. Since I run most of my SQL servers on FreeBSD, there is little more resource use. It's quick and painless and much easier to maintain IMHO.

-Tim

---

### Post by john_spiral on 2009-10-23
Have a look at this months LinuxUser magazine (linuxuser.co.uk), they have a four page article on this very topic.

---

