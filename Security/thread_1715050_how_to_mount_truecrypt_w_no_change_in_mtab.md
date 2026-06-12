---
title: "how to mount truecrypt w/ no change in mtab?"
date: 2011-03-26
forum: Security
---

### Post by fbs777 on 2011-03-26
I need to mount a truecrypt volume but when force power off and put the hd as slave in another linux anyone can see where the volume was mounted just watching the mtab file.

Mount command has an option (-n) to not write on mtab file, but in trucrypt i dont know how...

How to mount a truecrypt volume without change/write in /etc/mtab (in command line, not gui)?

in google i found this, but i dont know exactly what this does:

> Linux TC Stealth Install

 - Install TrueCrypt binary, rename to something innocuous (e.g.
/etc/rmt)

 - Create a large le (e.g. /var/tmp/.tmp1337), make TC
volume in it

 - On boot, use command line to open/mount it, then run script:
mp=/media/truecrypt1; cp /etc/mtab $mp/etc/
for i in bin etc home lib opt root sbin srv usr; do mount -o
bind $mp/$i /$i done

---

