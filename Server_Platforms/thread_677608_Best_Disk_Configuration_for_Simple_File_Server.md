---
title: "Best Disk Configuration for Simple File Server"
date: 2008-01-25
forum: Server Platforms
---

### Post by mgclinux on 2008-01-25
I've set up a simple Samba file server using Ubuntu 7.10. I'm new to the Linux command line but have managed very well with the great help from the community,  so my question has more to do with hardware than software. I'm looking for an efficient hard drive setup. I'll have 2-500g Seagate drives and 1-10g drive, that I may or may not use. 

The file servers main purpose is to hold music, videos, ebooks, photos and other data files. Access to the server is from Windows & Linux PC's and it will be headless. Which would be the best drive configuration?

1) The 10g drive with the OS on it and the 2 - 500g drives separate.
2) The 10g drive with the OS on it and the 2 - 500g drives in RAID1.
3) Open for any other suggestions.

I would appreciate any suggestions.

Thanks

---

### Post by HermanAB on 2008-01-25
Hmm, the 10G drive is likely so much slower than the big drives, that it would be best used for skeet shooting.

If you would use JFS on the big drives, instead of the default Ext3, then you will save several times more disk space than the size of the small drive, so the small drive is really just a drop in the bucket anyway.

Cheers,

Herman

---

### Post by dantrevino on 2008-01-25
You probably have enough memory and few enough concurrent connections that you'll never use swap, so I'd use the 10Gb disk for OS and swap.

You need to decide the rest.  Don't you need backup?  If it were me i'd keep the disks separate and use one as a backup disk in another machine or usb enclosure.  And I'd use XFS.

In terms of performance your network is likely the biggest limiting factor.

dan

---

### Post by tlcoffee on 2008-01-25
I'm using JFS on mine, I DID think about XFS but mp3s, photos and ebooks are just not large enough to really get the full benefit of XFS (which is awesome for large files)

---

### Post by rickyjones on 2008-01-25
> **mgclinux said:**
> I've set up a simple Samba file server using Ubuntu 7.10. I'm new to the Linux command line but have managed very well with the great help from the community,  so my question has more to do with hardware than software. I'm looking for an efficient hard drive setup. I'll have 2-500g Seagate drives and 1-10g drive, that I may or may not use. 

The file servers main purpose is to hold music, videos, ebooks, photos and other data files. Access to the server is from Windows & Linux PC's and it will be headless. Which would be the best drive configuration?

1) The 10g drive with the OS on it and the 2 - 500g drives separate.
2) The 10g drive with the OS on it and the 2 - 500g drives in RAID1.
3) Open for any other suggestions.

I would appreciate any suggestions.

Thanks

Are you mainly writing to the hard drives or reading? Would you rather have only 500GB of space or the full 1TB? 

Personally, for a fileserver like that, I'd do the 2x 500GB in a RAID1 array. 

-Richard

---

### Post by mgclinux on 2008-01-25
Thank you Richard...A good estimate would be about 85% reading and 15% writing. At this point 500GB of storage is plenty and I was strongly considering Dan's suggestion of using the second drive for backups. Would a RAID1 offer an advantage over the seperate drive configuration considering the way it will be used?

---

### Post by rickyjones on 2008-01-25
> **mgclinux said:**
> Thank you Richard...A good estimate would be about 85% reading and 15% writing. At this point 500GB of storage is plenty and I was strongly considering Dan's suggestion of using the second drive for backups. Would a RAID1 offer an advantage over the seperate drive configuration considering the way it will be used?

Yes, RAID1 would actually have a slight advantage. By having the two disks in RAID1 you would have a slightly slow **write** speed, but a faster **read** speed because you'll be reading from two disks as opposed to just one.

In this manner if one disk dies you'll still have all your data just the way it is. Sure, a secondary backup disk could perform the same function but if the primary data disk dies before the backup runs then there is a potential for data loss. RAID1, in addition to a competent backup scheme, will be your best choice (in my honest opinion).

-Richard

---

