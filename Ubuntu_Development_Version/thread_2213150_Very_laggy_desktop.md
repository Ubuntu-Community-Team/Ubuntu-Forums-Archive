---
title: "Very laggy desktop"
date: 2014-03-25
forum: Ubuntu Development Version
---

### Post by Lucetius on 2014-03-25
Upgraded to 14.04 and everything appears to have gone well, but the desktop is now very laggy with stuttering if I move windows around or maximize/close 

Games are down to just 1fps.

If I switch to the proprietary driver, the problem goes away, however switching back to the open driver brings the problems back again.

I have tried updating to the latest open driver but it has had no affect.

This was not a problem on 13.10 which ran butter smooth.

System specs

Intel E8400 core 2 duo
4 GB RAM
AMD 5870 1GB

---

### Post by grahammechanical on 2014-03-25
Ubuntu now uses Gallium llvmpipe as a fallback mode for graphic adapters that cannot give hardware accelerated 3D graphics. We also get Gallium llvmpipe when we run Recovery mode>Resume. It does give a slower than expected user experience.

Not only that but there has been a change to the way windows enlarge. We no longer get that orange preview but the window should enlarge in step with the movement of the mouse. On some systems this movement may show as laggy. Especially if system resources are already being used extensively.

You do say that this goes away when you switch to proprietary video driver. It is clearly is an issue with the open source driver and not with Ubuntu Trusty Tahr.

Regards.

---

### Post by pauljwells on 2014-03-25
Which OS driver is being used? For some Intel integrated graphics chips the software Gallium driver is loaded with lvmpipe instead of the proper intel hardware driver. I had this issue on an Atom powered netbook. I uninstalled the nouveau package and it loaded up the intel driver on the next reboot.
See this (old) bug for some background [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1074779]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1074779")

---

### Post by james114 on 2014-03-26
Maybe you need to update your graphics driver to fit 14.04

---

### Post by Lucetius on 2014-03-26
Graphics driver is updated to the latest open source using oibaf's PPA here

[http://www.phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers](http://www.phoronix.com/forums/showthread.php?50038-Updated-and-Optimized-Ubuntu-Free-Graphics-Drivers)

Desktop remains very laggy and games will not play.

3d acceleration on the desktop has apparently been disabled.

No issues with catalyst driver, so perhaps it is an open source driver issue? Graphics card is AMD HD5870 1GB and has had no issues playing games until now.

Very strange Canonical would release a distribution with such poor performance by default.

EDIT: I remember there was an error when upgrading to 14.04 and had to manually force it to finish. I wonder if a config file got corrupted somewhere?

Fresh install might be the solution?

---

### Post by LinuXXuniL on 2014-03-26
Hi. I am with this problem since Ubuntu 13.04 and it is related to some conflicts between graphic card and open source default driver, that I don't fully understand. As a solution, as soon as I install Ubuntu, I move to the proprietary driver. You can try a fresh install but the solution is to NOT use default video driver, IMO.

---

### Post by buzzingrobot on 2014-03-26
Dunno if this applies in this instance, but... I did a clean install using yesterday's 14.04 daily, on Intel video.  Several previous installs were a breeze, but this time I had to use "nomodeset" to persude the install image to boot correctly. The install was normal after that. I spent the rest of the day wondering why things were sluggish. Checked "Details" and saw it was on the Gallium driver. I'd forgotten to remove "nomodeset" from grub's config. Did that, ran update-grub, rebooted, and all was as it should be.

---

### Post by Stinger on 2014-03-26
Try these commands and let's see what you got ;)
```
glxinfo | grep render
```
and
```
lspci | grep VGA & sudo lshw -C video
```
Remember to type in your password when asked for
Here is my output for comparison :
> [1] 8946
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV730 XT [Radeon HD 4670]
[sudo] password for xxxx: 
  *-display               
       description: VGA compatible controller
       product: RV730 XT [Radeon HD 4670]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:44 memory:d0000000-dfffffff memory:fe9f0000-fe9fffff ioport:c000(size=256) memory:fe9c0000-fe9dffff
[1]+  Done                    lspci | grep --color=auto VGA

---

### Post by ventrical on 2014-03-26
This is the proper open source driver for that series I believe... and everything (including ccsm gizzmos) are working. Gallium does not always designate llvmpipe.



```

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cedar HDMI Audio [Radeon HD 5400/6300 Series]

```

---

### Post by ventrical on 2014-03-26
> **Lucetius said:**
> 

System specs

Intel E8400 core 2 duo
4 GB RAM
AMD 5870 1GB

Is that an Intel MoBo? If so , what is the form factor (number). The firmware has a quirky setting in BIOS on some of the DQ series. Sounds like you know what you are doing . I would say check BIOS settings once again and take a look around. I had a problem with my AMD 5450 card on an Intel MoBo so I put in a nVidia card and works great.

 That would not be a driver problem but a problem with the way the BIOS video settings are set up. I am not sure if a BIOS upgrade would help because I haven't tried that yet.

---

### Post by Lucetius on 2014-04-03
Sorry for delayed reply... here is the outputs of:

"glxinfo | grep render"

> direct rendering: Yes
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer, 
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
    GL_MESA_ycbcr_texture, GL_NV_blend_square, GL_NV_conditional_render,

"lspci | grep VGA & sudo lshw -C video"

> [1] 3222
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cypress XT [Radeon HD 5870]

  *-display               
       description: VGA compatible controller
       product: Cypress XT [Radeon HD 5870]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:44 memory:d0000000-dfffffff memory:fe9c0000-fe9dffff ioport:c000(size=256) memory:fe9a0000-fe9bffff
[1]+  Done                    lspci | grep --color=auto VGA



The motherboard is an Asus P5Q Deluxe with intel P45 chipset

---

### Post by pauljwells on 2014-04-03
This is your problem. Software rendering

```
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
```

See my earlier post (uninstall Nouveau is what worked for me)

---

### Post by ventrical on 2014-04-03
> **pauljwells said:**
> This is your problem. Software rendering

```
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
```

See my earlier post (uninstall Nouveau is what worked for me)

+1

---

### Post by Stinger on 2014-04-03
Have a look at your /var/log/Xorg.0.log file
Look for errors (EE) like:
[ 23.008] [drm] failed to load kernel module "radeon"
[ 23.008] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM

the problem could be related to the ppa you added "ppa: oibaf/graphics-drivers"

I would try this:
1. purge the ppa:
> === Revert to original drivers ===
To revert to standard Ubuntu drivers type the following in a prompt shell:
$ sudo apt-get install ppa-purge
$ sudo ppa-purge ppa: oibaf/graphics-drivers
2.
Purge any unwanted fglrx residue, reinstall and reconfigure the x-server: 
>   sudo apt-get remove --purge xorg-driver-fglrx fglrx*
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg

Don't forget to reboot to activate the changes ! ( but I guess you know that already ) 

Usefull links:
[VideoDriverDetection]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection")

[RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Hope it helps

---

