---
title: "small server setup possible? (64mb)"
date: 2010-01-05
forum: Server Platforms
---

### Post by jpgeerets on 2010-01-05
hi folks,

i got an old server with a 64mb flash-disk in.
this seems to be the boot-disk.
would it be possible to get ubuntu server on this?
there is also an ide-disk in.
in my opinion it should be good to boot of the flash disk and put the /home or /srv on the ide disk.
someone any ideas about this?

thanks in advanced!

Jean-Paul

---

### Post by BkkBonanza on 2010-01-05
Well, how big is the IDE disk? I don't think you'll get away with Ubuntu server on 64 MB only. Though it could be close, even the minimal install uses >100 MB now I think. There are smaller Linux distros like DSL that may be better suited. After all, my Linksys router uses something like 32MB for Linux.

Also how much RAM is there available?

---

### Post by jpgeerets on 2010-01-11
well,

i dont know the specs until the bit, but, the ide-disk is some gb's.
it is also easy to place a new / other ide disk which is big enough.
but, i thought it would be a nice idea to put the server software on a 64mb flashdisk.

---

### Post by HighCommander540 on 2010-01-11
> **jpgeerets said:**
> well,

i dont know the specs until the bit, but, the ide-disk is some gb's.
it is also easy to place a new / other ide disk which is big enough.
but, i thought it would be a nice idea to put the server software on a 64mb flashdisk.

Yeah, there are other distros that will allow you to put it on something that small. Not Ubuntu though.

---

### Post by jpgeerets on 2010-01-11
wow...
fast reply.

any suggestion what distro?

---

### Post by volkswagner on 2010-01-11
If you just need a file server you may consider FreeNas.  Choose embeded to run from flash, as it will run in RAM and not trash the CF card.

[http://freenas.org/documentation:setup_and_user_guide:hardware_requirements](http://freenas.org/documentation:setup_and_user_guide:hardware_requirements)

---

### Post by Lars Noodén on 2010-01-11
As @ volkswagner said, FreeNAS is an option.  

DamnSmall Linux, Puppy Linux, and Slitaz are other options.  
Slackware might be customizable enough. uClinux is often used for small, embedded systems. 

Or if you know which application(s) you want you can roll up something in BusyBox, which is also often used for embedded systems.  

One item to remember is that some directories must be read-write, like /proc, /tmp, /dev, /var/tmp, and /var/log

---

### Post by HighCommander540 on 2010-01-11
> **Lars Noodén said:**
> As @ volkswagner said, FreeNAS is an option.  

DamnSmall Linux, Puppy Linux, and Slitaz are other options.  
Slackware might be customizable enough. uClinux is often used for small, embedded systems. 

Or if you know which application(s) you want you can roll up something in BusyBox, which is also often used for embedded systems.  

One item to remember is that some directories must be read-write, like /proc, /tmp, /dev, /var/tmp, and /var/log

+1 FreeNAS and DamnSmall.

---

### Post by lykwydchykyn on 2010-01-11
Last time I installed dsl on a flash media it required about 90 MB IIRC.

Try tinycore; its only 10 mb and has a more modern kernel (and a nicer GUI, though that's probably irrelevant here).

---

### Post by Lars Noodén on 2010-01-12
@ lykwydchykyn : thanks for pointing out tinycore.  It looks like an interesting use of BusyBox and especially the 6MB no-graphics version.

@ jpgeerets : another option which might be possible would be to use the flash for /boot and put everything else on the hard drive.  That won't really conserve any space, rather the opposite, when compared to the embedded distros, but it would possibly allow you to run Ubuntu server or plain old Debian. On a server, I would lean towards Debian-stable.

---

