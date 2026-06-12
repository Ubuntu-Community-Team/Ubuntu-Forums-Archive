---
title: "No grub screen after Raring update today"
date: 2013-04-10
forum: Ubuntu Development Version
---

### Post by debb1046 on 2013-04-10
Been running Raring for a while now without significant problems. After installing today's upgrades the grub screen no longer shows up and the laptop boots directly into Windows 8. I'm using UEFI mode with secure boot turned off. Ideas?

---

### Post by dino99 on 2013-04-10
real install or wubi ?
how many ubuntu kernel installed ?

---

### Post by mJayk on 2013-04-10
> **dino99 said:**
> real install or wubi ?
how many ubuntu kernel installed ?


wubi with win8 and ringtail?

---

### Post by QDR06VV9 on 2013-04-10
> **debb1046 said:**
> Been running Raring for a while now without significant problems. After installing today's upgrades the grub screen no longer shows up and the laptop boots directly into Windows 8. I'm using UEFI mode with secure boot turned off. Ideas?


Don't know if you already have done this or not, but try
sudo update-grub
With one of the updates a day or so ago I had to use boot repair to get grub back with Dual Booting
the other machine i have with raring on it solely (nothing else)
Turned out fine (meaning i had grub)

---

### Post by zika on 2013-04-11
> **debb1046 said:**
> Been running Raring for a while now without significant problems. After installing today's upgrades the grub screen no longer shows up and the laptop boots directly into Windows 8. I'm using UEFI mode with secure boot turned off. Ideas?You've choosen to install new version of /etc/default/grub. Press LeftShift at the very end od of BIOS POST screen and You should get Grub screen...
After You get into Ubuntu edit afore mentioned file... Then apply update-grub...

---

