---
title: "Mount ISO Read/Write not working"
date: 2012-09-22
forum: Server Platforms
---

### Post by webusr1 on 2012-09-22
All,
I'm running Ubuntu 12.04 and I'm trying to mount an ISO file as Read and Write but get the following warning: 
mount: warning: /mnt/iso1 seems to be mounted read-only.

I issue the following command:
sudo mount -rw -o loop Core-current.iso /mnt/iso1


Any ideas why I can't mount the ISO file as read/write???

Thanks!

---

### Post by matt_symes on 2012-09-22
Hi

> **webusr1 said:**
> All,
I'm running Ubuntu 12.04 and I'm trying to mount an ISO file as Read and Write but get the following warning: 
mount: warning: /mnt/iso1 seems to be mounted read-only.

I issue the following command:
sudo mount -rw -o loop Core-current.iso /mnt/iso1


Any ideas why I can't mount the ISO file as read/write???

Thanks!
 
As it's an ISO  9660, i don't believe you can mount it read/write. These are the old CD Rom images and it does not make much sense to mount them read/write.

The general technique is to extract modify and recreate the ISO with the changes you want using *genisoimage* or *mkeisofs*.

Kind regards

---

### Post by webusr1 on 2012-09-23
Yes, that makes sense. I'll copy the data off to directory and generate an ISO image.

Thanks!

---

