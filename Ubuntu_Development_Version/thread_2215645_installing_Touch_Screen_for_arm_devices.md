---
title: "installing Touch Screen for arm devices"
date: 2014-04-07
forum: Ubuntu Development Version
---

### Post by nataku2 on 2014-04-07
Hi All,

I've been playing around with Ubuntu for the last couple month and recently I've been tasked with a job to setup and try a few distros on micro PCs and install touch screen on them. I have searched and found ways around most issues, but I can not seem to find much documentation on installing Touch Screen manually. (all the ones that I found were for 10/11/may be 12.

I'm using Ubuntu created by a guy for Cubieboard2, from here -> [http://www.gplsquared.com/eoma_boot/eoma_boot.html#Ubunt_13_04_3D](http://www.gplsquared.com/eoma_boot/eoma_boot.html#Ubunt_13_04_3D)
The TouchScreen given to me is Acer T232HL

Being a rookie I do not posses the knowledge to build an image from the ground up. (or at least I have failed miserably) So I've been relying on other people's images to get these boards up and running. Cubieboard2 uses AllWinner A20 (ARM) for processing so the solution I've found doesn't always seem to work (for other stuff, touch never worked) I was able to get touch working on a NitrogenN6 (a different board) with Debian, but Debian isn't exactly as user friendly as Ubuntu so I've been trying to get the Ubuntu version working. I have not found a image of Ubuntu for NitrogeN6 so I haven't tried that yet.

Any help would be appreciated.

Info here again:
Board: Cubieboard 2 (don't think this matters)
Type: ARM
Touch Monitor: Acer T232HL
lsusb: Bus 001 Device 014: ID 2149:2306 (This one pops and disappears when I connect and disconnect the monitor, strangely there is no name after it)

lsmod:
disp_ump
mali_drm
drm
mali
ump
rfcomm
ppdev
bnep
lp
bluetooth
parport
usb_storage

(did not see anything for touch screen, which is why I think I need to manually install it, but I have been unable to find the correct way to do so...)

EDIT: almost forgot, the current distro on it is 13.10

Thanks,

---

### Post by grahammechanical on 2014-04-07
I do not think that lsmod will detect monitors. I have found this for you

[https://apps.ubuntu.com/cat/applications/saucy/touchegg/](https://apps.ubuntu.com/cat/applications/saucy/touchegg/)

[https://code.google.com/p/touchegg/](https://code.google.com/p/touchegg/)

I have no idea how well it works with a monitor. And Ubuntu does have as default an on screen keyboard called Onboard. Ubuntu 13.10 does have some code from the Ubuntu phone platform. Things get better with 14.10 but by 14.10 or 15.04 at the latest the Ubuntu mobile code will be converged in the Ubuntu desktop code base. So, things will definitely get better for touch screen monitor use.

Regards.

---

### Post by nataku2 on 2014-04-07
Thanks for the link, I just noticed a couple minute ago playing around with debian distro on the Nitrogen board that it shows the touchscreen name in /dev/input/by-id, so I thought I'd look there booting into the Cubieboard with Debian and the touchscreen is missing

I think the Ubuntu part might be doing the same thing, is there somewhere in Ubuntu that I can check to be sure that certain devices (in this case the touch screen) are/aren't being detected?

---

