---
title: "Raid 10 backup scheme help"
date: 2009-06-25
forum: Server Platforms
---

### Post by druca on 2009-06-25
Hi! 

I was going to make a backup script using dd and tar of 'drive images' for my *nix servers. I have a general idea of how to go about it, but what if I have raid 0+1 ?

I think from my point of view treats it as one logical volume, so can I just copy it from there and make one image? And then I will have to have a somewhat functioning linux system for restoration using the same driver, and that driver will make sure that the data is written correctly mirrored and striped across all discs. 

and no i have kernel 2.4 series so no Linux raid 10 driver  

any suggestions would be appreciated.

thank you,
drew

---

### Post by antikristian on 2009-06-26
If it's hardware raid, I belive it's treated as a single volume to the OS, so you can't mirror the disks, unless you shut the system down, ejected the disks, inserted them into a second system, ran a livecd, and ran the script from there...

Also, I really don't think you should run dd on a mounted volume, not because you can't, but because I belive you'll end up with a corrupt image as soon as something changes on the drive. I'd rather just use a combination of find and tar, 

My guess to what would happen with dd is, you run the backup, and someone changes a file, you end up with half of the new file, wich the filesystem might have placed on the end of the raid, volume, and part of the old file, wich is still located at the end of the volume (if the filesystem thinks that's a good idea) 

Also, with dd, if you have 500 GB of storage space, and only use 40 GB, you'll end up with a backup file with 460 GB of empty space, or gibberish from past deleted files.

---

