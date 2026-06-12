---
title: "Ubuntu 6.06 server how to  use grub  ?"
date: 2006-07-17
forum: Server Platforms
---

### Post by slo on 2006-07-17
I install ubuntu 6.06 server on my PC, but I found ubuntu use Lilo as OS loader, and Install CD not provide OS loader lilo or grub let me to choice, I want use grub as OS loader , how to do it ?

---

### Post by ifokkema on 2006-07-17
> **slo said:**
> I install ubuntu 6.06 server on my PC, but I found ubuntu use Lilo as OS loader, and Install CD not provide OS loader lilo or grub let me to choice, I want use grub as OS loader , how to do it ?
Grub is the Ubuntu default. Where did you read it came with Lilo?

---

### Post by slo on 2006-07-17
I searched some info, it explain as blowing:
Grub where crashed when boot partion is xfs filesystem since some bug,so Lilo will replace Grub when you /boot is xfs filesystem.
But I always use xfs on all partations on my gentoo system, and grub never crashed, why Ubuntu has this problem ?
Is there anybody can explain it ?

---

### Post by ekerazha on 2006-08-12
> **slo said:**
> I searched some info, it explain as blowing:
Grub where crashed when boot partion is xfs filesystem since some bug,so Lilo will replace Grub when you /boot is xfs filesystem.
But I always use xfs on all partations on my gentoo system, and grub never crashed, why Ubuntu has this problem ?
Is there anybody can explain it ?

Yeah... why?

---

### Post by lamego on 2006-08-12
According to some pages on the web on some systems grub can cause data corruption when booting from XFS systems, it doesn't mean it would crash on you but it can crash to other people that is why lilo is used instead.

---

