---
title: "LVM and adding existing volume"
date: 2011-10-03
forum: Server Platforms
---

### Post by iburry on 2011-10-03
A few years back I set up a file server using Ubuntu Server 9.1. I decided to set up LVM and have /home on its own harddrive, and the root on another.  This worked well until recently when the hd containing root decided to up and die. I thought replacing the failed drive and reinstalling the OS would be a snap, but after getting to the drive partitioning part of the install, I didn't find any explicit way of adding the existing /home volume. The FAQs I've read have been unhelpful.  Is there any way of doing this safely?

---

### Post by lcman on 2011-10-04
> **iburry said:**
> A few years back I set up a file server using Ubuntu Server 9.1. I decided to set up LVM and have /home on its own harddrive, and the root on another.  This worked well until recently when the hd containing root decided to up and die. I thought replacing the failed drive and reinstalling the OS would be a snap, but after getting to the drive partitioning part of the install, I didn't find any explicit way of adding the existing /home volume. The FAQs I've read have been unhelpful.  Is there any way of doing this safely?

Partition the new drive with LVM like you need and boot the system. Add the lv with home to the new volume group and mount it at /home. Should work!

---

