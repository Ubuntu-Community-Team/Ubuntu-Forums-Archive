---
title: "mdadm : what's the minimum on reserved space"
date: 2013-04-10
forum: Server Platforms
---

### Post by FrankT-Qc on 2013-04-10
Hi

Trying to create a RAID 1 over 2 2TB drives. 

I know there is reserved space for superblock, but I would expect this to be a few KiB... Read 2MiB somewhere.

My drive is 2000398934016 bytes and mdadm refuses to create anything bigger than 2000264560640 bytes. That is 128 MiB of reserved space. 

It's not that much of an issue as I was going for 100MiB of slack, but still, what explain this limit ? It's not documented, or at least not in the man pages for md or mdadm nor jumping at me from the google fountain.

Anyone can explain what's happening ?

thanks,

---

### Post by MAFoElffen on 2013-04-11
From Linux man mdadm:
> 
Option that is s not mode-specific

-z, --size=
Amount  (in  Kibibytes)  of space to use from each drive in RAID levels 1/4/5/6. This must be a multiple of the chunk size and must leave about 128Kb of space at the end of the drive for the RAID superblock. If this is not specified (as it normally is not) the smallest drive (or partition) sets the size, though if there is a variance among the drives of greater than 1%, a warning is issued.

Of course with large drives, then you're going to lose some if it's GPT for the redundant partition tables. Then if it's a boot drive, then you are going to lose another 1MB to allow for bios_grub. I usually also leave about 1MB unallocated before the start of the first partition. Then if it is a ext3 or ext4 filesystem, then it takes away another 128Mib for it's filesystem journaling. You could force less for journaling, but really not recommended.

---

