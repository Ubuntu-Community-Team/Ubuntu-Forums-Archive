---
title: "Skylake and 16.04"
date: 2015-12-25
forum: Ubuntu Development Version
---

### Post by fjgaude on 2015-12-25
Can anyone give be a clue as to how to make my /dev/sda3 partition work as well as /dev/sdb7. The former is an SSD; the later an HDD, likely has nothing to do with the video speed.

Notice one has vesa, the other fbdev as video drivers. If I knew how to change out fbdev for vesa I think I'd be in business. Both partitions seem to function correctly for a 16.04 install and using Skylake HD530 video. Maybe just intel driver is needed? sdb7 is ten times faster than sda3.

Please, if you can help!

Thanks!

frank

on ASRock sda3 (SSD) Skylake
frank@flash:~$ inxi -b
System:    Host: flash Kernel: 4.3.0-2-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASRock model: Z170 Gaming-ITX/ac
           Bios: American Megatrends v: P1.50 date: 11/04/2015
CPU:       Dual core Intel Core i3-6100 (-HT-MCP-) speed/max: 3699/3700 MHz
Graphics:  Card: Intel Sky Lake Integrated Graphics
           Display Server: X.Org 1.17.3 drivers: fbdev,intel (unloaded: vesa)
           Resolution: 2560x1440@93.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.6, 256 bits)
           GLX Version: 3.0 Mesa 11.0.7
Network:   Card-1: Intel Ethernet Connection (2) I219-V driver: e1000e
           Card-2: Broadcom BCM4352 802.11ac Wireless Network Adapter
           driver: bcma-pci-bridge
Drives:    HDD Total Size: 756.2GB (32.1% used)
Info:      Processes: 231 Uptime: 3 min Memory: 870.6/15736.6MB
           Client: Shell (bash) inxi: 2.2.28 
---

on ASRock sdb7 (HDD) Skylake
Graphics:  Card: Intel Sky Lake Integrated Graphics
           Display Server: X.Org 1.17.3 drivers: vesa,intel (unloaded: fbdev)
           Resolution: 2560x1440@0.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.6, 256 bits)
           GLX Version: 3.0 Mesa 11.0.7

works as it should but for compiz taking up 25% of the CPU cycles
---

on ASUS Haswell box
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller 
           X.Org: 1.15.1 drivers: intel (unloaded: fbdev,vesa) Resolution: 2560x1440@60.0hz 
           GLX Renderer: Mesa DRI Intel Haswell Desktop GLX Version: 3.0 Mesa 10.1.3
---

---

### Post by mc4man on 2015-12-26
Well running on llvmpipe isn't going to prove too use-able, it's only value seems to be  giving a log in to figure out how to get on a driver.
I've a skylake laptop though not here atm, 16.04 worked ok in a test a little while back though it has a HD520 if that matters.. 

Did you happen to use nomodeset to boot to live before install, if so ck. your install's kernel options for that & if there get rid of it.

---

### Post by fjgaude on 2015-12-26
Thanks for the reply!

Yes, nomodeset is used on installs, all three. That is or was the only way to get to a desktop, else a blank.

Now please, if you can, suggest what it takes to remove llvmpipe driver and replace it with, I guess, intel. I wonder what vesa has to do with it all?

---

### Post by grahammechanical on 2015-12-26
I have no experience with Intel integrated video systems. So, I am not sure if I am stating the obvious or something stupid. Additional Drivers?

I do know a couple of things. Ubuntu uses llvmpipe to give an approximation of Unity 3D on machines that have video adapters that cannot do hardware accelerated 3D rendering. This is not your situation. The other case use I have seen for llvmpipe is when there is some kind of problem with proprietary video drivers.

There is a third case use for llvmpipe that I do not see with Xenial. When we select Recovery Mode Resume.

I also know that vesa is old technology. Although I have just read that vesa has something to do with the specification for DisplayPort. So, 2 questions come into my mind. Is the video connector the difference between these two machines? Is there an Intel Linux driver for Intel Sky Lake?

[http://askubuntu.com/questions/698168/cant-get-intel-hd-graphics-530-skylake-i7-6700-to-work](http://askubuntu.com/questions/698168/cant-get-intel-hd-graphics-530-skylake-i7-6700-to-work)

You may need the 4.4 kernel

[http://www.phoronix.com/scan.php?page=article&item=intel-sklxeon-compilers&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-sklxeon-compilers&num=1)

[http://www.phoronix.com/scan.php?page=article&item=intel-xeon-1245v5&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-xeon-1245v5&num=1)

[http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset](http://www.phoronix.com/scan.php?page=news_item&px=WKS-GT2-No-Modeset)

Regards.

---

### Post by fjgaude on 2015-12-26
The two partitions are on the same machine, an ASRock, different drives. The connection is an HDMI, though the MB has a DP. I'm not using other than the integrated GPU, no external graphics card.

After reading over your askubuntu link I see we have a complex situation. I may just have to wait until Ubuntu and Linus fix the situation for skylake. Up to four more months, if then.

I'll keep playing around trying to get sda3 working as well as sdb7. <smile>

Any thoughts?

---

### Post by mc4man on 2015-12-26
Can you now boot without nomodeset?
Here I had no issue with the 4.3 kernel, no add. kernel options from default supplied needed. I may be able to try again tonight to see if anything has  changed over last couple of weeks.
(- the only other difference is my laptop came with a i7 u cpu. I didn't notice nor knew what the u meant, now I do though due to some unfortunate circumstances wasn't able to use the laptop until the 14 day return was over so am stuck with...

Otherwise have you tried removing nomodeset & using this instead as a kernel option?
```
i915.preliminary_hw_support=1
```

---

### Post by fjgaude on 2015-12-26
I'm using an i3 until I can afford something faster. I did use the i915 with 15.10 but with no luck. Will try with 16.04, latest update, and see... no big deal, just a matter of time before the OS is fixed.

Thanks for giving me advise as it seems few folks are using skylake at present.

---

### Post by fjgaude on 2015-12-27
Okay, folks, after much playing around I switched from HDMI to DP and voila, I got this:

frank@flash:~$ inxi -b
System:    Host: flash Kernel: 4.4.0-040400rc5-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASRock model: Z170 Gaming-ITX/ac
           Bios: American Megatrends v: P1.50 date: 11/04/2015
CPU:       Dual core Intel Core i3-6100 (-HT-MCP-) speed/max: 799/3700 MHz
Graphics:  Card: Intel Sky Lake Integrated Graphics
           Display Server: X.Org 1.17.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 2560x1440@59.95hz
           GLX Renderer: Mesa DRI Intel Skylake DT GT2
           GLX Version: 3.0 Mesa 11.0.7
Network:   Card-1: Intel Ethernet Connection (2) I219-V driver: e1000e
           Card-2: Broadcom BCM4352 802.11ac Wireless Network Adapter
           driver: bcma-pci-bridge
Drives:    HDD Total Size: 756.2GB (32.1% used)
Info:      Processes: 250 Uptime: 1 min Memory: 615.2/15736.5MB
           Client: Shell (bash) inxi: 2.2.28 

Notice only the intel was loaded and the GLX Renderer is skylake. I booted into kernel 4.4 without nomodeset. Likely this is a minor bug in some code and will be fixed soon.

I trust that 16.04 will be a great LTS distro. <smile>

Once again, thanks!

---

