---
title: "Linux 2.6 kernal ported to the iPhone"
date: 2008-11-29
forum: The Cafe
---

### Post by nick09 on 2008-11-29
[QUOTE=iPhonestalk.com]A rather interesting report has been filtering out of various websites: a 2.6 version of the Linux kernel has been ported to the iPhone. This Linux operating system can be used on the iPhone 2G, iPhone 3G, and first-generation iPod touch platforms.

iPhone Linux

This site: [http://linuxoniphone.blogspot.com/2008/11/linux-on-iphone.html](http://linuxoniphone.blogspot.com/2008/11/linux-on-iphone.html) announced that the Linux 2.6 kernel has been ported to Apple’s iPhone and is fully (more or less) functional, with support for the first and second generation iPhones as well as the first generation iPod touch. They do warn that this is a rough first draft

[IMG]http://www.iphonestalk.com/images/iphonelinux.jpg[/IMG]

of the port, and many drivers are still missing, but it’s enough that a real alternative operating system is running on the iPhone.

This could be an important stepping stone for the true acceptance of the iPhone for a new breed of higher-end tech user.

What’s included so far: the Framebuffer driver, a Serial driver (and over USB as well), and interrupts, MMU and clock. Read-only support for the NAND is nearly complete as well. Touchscreen, sound and wireless networking as still being added, but he anticipates those will be in soon.[/QUOTE]
[Source](http://www.iphonestalk.com/linux-26-kernel-ported-to-the-iphone/)
Though it is a rough draft and touch use is still being developed.

---

### Post by Swarms on 2008-11-29
That is amazing, though I really enjoy the interface of the the iPhone, I would very like to see Android on it too.

---

### Post by smartboyathome on 2008-11-29
> **Swarms said:**
> That is amazing, though I really enjoy the interface of the the iPhone, I would very like to see Android on it too.

Android != Linux. Android is completely different, and would have to be ported separately.

---

### Post by klange on 2008-11-29
I'd venture a guess that the next steps would be porting X, reverse engineering the graphics chipset, and getting some multi-touch input working (not exactly in that order). It is an ARM7 processor, so in theory we could get Ubuntu Jaunty running at some point.

Also, the quote is misleading: there's just a framebuffer terminal, so the only thing you can do is boot it and say "hey, my iPhone is running Linux!".

---

### Post by Swarms on 2008-11-29
> **smartboyathome said:**
> Android != Linux. Android is completely different, and would have to be ported separately.

Yeah I know they are different, but are you saying that if they get a linux kernel and all drivers up and running that they can't put Android on it?

---

### Post by Redache on 2008-11-29
Android isn't Linux. It's different. Even so, I'd imagine Android has an Arm port, right?.

---

### Post by klange on 2008-11-29
> **Redache said:**
> Android isn't Linux. It's different. Even so, I'd imagine Android has an Arm port, right?.

Android is Linux, Linux is not Android. Square-Rectangle conundrum.
There's just a lot more to Android than just Linux (it's a distro, and a display server, and desktop environment, and everything else)

---

### Post by smartboyathome on 2008-11-29
> **WindowsSucks said:**
> Android is Linux, Linux is not Android. Square-Rectangle conundrum.
There's just a lot more to Android than just Linux (it's a distro, and a display server, and desktop environment, and everything else)

No, I thought it was a completely different operating system, with its own kernel and all. I could be wrong though.

---

### Post by bruce89 on 2008-11-29
> **smartboyathome said:**
> No, I thought it was a completely different operating system, with its own kernel and all. I could be wrong though.

See [http://code.google.com/android/what-is-android.html](http://code.google.com/android/what-is-android.html). Android is similar to what Maemo is, but it's completely different (not using GTK+ or GStreamer).

---

### Post by SunnyRabbiera on 2008-11-29
Proves how diverse linux can be :D

---

