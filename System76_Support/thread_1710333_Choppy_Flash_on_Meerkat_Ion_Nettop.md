---
title: "Choppy Flash on Meerkat Ion Nettop"
date: 2011-03-19
forum: System76 Support
---

### Post by Rob_H on 2011-03-19
Hi all. I just bought the Meerkat Ion Nettop and installed Kubuntu 10.10 (32-bit) on it. I'm using Flash 10.2 and the Nvidia 260.19 proprietary driver. I expected decent fullscreen video performance on Hulu, since Flash 10.2 is supposed to be accelerated on the Ion, but it's quite choppy. Anyone else experiencing the same thing? Is there something I can do to get better performance? Fullscreen video on XBMC playing a local MPEG-4 file is very good, so the problem is specific to Flash.

---

### Post by Rob_H on 2011-03-21
bump

---

### Post by isantop on 2011-03-22
Go ahead and point your firefox to about:plugins. Scroll down until you reach the Shockwave Flash section, then take a screenshot of it with the PrtSc key. Also, what version of Ubuntu is installed? Is it 32-bit or 64-bit?

---

### Post by Rob_H on 2011-03-22
> **isantop said:**
> Go ahead and point your firefox to about:plugins. Scroll down until you reach the Shockwave Flash section, then take a screenshot of it with the PrtSc key. Also, what version of Ubuntu is installed? Is it 32-bit or 64-bit?

It is Kubuntu 10.10 32-bit. Shockwave Flash version as reported in Firefox is 10.2 r152. (Can't take a screenshot at the moment because I'm not sitting in front of it.) Thanks!

---

### Post by isantop on 2011-03-22
Do you have the proprietary Nvidia Drivers loaded?

---

### Post by Rob_H on 2011-03-22
Yes, proprietary NVIDIA driver from the Ubuntu Maverick repo is installed and enabled (the **nvidia-current** package).

I saw a message [here]("http://forum.xbmc.org/showthread.php?t=86591&page=2") that suggests the problem is Hulu-specific and not related to software configuration. Can you check to see if video acceleration *should* work in Hulu on a "stock" Meerkat Ion Nettop?

---

