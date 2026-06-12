---
title: "Nvidia drivers and up and down performance"
date: 2008-06-23
forum: The Cafe
---

### Post by Andrewie on 2008-06-23
This is getting crazy, I'll Install one driver and I'll get fast performance in all my games, then I'll install the next version up and everything will slow down to a crawl. Is anyone else experiencing this?

I have a Geforce go 6100

---

### Post by smartboyathome on 2008-06-23
I have the same card (not go, but a Geforce 6100 video) and haven't experienced this.

---

### Post by Andrewie on 2008-06-23
I think I found the problem, I was playing around with some Bios settings and I forgot to return them.

the 9XXXXX drivers ran good
the 169.xx drivers ran bad
the 17X.XX drivers are running good again

I think it's just my crappy shared video card

---

### Post by mnmus on 2008-06-23
I'm on my third day of this Hardy install.

I, too, have the nVidia GeForce 61XX series (GeForce 6150SE, nForce 430 onboard chipset on an HP/ASUS M2N68-LA mobo). The nVidia 169.12 driver mostly worked, aside from a logon screen that had the UN/PW box located well outside the viewing area, but when I finally managed to effect an installation of the nVidia 173.08 driver from the nVidia website, *poof*--back at a maximum 800X600 resolution with no other options but much lower.

*sigh*

This is definitely THE issue where Windows has a decided edge over Linux in general: ease and reliability of driver installation.

Anyone have any magic pill for my nVidia woes?

---

### Post by bufsabre666 on 2008-06-23
> **mnmus said:**
> I'm on my third day of this Hardy install.

I, too, have the nVidia GeForce 61XX series (GeForce 6150SE, nForce 430 onboard chipset on an HP/ASUS M2N68-LA mobo). The nVidia 169.12 driver mostly worked, aside from a logon screen that had the UN/PW box located well outside the viewing area, but when I finally managed to effect an installation of the nVidia 173.08 driver from the nVidia website, *poof*--back at a maximum 800X600 resolution with no other options but much lower.

*sigh*

This is definitely THE issue where Windows has a decided edge over Linux in general: ease and reliability of driver installation.

Anyone have any magic pill for my nVidia woes?

simplify the process and reinstall

```
sudo apt-get update && sudo apt-get install envyng-core envyng-gtk
```

its under the applications->system menu, envyng

select the latest nvidia drivers and install, it sets up your xserver for you, envy i honestly think is the most under rated program, its not perfect but installing them manually sucks

---

### Post by Methuselah on 2008-06-23
> **mnmus said:**
> I'm on my third day of this Hardy install.

I, too, have the nVidia GeForce 61XX series (GeForce 6150SE, nForce 430 onboard chipset on an HP/ASUS M2N68-LA mobo). The nVidia 169.12 driver mostly worked, aside from a logon screen that had the UN/PW box located well outside the viewing area, but when I finally managed to effect an installation of the nVidia 173.08 driver from the nVidia website, *poof*--back at a maximum 800X600 resolution with no other options but much lower.

*sigh*

This is definitely THE issue where Windows has a decided edge over Linux in general: ease and reliability of driver installation.

Anyone have any magic pill for my nVidia woes?

Sorry for your problems, but windows doesn't *generally* have the edge here. The linux way is not to download drivers and install but to have them already included in the kernel. At boot, the OS probes your hardware and enables the necessary drivers. For drivers to go into the kernel the source code must be available and it has to go through a peer review process etc. That's why the vast majority of your hardware probably worked with linux without you doing a single thing. Unfortunately, nobody in the linux community can really help you when closed NVidia drivers prove unstable. :(

Pretty much your only option now is to complain to NVidia, and complain you should. Nvidia is pretty much the main holdout here. You might say a  closed driver is better than none but you might think differently after fighting with it trough kernel updates etc. Intel has open source drivers and AMD/ATI is actively working to facilitate that. In fact, if you want guaranteed support under linux it's best to go with intel. Unfortunately, they don't really have discrete graphics chips yet just integrated. That's why I have an ATI card right now.

---

