---
title: "Sync MySQL between Ubuntu and Windows?"
date: 2008-04-30
forum: Server Platforms
---

### Post by LIJI on 2008-04-30
Hey,
I'm a dual booter of Windows XP and Ubuntu.
I run a small home server for internal proposes on both OSes.
Both use Apache, PHP and Mysql (Wamp and Lamp).
Since I switch between the OSes quite often, I wonder if it is possible to have both OSes to use the same database (Or sync them in any way automatically).
Note: Ubuntu got read and write support for the Windows XP partitions.

Thanks in Advance!

---

### Post by Thirtysixway on 2008-05-01
I don't think so.  If you want to share a mysql database between the 2 operating systems, I would suggest either getting a seperate db server.

Personally, if you're running a server you should stick to one OS, less downtime.  Since it's an internal home server, you can get an old box, throw on ubuntu server, and be on your way. :)

---

### Post by hezuo on 2008-10-23
I understand what you're doing. I also dual boot because unfortunately there are some programs that doesn't run properly in ubuntu yet :( . 

I think you must create a symlink. That's what i did to share my php files between xampp and apache2.

---

### Post by goksu on 2008-10-23
you could try the following:

hosting the files in another machine. or

maybe adding a partition both linux and windows can read. then putting the mysql databases on that partition, then setting both mysqls to read from that partition db files. if possible you could set the lamp to read from the ntfsorfat directly.

or use a script both at boot and shutdown to copy the files to ntfs (bad idea if big files or crash).

if you have the time maybe its worth a try. I'd go with one.

---

### Post by minoo1 on 2011-03-16
What do you think about using virtual box. It can be installed on both Operating systems, you can load there some limited edition of ubuntu without desktop managers, only osme console version, and install there mysql, apache and setup phpmyadmin. You can boot the machine everytime you need mysql.

---

### Post by MSPdwalt on 2011-03-16
Dude,

Amazon Ec2, greatest thing since sliced bread.  I have a small instance running Lucid server that I do my dev work on.  Costs me $.50 USD (50 cents US dollars) a month, and that's if I leave it on.  Amazon only changes you for resources used, if you power down your instance and release your elastic IP you pay nothing until you fire it back up.

DW

---

### Post by haafmaad on 2011-03-19
If you use virtualbox to run another operating system you can sync between the two systems but in your case you can't do it dude as windows won't even recognize the ubuntu partition.

---

