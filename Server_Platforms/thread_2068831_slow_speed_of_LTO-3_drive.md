---
title: "slow speed of LTO-3 drive"
date: 2012-10-10
forum: Server Platforms
---

### Post by big_blue on 2012-10-10
Hi,

i use a LTO3 drive to backup some of my data. Until now i used a LTO-1 drive which worked very well with correct speed. Now i buyed a second hand LTO-3 Drive and tested it yesterday with moderate success.

First i store the "old" LTO-1 catridges back to disk with the known 20MB/s performance like the old LTO-1 drive. Maybe this is ok, because the catridge is not able to get more speed. After restoring i tried to backup from the disk to a new LTO-3 catridge. But now i only get 30MB/s of write performance with the drive.

My harddisk is fast enough to get more thank this. I also use mbuffer see who will be the bottleneck. But the buffer is still on 100%, so the drive is not fast enough. Maybe i used a wrong parameter while using tar.

Here is the command i used to backup from the filesystem.
```

mt -f /dev/nst0 rewind # rewind the catridge
tar -c1 -b 512 -f - ./ 2>/dev/null | mbuffer -L -s 256K -m 1G -P 85 > /dev/nst0

```

Maybe some of you know what to do to get more write performance with the LTO Drive.

Ohh, sorry i forgot to show you my system. It is a AMD64 3000+ AMD Processor with a Raid1 of 2 1TB SATA HDD. The LTO-3 drive is a Tanberg BRSLA-0605-DC SCSI drive on a PCI Symbios Logic UW SCSI Controller.

Thanks for your help.
Cheers
big_blue

---

