---
title: "Impossibly Slow ZFS RAIDZ (350KB/s) Brand New Install"
date: 2014-01-12
forum: Server Platforms
---

### Post by liam5 on 2014-01-12
Posted this thread in the beginners section, but didn't seem to get much of a response. Upon searching the forums it appears most ZFS issues have been posted in this Server section, so thought it was worth a shot.

[Original thread](http://ubuntuforums.org/showthread.php?t=2197880).

Until recently I had been using mdadm with four drives, with each pair in a RAID1 configuration. These drives were 2x2TB, and 2x3TB, however as free space was very short, I purchased another 2x3TB drives with the intention of using mdadm and RAID5.

Upon building the RAID5 array, the initial sync was apparently going to take 11000 minutes to complete at a very slow 4500KB/s speed. I was advised that perhaps ZFS was the best way to go.

So, I installed a minimal version of ubuntu 13.04 and created my ZFS RAIDZ pool using all four 3TB drives (they are all Seagate ST3000DM001 drives), then created a dataset and attempted to copy a file to it... At a whopping 350KB/s!

The machine is a HP Microserver N40L with 8GB of RAM.

I have tested the drives with Windows installed on the same machine and get speeds of ~160MB/s per individual drive (same results in ubuntu using hdparm). I then tried FreeNAS on the machine and set up a ZFS RAIDZ pool using the web interface. I was only connected to a 100mb LAN connection at the time, but the file transfer saturated this connection as expected.

ubuntu-zfs was installed from the ppa:zfs-native/stable repository.

I used the following command to create the pool (serials omitted) ```
sudo zpool create -o ashift=12 datapool raidz scsi-SATA_ST3000DM001 scsi-SATA_ST3000DM001 scsi-SATA_ST3000DM001 scsi-SATA_ST3000DM001
```

I really hope someone can help me out here, as I don't know why performance is so poor. I have seen online other people that have used the same hardware as me without this sort of issue.

According to the ubuntu wiki page ubuntu-zfs is a "native kernel module".


Drives are updated to the latest firmware. I know they are cheap, but they are just being used for a simple home setup, nothing critical, and given their individual performance I cannot see why using them in this configuration would be an issue - they worked perfectly in the RAID1 array, and a software RAID5 array in Windows Server. Speed is not my top priority, if I only get 20MB/s, it's not ideal, but I can live with it.


I'm positive the CPU is up to the task as many people use this exact machine in this way, again, if I'm not seeing 200MB/s transfer speeds, I'm really not fussed. Likewise with the RAM, if 8GB isn't enough for maximum performance, I'm not fussed as long as it works without issues.


I do not mind which version of ubuntu I use, if 12.04 is recommended, I am happy to use that.


Given that FreeNAS ran so smoothly, and with decent transfer speeds (I may reinstall it to run a test over the gigabit network as this will be the main type of transfers I will be doing), surely the issue I am experiencing can only be down to software-based configurations rather than hardware limitations.

---

### Post by houstonbofh on 2014-01-13
I am a big fan of ZFS.  It really is wonderful, and I love it.  That said, ZFS on Linux is just not stable yet.  Part of it is that it is new, and part of it is that Linux does not have some of the debugging tools that makes ZFS what it is.  I would stick with FreeBSD, FreeNAS or nas4free (I use nas4free) for ZFS and just have some very fast and stable network attached storage.

---

### Post by lukeiamyourfather on 2014-02-10
Were you able to figure out the issue? That is unusually slow unless you're copying multiple TB of like 1KB files. ZFS on Linux is definitely the way to go in my opinion but I have not experienced the performance issues you're describing. Is it possible the performance issues could be unrelated to ZFS like on the network (wireless especially) or another service like Samba?

---

### Post by brokenhachi on 2014-02-11
did you try changing some of the tuning variables? 

[http://askubuntu.com/questions/228386/how-do-you-apply-performance-tuning-settings-for-native-zfs](http://askubuntu.com/questions/228386/how-do-you-apply-performance-tuning-settings-for-native-zfs)

noprefetch did it for me. 

Also, how did you configure the raid card? JBOD?

---

### Post by brokenhachi on 2014-02-11
sorry, double post :(

---

### Post by liam5 on 2014-02-15
> **lukeiamyourfather said:**
> Were you able to figure out the issue? That is unusually slow unless you're copying multiple TB of like 1KB files. ZFS on Linux is definitely the way to go in my opinion but I have not experienced the performance issues you're describing. Is it possible the performance issues could be unrelated to ZFS like on the network (wireless especially) or another service like Samba?

I tried copying a single file, for example ~1GB over a wired network.

I never did resolve the issue on Ubuntu despite trying everything I could find on the net to try, tweaking variables etc.

My solution was to just use FreeNAS and I now get ~90MB/s over the network.

> **brokenhachi said:**
> did you try changing some of the tuning variables? 

[http://askubuntu.com/questions/228386/how-do-you-apply-performance-tuning-settings-for-native-zfs](http://askubuntu.com/questions/228386/how-do-you-apply-performance-tuning-settings-for-native-zfs)

noprefetch did it for me. 

Also, how did you configure the raid card? JBOD?

I tried various things yes, but nothing seemed to have any effect. Maybe 100KB/s or so, but that might not be related to the tweaked values.

No RAID card, just the motherboard connectors.

---

