---
title: "Make a supercharged distro using tmpfs?"
date: 2009-06-26
forum: The Cafe
---

### Post by monsterstack on 2009-06-26
For those not in the know, you can mount a temporary filesystem in your RAM using the following command:

```
mount -t tmpfs -o 'size=100M' tmpfs /path/to/mount/point
```

I've been fooling around with such things for a few days now, and they are *crazy* fast. Whereas a harddrive will typically write at under 100mb a second and read a little faster, in RAM the speeds are closer to 11,000mb a second read/write. So I was wondering how I could use such things to my advantage. The only downside to these partitions is that they are deleted after you shut-down your computer. But still I wonder if they can't be put to better use.

RAM-disk hardware already exists for servers, and they are used by sites that require a lot of file i/o operations and database work, and they reduce unnecessary writes to the hard disk. But how about utilising such methods for desktop machines? Obviously, these server devices have a back-up battery supply in case of power-outages, which give them enough juice to dump the contents of the RAM disks to hard-disk before they completely die. But let's just say for now that isn't really a problem for me.

I am buying a whole load of RAM soon, 8GB, because I can, but I am aware that I probably won't be using much more than 2gb of it at any one time. So how about offloading as much as possible into tmpfs partitions to speed things up even more? I imagine I could probably start loading up the tmpfs partitions as a background process after I log in. It would take a few minutes to load everything, but when it does, the speed of everything will be worth it. I know minimal distros such as Slitaz already load the entire desktop environment into RAM (if you have enough), which is key to the speed they achieve. So how about doing it for a standard Debian/Ubuntu distro? Can I load OpenOffice into RAM, with all the necessary libraries, ready to open in 0.01 seconds? Is this do-able? Has anyone ever tried? Is there any difference between doing this and just opening a load of applications at start-up and then forgetting about them? Am I just talking crazy?

Help me out, here!

---

### Post by sim-value on 2009-06-26
Just write a Script that at bootup a tmpfs partition is created and the stuff you want is moved there ..

Like /bin and /lib

---

### Post by monsterstack on 2009-06-26
> **sim-value said:**
> Just write a Script that at bootup a tmpfs partition is created and the stuff you want is moved there ..

Like /bin and /lib

*Move* them? I can see myself borking my machine if I try that. Copying them, however, sure, I can see that. I guess I could make symbolic links to make everything divert to the RAM partitions to grab binaries and libraries and stuff, but applications will still be accessing the hard disk to do that, slowing things down.

---

### Post by surfed on 2009-06-26
> **monsterstack said:**
> For those not in the know, you can mount a temporary filesystem in your RAM using the following command:

```
mount -t tmpfs -o 'size=100M' tmpfs /path/to/mount/point
```

I've been fooling around with such things for a few days now, and they are *crazy* fast. Whereas a harddrive will typically write at under 100mb a second and read a little faster, in RAM the speeds are closer to 11,000mb a second read/write. So I was wondering how I could use such things to my advantage. The only downside to these partitions is that they are deleted after you shut-down your computer. But still I wonder if they can't be put to better use.

RAM-disk hardware already exists for servers, and they are used by sites that require a lot of file i/o operations and database work, and they reduce unnecessary writes to the hard disk. But how about utilising such methods for desktop machines? Obviously, these server devices have a back-up battery supply in case of power-outages, which give them enough juice to dump the contents of the RAM disks to hard-disk before they completely die. But let's just say for now that isn't really a problem for me.

I am buying a whole load of RAM soon, 8GB, because I can, but I am aware that I probably won't be using much more than 2gb of it at any one time. So how about offloading as much as possible into tmpfs partitions to speed things up even more? I imagine I could probably start loading up the tmpfs partitions as a background process after I log in. It would take a few minutes to load everything, but when it does, the speed of everything will be worth it. I know minimal distros such as Slitaz already load the entire desktop environment into RAM (if you have enough), which is key to the speed they achieve. So how about doing it for a standard Debian/Ubuntu distro? Can I load OpenOffice into RAM, with all the necessary libraries, ready to open in 0.01 seconds? Is this do-able? Has anyone ever tried? Is there any difference between doing this and just opening a load of applications at start-up and then forgetting about them? Am I just talking crazy?

Help me out, here!

This might help:
[http://forums.gentoo.org/viewtopic-t-296892.html](http://forums.gentoo.org/viewtopic-t-296892.html)

from the page:with only /lib and /usr/lib put in ram, Firefox will load in 0.01 sec

---

### Post by monsterstack on 2009-06-26
> **surfed said:**
> This might help:
[http://forums.gentoo.org/viewtopic-t-296892.html](http://forums.gentoo.org/viewtopic-t-296892.html)

from the page:with only /lib and /usr/lib put in ram, Firefox will load in 0.01 sec

Perfect! Just the sort of thing I was looking for to get me started. I'm going to set up a small partition of Debian to play around with this idea. Good stuff!

---

### Post by Jackelope on 2009-06-26
This sounds like a great idea....I wonder if it'll become mainstream as huge amounts of ram become standard.

---

### Post by ericab on 2009-06-26
im trying this too, nice find..
thinking about trying to run my vmware server harddrives in ram...

---

