---
title: "Can You NetBoot With Ubuntu Server?"
date: 2010-07-23
forum: Server Platforms
---

### Post by SecretLegend on 2010-07-23
Hey guys I wanted to know if I can use my Ubuntu Server Computer to NetBoot Windows 7 on another computer in the house. So is this possible and how can I set it up? Thanks in advance :)

---

### Post by arrrghhh on 2010-07-23
So... are you looking to have diskless clients use resources on your Ubuntu server a la [LTSP](https://help.ubuntu.com/community/UbuntuLTSP)?  Or are you looking to image workstations via Ubuntu server a la a tftp server?  [Netboot reference](https://help.ubuntu.com/community/Installation/Netboot).

I've only done this with Ubuntu/Linux.  At work we used Novell Zenworks Imaging to image workstations with Windows images, so I'm sure it's possible.  Clonezilla or the like would probably acheive it.

Diskless thinclients... Not so sure about that.  Beyond my expertise, I'd be interested to see where this thread goes tho.  Both are prospects I'm interested in.

---

