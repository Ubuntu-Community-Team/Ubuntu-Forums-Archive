---
title: "CDs/DVDs not mounting properly"
date: 2015-10-24
forum: Ubuntu Studio
---

### Post by cobradabest on 2015-10-24
I've recently upgraded UbuntuStudio 15.04 to 15.10 (64-bit), and ever since, it's no longer recognising CDs/DVDs properly...

I'm trying to install a windows games (Quake 2 to be exact, but all the games I've tried have this same issue), and it's only recognising the audio CD part of it, it used to also show the section that hjas the installation files, but it doesn't anymore.
[IMG]http://i.imgur.com/CaH9ipk.png[/IMG]
(I'm using Cinnamon, by the way)

After doing a bit of digging, I realised that the problem may lie in the fstab file, because my drive is only 1 year old, so it can't have already gone bad, can it?

When I tried to use the command "sudo mount /dev/dvd /media/cdrom", I got this:
```
mount: /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```

and when I run the dmesg | tail, I got this:
```
[ 1591.059216] sr 5:0:0:0: [sr0] tag#5 Add. Sense: Illegal mode for this track
[ 1591.059218] sr 5:0:0:0: [sr0] tag#5 CDB: Read(10) 28 00 00 05 2c fc 00 00 01 00
[ 1591.059220] blk_update_request: I/O error, dev sr0, sector 1356784
[ 1591.059222] Buffer I/O error on dev sr0, logical block 339196, async page read
[ 1591.071056] sr 5:0:0:0: [sr0] tag#7 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1591.071059] sr 5:0:0:0: [sr0] tag#7 Sense Key : Illegal Request [current] 
[ 1591.071061] sr 5:0:0:0: [sr0] tag#7 Add. Sense: Illegal mode for this track
[ 1591.071063] sr 5:0:0:0: [sr0] tag#7 CDB: Read(10) 28 00 00 05 2c fd 00 00 01 00
[ 1591.071064] blk_update_request: I/O error, dev sr0, sector 1356788
[ 1591.071066] Buffer I/O error on dev sr0, logical block 339197, async page read
```

So what do I do?

If it helps, here are my PC specs:
500GB HDD
Intel 2-core 4.0GHz CPU (64-bit)
AMD R9 280X GPU
8GB RAM

---

