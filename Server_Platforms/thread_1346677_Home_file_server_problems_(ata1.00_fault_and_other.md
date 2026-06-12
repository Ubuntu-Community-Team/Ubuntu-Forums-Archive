---
title: "Home file server problems (ata1.00 fault and others)"
date: 2009-12-05
forum: Server Platforms
---

### Post by ajk32 on 2009-12-05
Hi all,

After over a year of flawless running, my home file server has quit working and I need some help getting it back up! I'll give as much info as I can. I'm fine with computers in general but a bit of a linux/Ubuntu noob.

I set up a simple headless file server, with 4x500GB SATA disks in software RAID5 configuration and a seperate PATA 80GB (an old spare) for the OS. It didn't have anything particularly special installed - SAMBA and Twonky and that's about it. I used it for backup mostly and streaming video.

A few days ago, I noticed I couldn't connect to it via my windows machine. I connected a monitor and found a bunch of error messages:

```
ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata1.00: status: { DRDY }
ata1.00: revalidation failed (errno =-5)
```

Then it dropped me to a busybox v1.1.3 prompt.

I naturally restarted the server to see if the fault cleared, but now all I get is a flashing underscore curser after POST, nothing else, not even the error messages are appearing. 


My suspicion is that maybe the OS hard disk has failed. My original reasoning behind setting the server up the way I did was that if the OS hard disk failed, I could pop in another HD, install Ubuntu, and it would recognise the RAID array and no data would be lost. Maybe I'm at that point now!! The HD does show up in BIOS, but I know that's no indication that it's not messed up.

Any advice or help would be very much appreciated.

Andrew

---

### Post by ajk32 on 2009-12-05
OK, I've pulled the OS HD and stuck it in an external USB enclosure, hooked it up to my Ubuntu running laptop and tried to mount the volumes.

Looks like I have 3 partitions (1GB, 10GB and 10GB). The 1GB partition seems to mount but the other two partitions have the error:

```
mount: /dev/sdd7 is not a valid block device
```

Could this be the trouble?

---

### Post by ajk32 on 2009-12-06
No takers?

I'm currently reinstalling ubuntu server on a spare HD. Could someone help me with the MDADM command for 'finding' the raid array? I obviously don't want to lose any information if I can help it, all the web sites I can find are for creating a raid array, or recovering from a failed disk that is part of the array, not the OS hard disk itself.

Thanks in advance....Andrew

---

