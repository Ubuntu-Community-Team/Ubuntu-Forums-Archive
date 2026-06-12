---
title: "fresh install ubuntu server - grub error out of disk?"
date: 2012-10-11
forum: Server Platforms
---

### Post by panupat on 2012-10-11
Hi.

I'm trying to set up a samba server on my DELL server but right after installing ubuntu server 64 bit, I get this error

error : out of disk
grub rescue>

Ubuntu server 12.04.1 x64 bit

While installing, I choose to use "the entire disk" without using LVM and pretty much using the default partition Ubuntu provided. 


The disk is using hardware RAID 0, for a total space of 4TB in a single volume.

checked only "samba server"

Any help appreciate. Thanks.

---

### Post by nothingspecial on 2012-10-11
*Thread moved to **Server Platforms**.*

---

### Post by DELL JonathanS on 2012-10-11
[FONT=Calibri]Hi Panupat,[/FONT]
  [FONT=Calibri] [/FONT]
  [FONT=Calibri]What server model and internal storage controller do you have? It sounds like you might be running into a boot device size limit. What partition sizes did Ubuntu set up on your 4TB RAID-0? These information can help us determine if that is in fact causing the boot failure.[/FONT]

---

