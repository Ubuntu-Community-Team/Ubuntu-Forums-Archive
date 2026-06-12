---
title: "Software RAID 5 troubles"
date: 2006-01-13
forum: Server Platforms
---

### Post by bigtex on 2006-01-13
I've learned the hard way that you can't boot from a software RAID 5.  In fact, the installation won't even finish.  I had set up my 4x120GB PATA IDE RAID 5 array in the installation, tried installing, and got some nasty errors.

OK.  So I put in a 30 GB disk, installed there, booted up, everything's fine.  Now how do I set up my RAID array?  I've tried installing GParted, but I get a very curious error:

**Application 'gparted' not available**

*The application can not be found in your archive. This usually means that it is not available for your hardware plattform.*

That's strange.  I tried installing QParted and got this even stranger error:

**Cannot install 'qtparted'**

*Installing this application would mean that something else needs to be removed. Please use the "Advanced" mode to install 'qtparted'.*

So I select advanced, which takes me into Synaptic, and under All there is no GParted, no QParted.  What's going on?

I notice in top (at the command line) that RAID is definitely on and eating up a LOT of my CPU cycles.  
```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 3199 root      15   0     0    0    0 S 40.2  0.0  11:34.03 md0_raid5
 3200 root      15   0     0    0    0 D  3.3  0.0   0:56.63 md0_resync
```

OK.  RAID is on, and the array that I created during the initial (failed) installation is there.  How do I mount it?  Or format it?  Or do anything with it?

I've opened Disks Manager, but I can't do much from there.  It recognizes my 5 IDE drives (and CDRom and floppy) but I can't do anything with the four that are in the RAID array.

Any ideas, anybody?

---

### Post by bigtex on 2006-01-13
my **/proc/mdstat** looks like this:

[COLOR="Red"]Personalities : [raid5]
md0 : active raid5 hde1[0] hdg1[3] hdh1[2] hdf1[1]
      351557952 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      [=====>...............]  resync = 26.4% (31001984/117185984) finish=129.6min speed=11072K/sec
unused devices: <none>[/COLOR]

So that means my RAID array is being rebuilt?  I'm going to assume so, because I reloaded the file and it had progressed a bit.  What do i do after that?

I tried using mdadm to check it out and it wouldn't let me.  Perhaps this is because the array is being rebuilt?

[COLOR="Red"]bigtex@server:~$ mdadm -D /dev/md0
mdadm: cannot open /dev/md0: Permission denied
[/COLOR]

---

