---
title: "kubuntu splash screen"
date: 2010-10-14
forum: The Cafe
---

### Post by inobe on 2010-10-14
completely messy, whats wrong with it.

i can't get a screeny but i will find my camera and record a short clip or take a pic.

it's not as nice as this one

[IMG]http://lh5.ggpht.com/_wNH6h6C1mY0/S9q4A3y_GXI/AAAAAAAAAqU/CU4I9u0V_r0/s400/plymouth4.png[/IMG]

it flickers and shows some commands happening

---

### Post by inobe on 2010-10-14
[click to watch in firefox]("http://www.itsyourpc.org/duane/files/splash.swf")

---

### Post by Mr. Picklesworth on 2010-10-14
That's probably because you're running Nvidia's proprietary driver (or ATI's, I think), which doesn't have the kernel component necessary to support Kernel Modesetting. As a result, the boot splash falls back to its boring alternative as the display mode isn't guaranteed to be set right until X starts.

If you switch to a free driver for your respective graphics hardware, you will see a much prettier and snappier startup sequence.

---

### Post by inobe on 2010-10-15
this started with 10.04, this is 10.10, i'm wondering why the last two distributions are affected and none of the priors.

im also wondering if there is a remedy other than switching to the os driver.

what has changed to cause this ?

thanks

---

### Post by Khakilang on 2010-10-15
I got the same thing on my splash screen and when I shutdown my screen got a green smudge on the bottom left. But I don't really bother.

---

### Post by inobe on 2010-10-15
in 10.04 i ignored it, maybe it really wasn't an issue and something that could be ignored, seeing it again makes me think i'm not the only one that sees this.

definitely a quality issue, i think the splash screen shouldn't go unnoticed or ignored any further.

---

### Post by NightwishFan on 2010-10-15
It is actually normal for plymouth. Ubuntu did not start to use plymouth until 10.04. I do like usplash better, however Plymouth is the way forward for a few reasons. When it works it will work awesome.

There is a fix. Quote from /usr/share/doc/plymouth/README.Debian
```
High-color graphics on nVidia, ATI and other cards
--------------------------------------------------

Our default configuration uses low-color graphics on cards or drivers
for which "Kernel Mode Setting" (in-kernel graphics drivers) are not
available.

This is because the driver that permits high-color graphics tends to
cause issues with suspend and resume, and we opted to prefer that
working.

    For nVidia and ATI users, the default "nouveau" and "radeon"
    drivers are Kernel Mode Setting enabled, but do not always
    provide 3D capability at the current time.  By switching to
    using the restricted/non-free nvidia-glx or fglrx drivers,
    you will gain 3D capability at the loss of a high-color
    splash screen.

You can however chose to enable high-color (and resolution) console
if you find it doesn't affect suspend/resume for you, or you don't
use that feature.

There are various methods of doing this, the most robust is the
following four steps:

 Append video=vesafb to the GRUB_CMDLINE_LINUX_DEFAULT in
   /etc/default/grub
 sudo update-grub

 echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
 sudo update-initramfs -u
```

For some Intel cards that get brief or no splash these two commands alone are needed:
```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
 sudo update-initramfs -u
```

---

### Post by Ctrl-Alt-F1 on 2010-10-15
That's rad Nightwish!  I had no idea (I mean I knew it was something to do with Plymouth, but not the details).  I don't think I'll use it as I like to suspend my machine sometimes, but its nice to know I have the option.  Thanks!  :)

---

### Post by NightwishFan on 2010-10-15
The next couple release plymouth should be sorted out.

---

### Post by johntaylor1887 on 2010-10-15
The splash screen is the least of my concerns. As long as my computer is stable and does what I want, I'm happy.

---

### Post by inobe on 2010-10-15
> **NightwishFan said:**
> It is actually normal for plymouth. Ubuntu did not start to use plymouth until 10.04. I do like usplash better, however Plymouth is the way forward for a few reasons. When it works it will work awesome.

There is a fix. Quote from /usr/share/doc/plymouth/README.Debian
```
High-color graphics on nVidia, ATI and other cards
--------------------------------------------------

Our default configuration uses low-color graphics on cards or drivers
for which "Kernel Mode Setting" (in-kernel graphics drivers) are not
available.

This is because the driver that permits high-color graphics tends to
cause issues with suspend and resume, and we opted to prefer that
working.

    For nVidia and ATI users, the default "nouveau" and "radeon"
    drivers are Kernel Mode Setting enabled, but do not always
    provide 3D capability at the current time.  By switching to
    using the restricted/non-free nvidia-glx or fglrx drivers,
    you will gain 3D capability at the loss of a high-color
    splash screen.

You can however chose to enable high-color (and resolution) console
if you find it doesn't affect suspend/resume for you, or you don't
use that feature.

There are various methods of doing this, the most robust is the
following four steps:

 Append video=vesafb to the GRUB_CMDLINE_LINUX_DEFAULT in
   /etc/default/grub
 sudo update-grub

 echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
 sudo update-initramfs -u
```

For some Intel cards that get brief or no splash these two commands alone are needed:
```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
 sudo update-initramfs -u
```


amazing... i had no idea they tried to save suspend/ resume.

---

### Post by Half-Left on 2010-10-15
> **NightwishFan said:**
> The next couple release plymouth should be sorted out.

Funny how Plymouth's splash works in Fedora on three machines I've tested, even with the NVIDIA binary driver.

---

### Post by NightwishFan on 2010-10-15
I am not in charge of plymouth, so I couldn't tell you.

---

### Post by inobe on 2010-10-15
[http://lizards.opensuse.org/2010/10/12/getting-plymouth-on-opensuse/](http://lizards.opensuse.org/2010/10/12/getting-plymouth-on-opensuse/)

soon to appear in opensuse.

> There are a few patches that help in getting rid of this bad transition.

    * xorg-server needs to be patched to not clear the screen to black at start up, but instead use the current screen (the bgnr patch that brings the “-nr” option is already shipped with 11.3 and Factory)
    * the video driver needs to be patched to make good use of this functionality (nouveau needs to be patched, no idea for the open sourced ATI and Intel drivers)
    * GDM needs to be patched to be able to use the vt1 by default. There is Fedora patch that do the trick, and Fedora/Kubuntu made it working with KDM. As a sidenote, I don’t think those patches will make their way upstream without a much proper integration.



---

### Post by inobe on 2010-10-15
im going to jump this on page one as there are lots of brains in the audience today:)

i won't go near the os driver at the moment, too many things perfected and not willing to break anything just yet.


the main question...

where can i look or what can i do to help the community resolve this quicker, or shall i wait because the bug is being taken care of and there's no more i can do and i just need to wait till the next release ?

---

### Post by Half-Left on 2010-10-15
Some NVIDIA cards just won't support certain resolutions like 16:10. I cannot use any 16:10 resolutions, only 4:3. I think this is a card limitation thanks to the manufacturer not supporting VESA 3.0 fully or something like that. I heard NVIDIA doesn't properly support VESA 3.0, even though they claim to.

No 16:10 framebuffer usually means broken VESA support somewhere.

---

