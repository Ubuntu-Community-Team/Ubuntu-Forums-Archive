---
title: "Mint 18.2 Running in Software Rendering Mode, but ticked Enable 3d Acceleration"
date: 2017-10-08
forum: Virtualisation
---

### Post by SciGuy1872 on 2017-10-08
I'm trying to run Linux Mint 18.2 in Vbox 5.1.28.  I have Ubuntu 16.04, and [saw]("https://www.organicweb.com.au/18829/general-technology/linux-mint-video-problem/") that I needed to check Enable 3d Acceleration, and the problem of having Mint run in Software Rendering Mode would stop. I think I tried this before, but the screenshot of the message was the exact problem I was having, so I tried it again, but it didn't stop the problem. The host is Ubuntu Mate 16.04. Does anyone have advice? I saw a command, ```
virsh dumpxm {Guestname, Guest ID, or uuid}
```, so I entered ```
 virsh dumpxml {Mint 18.2}
```; but the return said ```
 error: unexpected data '18.2}
```; That command might be for KVM, but I saw a post where it gave necessary information, so I decided to try it. I'm running the 32-bit version.

---

