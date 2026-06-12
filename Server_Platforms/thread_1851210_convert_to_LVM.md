---
title: "convert to LVM ?"
date: 2011-09-27
forum: Server Platforms
---

### Post by ipguy on 2011-09-27
Hi all

Is there an easy way to convert a Ubuntu Server 10.04 installation to LVM ?
I need to grow /dev/sda1 and am unable to without LVM

---

### Post by rubylaser on 2011-09-27
What filesystem did you use?  You can [grow / shrink EXT4]("http://en.positon.org/post/Resize-an-ext3-ext4-partition") without the need for LVM.

---

### Post by ipguy on 2011-09-27
> **rubylaser said:**
> What filesystem did you use?  You can [grow / shrink EXT4]("http://en.positon.org/post/Resize-an-ext3-ext4-partition") without the need for LVM.

given it's the root partition i take it i will need to boot into a livecd ?

---

### Post by rubylaser on 2011-09-27
Yup, that's exactly what you'd need to do.  Make sure you have a backup before you try this or any other method to shrink / migrate this install.

---

