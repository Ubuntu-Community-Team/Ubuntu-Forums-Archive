---
title: "U10 clonzilla ends at grub&gt;"
date: 2010-07-09
forum: Server Platforms
---

### Post by xkaliburx on 2010-07-09
I have 5 identical webservers, all Dell PowerEdge sc1425's.  I have a new configured image running u10 64bit, which I made a clonezilla image and stuck on our NFS server (something I have done numerous times with u8, 9 etc.)

I put this image on 2 servers, one booted just fine where another left me at a grub> prompt and I am stuck.  Been reading a bit, and it seems some things have changed, I don't see a menu.lst, etc.

I did try this with the following results;


grub> root (hd0,0) 
Filesystem type is ext2fs, partition type 0x83

next I issued;
grub>setup (hd0)
Checking if "/boot/grub/stage1" exists... no
Checking if "/grub/stage1" exists ... no
Checking if "/grub/stage2" exists ... no
Checking if "/grub/e2fs_stage1_5" exists ... yes
Running "embed /grub/e2fs_stage1_5 (hd0) (hd0)1+17 p (hd0,0)/grub/stage2 /grub/menu.list" ... succeeded
Done.

But from there I am stil stuck.  A reboot leads me to the same place.  Hints or help is greatly apprecaited, just really odd the same image did this to one not the other, and I have 2 more to do, but dont want to be down 2 more webservers!

---

