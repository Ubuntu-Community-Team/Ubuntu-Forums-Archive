---
title: "Disadvantages of older kernels"
date: 2014-07-24
forum: Ubuntu, Linux and OS Chat
---

### Post by Christopher_Wells on 2014-07-24
What are the disadvantages of using an older kernel (and older distro) such as Lucid with 2.6 or 3.0 kernel?  There is a point to the question:  In my case, I have a GPU that is without a proprietary driver since X 1.13 or so.

---

### Post by Sef on 2014-07-24
Moved. Not a support question.

---

### Post by Bucky Ball on 2014-07-24
Welcome. If it is unsupported (from an end-of-life release) you will not get updates for it, and that includes security updates. The longer this goes on the more vulnerable your system will become to security breaches. If you never go online with your machine, not a problem. If you do, I'd take precautions, especially if your kernel is VERY old.

---

### Post by tgalati4 on 2014-07-25
Make the machine dual-boot.  New distro for using the web with 14.04 and the open graphics driver and the old distro for playing games with the proprietary driver but don't use it for web access.  This is not the most convenient way to use a computer, but it preserves your unsupported graphics card for a specific use case and gives you improved security with the latest long term support (LTS) version.

---

### Post by Bucky Ball on 2014-07-25
> **tgalati4 said:**
> Make the machine dual-boot.  New distro for using the web with 14.04 and the open graphics driver and the old distro for playing games with the proprietary driver but don't use it for web access. 

That'll work if you have the room on the drive for another partition. You can use the existing /swap and /home (if you have one) or symlink to the existing /home inside /.  ;)

---

### Post by RadicaX on 2014-07-27
Already pointed out, is the updates! Older ones that are not supported no more, get no updates, including security updates.

Another disadvantage, is that an older kernel might not be made to work with newer tech (Just goes with updates), but there is an advantage to this also, because newer kernels might drop support for older hardware, something to keep in mind and be ready to always go back to an older kernel if this happens. 

Other than those reasons, can not really think of any problems with using older an older kernel, especially if it just works. If possible, you could do what the other said, and just dual boot. This would let you keep doing things you wanted with the web, and a newer kernel, while you could use the older one for your multimedia offline needs.

---

### Post by Axxon95 on 2014-07-27
Just my little bit of input, an option could definitely be a Dual-Boot.
I have quite a collection of older machines here that lost GFX support in later kernels and mesa updates due to hardware limitations and end of life, causing the machine to lose a lot of speed to software raster. I usually keep these machines(with Lucid or other 2.6 kernel Linux OSes) for offline or LAN uses. And for research and tinkering.
It also depends on your CPU(for Soft Raster GL) or GPU(for Hardware GL).

You haven't mentioned any hardware in specific, so I can only throw out there so much.

---

### Post by mastablasta on 2014-07-28
some older hardware got their opensource drivers improved dramaticly

---

