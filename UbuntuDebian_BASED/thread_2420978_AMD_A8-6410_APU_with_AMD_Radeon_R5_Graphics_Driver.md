---
title: "AMD A8-6410 APU with AMD Radeon R5 Graphics Drivers"
date: 2019-06-14
forum: Ubuntu/Debian BASED
---

### Post by v0id3dlif3 on 2019-06-14
Hello I'm running Peppermint 10 which is based on ubuntu 18.04 lts.

I have installed the A8-6410 with Radeon™ R5 Graphics Previous Drivers from amd's website.

AMD Radeon Software Crimson Proprietary Ubuntu 14.04 x86_64 Video Driver for Graphics Accelerators
AMD Radeon Software Crimson Proprietary Ubuntu 14.04 x86_64 Minimal Video Driver for Graphics Accelerators (Non-X Support)
AMD Radeon Software Crimson Proprietary Ubuntu 14.04 x86_64 Video Driver for Graphics Accelerators Devel Files (OGL, OCL)
AMD Radeon Software Crimson Proprietary Ubuntu 14.04 x86_64 Radeon Setting

all is required by amd to install the full support of the drivers, Revision Number15.11

I know it's for an old version of ubuntu, but 18.04 does not detect the apu. The install went ok somewhat lol, but it didn't give any errors other then the normals of not being i386 etc, after installation it picks up and uses the gpu, expect that it no longer picks up the second display "TV in my case with hdmi". I'm not a very advanced user at this. 

I found this, but the laptop I'm using is not on the list. Which is [https://support.hp.com/us-en/document/c04316812](https://support.hp.com/us-en/document/c04316812)

Then I also noticed that it does not pick up refresh rates etc, I'm also posting this on pepperment forums.

any help would be awesome thanks, if I need to run any commands or anything I will.

---

### Post by slickymaster on 2019-06-14
Thread moved to **Hardware** for a better fit

---

### Post by v0id3dlif3 on 2019-06-14
Thanks didn't know if it was the right fit or not

---

### Post by v0id3dlif3 on 2019-06-14
Ok well I'm not one to sit around waiting and I really need my system up, and tried everything I possible could try and even had a friend of mine that is more advanced then me. my plan is to drop back too 14.04 install the drivers and upgrade from there and see if I can't find away to keep the apu working.

---

### Post by v0id3dlif3 on 2019-06-16
Feel free to lock this, I just went back to windows. Not that I wanted too, but I've been fighting for 3 weeks on trying to get this APU to comply with ubuntu 18.04, and peppermintos 10. if anyone decides to add the support for this APU I would be greatly happy and will switch too linux right away. as it looks now I will just have to custom build a system to run linux.

---

### Post by kurt18947 on 2019-06-16
It may be too late for you but I had a similar problem with a Ryzen 3 APU, no boot using the APU. I installed a few years old AMD PCI-e video card and it worked perfectly. Just a couple hours ago I decided to see if the integrated video worked and sure enough, one of the updates enabled Vega video support. I find it handy to keep some older bits of hardware around that I KNOW work with Linux.

---

