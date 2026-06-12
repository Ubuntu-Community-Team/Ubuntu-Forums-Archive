---
title: "Cloning a server"
date: 2012-09-21
forum: Server Platforms
---

### Post by cesar98026 on 2012-09-21
[LEFT]What is the best way to clone a server? Files and OS, everything.[/LEFT]

---

### Post by jerrrys on 2012-09-21
[clonezilla]("http://clonezilla.org/")

won't do raid

---

### Post by cesar98026 on 2012-09-21
I've been reading that dd command is the way to go. How do you dd over SSH? :guitar:

---

### Post by koenn on 2012-09-23
[http://serverfault.com/questions/51567/how-to-set-up-disk-cloning-with-dd-netcat-and-ssh-tunnel](http://serverfault.com/questions/51567/how-to-set-up-disk-cloning-with-dd-netcat-and-ssh-tunnel)

the simpliest invocation would be something like
```
dd if=/dev/sdX bs=1M | ssh root@dstMachine " dd of=/dev/sdY bs=1M"
```
but be careful what you wish for.



Depending on what you think "best" means, a clonezilla life CD might be best.

---

### Post by LHammonds on 2012-09-24
Cloning?  As in taking one server and mass-produce a bunch of identical servers...I don't know.  I have always been of the mindset to create each new server from scratch.

If you are just talking about backup and restore to a backup server in the event of a disaster, I use a combination of LVM + LVM Snapshot + FSArchiver.  I have a click-for-click guide in my sig that covers it.

LHammonds

---

