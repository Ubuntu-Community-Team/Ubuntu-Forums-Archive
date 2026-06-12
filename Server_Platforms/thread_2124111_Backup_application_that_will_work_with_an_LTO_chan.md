---
title: "Backup application that will work with an LTO changer"
date: 2013-03-09
forum: Server Platforms
---

### Post by MakOwner on 2013-03-09
Looking for an out-of-the-repository backup application that will work with an older SCSI attached tape changer.
I have an old Dell PV122T 8 slot changer with an LTO2 drive in it.  

I'm looking for something that either installs and recognizes this, or has available simple, direct instructions on getting working.
I want to back up to the server it's attached to from other servers, but if I have to mount remote filesystems via NFS that's cool tool. 


I tried setting up Bacula, with no luck.  Horribly overcomplicated process and none of the guides and docs I found seem to talk about consistent versions.

---

### Post by Cheesemill on 2013-03-10
Take a look at [Amanda]("http://www.amanda.org/").

---

### Post by MakOwner on 2013-03-10
> **Cheesemill said:**
> Take a look at [Amanda]("http://www.amanda.org/").

I did.

I have setup some fairly complicated applications before - Tivoli Storage Manager I can do from memory - I started looking at Amanda and broke out in hives.
Maybe it's just because I'm starting with the Amanda in the Ubuntu repostories?
I have not found anythig on disk after installing on ubuntu that comes even close to looking like the documentation.

Is there a better distribution to start from?

---

### Post by koenn on 2013-03-11
There's a generic commadline tool for working a tape changer : mtx
(pacjkage name is also mtx)

in short, your tape changer should be known to you OS as a device (you'll have to find out which device name it is lnown as),
and then you use mtx to drive the robot, and mt to work with the LTO tape itself.
for backups, you need a program that can write to e device (rather than a filesystem) - eg. tar

It wouldn't surprise me if backup solutions like Amanda and Bacula can encapsulate all that, but maybe it helps if you know what you're looking for.

Here are some snippets from a backup script that uses an LTO robot : maybe you can see if something similar works with yours

```

tapedevice="/dev/st0";
taperobot="/dev/sg1";

# slots -  the slot in your tape magazine. You may want some logic to decide on what slot the tape comes from in stead of a hard number
# and you can store the tape in a different slot  than where it came from

$slot_from=1
$slot_to=1



#  show robot status
 mtx -f $taperobot status 

# load tape
mtx -f $taperobot load  $slot_from     0  

# do backup
cd /some/path
tar c $tar_opts   -f $tapedevice    *

# unload tape
mt -f $tapedevice rewind                 ;# maybe not needed for LTO?
mtx -f $taperobot unload $slot_to    0  


```

those are the basics, 'man mtx' explains  lots more


-----
for remote backups : the easiest is probably to  mount the backup source on  the machine the tape device is attached to

you can also do it the other way around, i.e. send a backup to a "remote" tape (but the problem with that is that you also have to remotely control your robot for loading and unloading tapes)

[http://docstore.mik.ua/orelly/unix3/upt/ch38_08.htm](http://docstore.mik.ua/orelly/unix3/upt/ch38_08.htm)
[http://docstore.mik.ua/orelly/unix3/upt/ch38_07.htm#upt3-CHP-38-SECT-7](http://docstore.mik.ua/orelly/unix3/upt/ch38_07.htm#upt3-CHP-38-SECT-7)

---

