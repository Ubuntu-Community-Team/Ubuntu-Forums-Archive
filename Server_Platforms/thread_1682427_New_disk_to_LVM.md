---
title: "New disk to LVM"
date: 2011-02-05
forum: Server Platforms
---

### Post by Loki57701 on 2011-02-05
Hello everyone, 

I recently setup an old desktop machine as my new server running 10.10. I'm going to be using this machine as a simple home file server using samba. During the OS install I opted for LVM, I don't have much experience with LVM, so the process of adding a new disk strictly for samba shares is new to me. Before all I had to do was pop in the new hard drive, format it, create a mount point, mount it, and add a line to my fstab. With LVM I'm not exactly sure how to do this. 

I've already done some googling, but honestly most of it was just confusing. If someone could point me in the right direction or provide a decent how-to link I wold be greatly appreciative.

Thanks.

---

### Post by Girya on 2011-02-05
[http://tldp.org/HOWTO/LVM-HOWTO/]("http://tldp.org/HOWTO/LVM-HOWTO/")

if you get stuck post your questions I'll try to help.

---

### Post by YesWeCan on 2011-02-05
Having LVM on your root disk does not require you to use LVM on any other disk. so you could just add another disk to fstab as you have done before and create a mount point for it wherever you choose. Or am I misunderstanding your setup?

---

### Post by insane_alien on 2011-02-06
> **YesWeCan said:**
> Having LVM on your root disk does not require you to use LVM on any other disk. so you could just add another disk to fstab as you have done before and create a mount point for it wherever you choose. Or am I misunderstanding your setup?

while this is true, part of the point of LVM is that you can treat all your disks as one (kind of like RAID in JBOD mode) and generally have better partition management that is typically allowed by normal partitioning.

its useful for single disk setups but becomes even more useful for multiple disk setups.

---

### Post by Loki57701 on 2011-02-06
Thanks for all the replies everyone. I decided to skip the LVM route and just go the standard - create mount point and edit fstab way instead. I need to do a little research on LVM and see how it could work for me.

Thanks again.

---

