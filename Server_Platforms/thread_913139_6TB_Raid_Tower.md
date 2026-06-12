---
title: "6TB Raid Tower"
date: 2008-09-07
forum: Server Platforms
---

### Post by InvIsiBlekID on 2008-09-07
I have a 6TB raid tower attached to my server via a scsi port on the back of my server.  Linux can see the tower as 6tb but cannot do anything with it

fdisk output:
```

#fdisk -l
...
Disk /dev/sda: 5994.1 GB, 5994172121088 bytes
...

```

But I cannot open it in cfdisk because it says this:
```

#cfdisk /dev/sda
Warning!!  Unsupported GPT (GUID Partition Table) detected. Use GNU Parted.

```

The problem is that every time I run parted, it doesn't matter what command I try to run, it crashes.  Says something about my sector size being 2048.

Had this working before (with a crude workaround) I had the 6TB partitioned into 4 partitions (because i couldnt make each any larger) then i used a volume group to put them all together.  BUt now when i try to make the volume group (this all after reinstalling because i wanted a fresh load for the actual server implementation), I keep getting errors about volume descripters being left open.

Anyone have a good, easy way for me to either use gpt under ubuntu (server 8.04.1) so i can use the entire raid tower, and not have to use a volume group?

---

