---
title: "Any of you do soft RAID using mdadm or other software?"
date: 2008-11-09
forum: The Cafe
---

### Post by kernelhaxor on 2008-11-09
I am thinking of doing this on my system.  
Could you comment about how easy/difficult it was to set up? any issues? how abt the performance?  anything else u would advise?

---

### Post by Cracauer on 2008-11-09
I'm using it since IIRC 2004, might be 2003, on my main server, a backup server and some of the workstations.

No issues. As always the critical part about RAID (and that's where that onboard RAID junk fails) is recovery on error. I survived a number of disk deaths with no problems.

Linux Software RAID beats most hardware controllers on re-sync speed, a critical thing when it comes to run raid-5 with terabyte disks. CPU usage on a three or four-disk RAID-5 isn' an issue with today's CPUs and (lame) disks.

Just don't fatfinger your mdadm commands :)

---

### Post by kernelhaxor on 2008-11-09
> **Cracauer said:**
> I'm using it since IIRC 2004, might be 2003, on my main server, a backup server and some of the workstations.

No issues. As always the critical part about RAID (and that's where that onboard RAID junk fails) is recovery on error. I survived a number of disk deaths with no problems.

Linux Software RAID beats most hardware controllers on re-sync speed, a critical thing when it comes to run raid-5 with terabyte disks. CPU usage on a three or four-disk RAID-5 isn' an issue with today's CPUs and (lame) disks.

Just don't fatfinger your mdadm commands :)

Thanks for the reply.
how is it better than hardware RAID cards? I thought RAID through hardware would be much faster?  
You think a Core 2 Duo 1.86Ghz is capable of RAID using mdadm? (I have two 500GB SATA drives)

---

### Post by Cracauer on 2008-11-09
No, the raid cards have the advantage of having an additional processor. That CPU is slower than a ninja macho Core2 something. But of course if you want to use your main CPU for something else that's better. 

Raid-5 (and 6) are just a bunch of XORs, on modern CPUs mainly limited by memory bandwidth, so normally you have plenty CPU left.

Anyway, the point here is that on your private use machine your average CPU and disk load during a disk fail is usually low. And your faster main CPU gets through the re-sync faster than a raid card. Of course you totally lose in a multiuser environment where other users keep the system at high load during the re-sync. In that situation you need a hardware RAID controller.

So: if you can keep the load low during resync you get through the resync faster. If you still have high load you want the hardware controller. Of course in the latter situation you probably lose either way, because high load on the raid *really* screws up re-sync time.

The main advantage of a hardware raid controller for a privately owned system is the battery backed up cache, so that you can turn the disk cache off (if you have it on you are risking your data on power fail).

---

