---
title: "Installation issues"
date: 2013-04-07
forum: Ubuntu Studio
---

### Post by junglistric on 2013-04-07
Hello,

I'm having installation issues with multiple distros of Ubuntu Studio (12.10 & 13.04 betas).  The issue is somewhat different each time I try to install.  I have tried liveCDs and USB sticks.  Sometimes the installation hangs at the splash page (spinning circle).  When I hit Ctrl+Alt+F1, the error messages are similar to the ones experienced by this user:

[http://ubuntuforums.org/showthread.php?t=2037074](http://ubuntuforums.org/showthread.php?t=2037074)

I have also tried upgrading to ubuntu studio from ubuntu 12.10 (that distro installs fine, as well as Mint).  The software packages seem to be installed but I still get the regular generic kernel (not lowlatency) and the desktop is still the old flavor.  Only the Ubuntu Studio splash page (spinning circle) shows up when I restart the system.

Any help would be appreciated.  I have tried different HDDs as well.  My system is MSI P6N-SLI Platinum, 2xNvidia 8600GT, 3.0ghz Intel Core 2 Duo, 4GIG RAM.

---

### Post by zequence on 2013-04-08
You can install linux-lowlatency separately. To get realtime privilege, you'll need to at least add yourself to audio group (note that this has nothing to do with the kernel).

Are you sure the live usb stick hangs at the spalsh screen? I would be interested to know exactly what kind of issue you have when installing with USB. Burned DVDs can be a bit flakey, as it's hard to know if the burn was perfectly successful or not.

---

### Post by junglistric on 2013-04-08
I've tried installing linux-lowlatency (image, headers, etc) and sometimes it works sometimes it doesn't.  It broke one of my installs so I'm afraid to try again.  When it boots it causes my system to freeze shortly after booting.  I was successful with installing Ubuntu Studio once, but messed up the install when I upgraded to nvidia video drivers.  That's the only time the lowlatency kernel ran smoothly.

With the USB stick alone, it dumps me at the boot: prompt.

---

### Post by zequence on 2013-04-08
Nothing gets broken by installing linux-lowlatency, but the driver modules may need to be rebuilt for it - this is a bug in how dkms seems to work in some releases.
One simple way to get around this problem is to first enable the free drivers, instead of the proprietary ones. Install linux-lowlatency, then boot into linux-lowlatency. Once running linux-lowlatency, install nvidia drivers, so they will be built against the right kernel.

linux-lowlatency is a clone of linux-generic, with only a couple of small config diffs. Anything that works with -generic, will work with -lowlatency.

---

### Post by junglistric on 2013-04-08
Thank for your info, I will try it.

The USB stick hangs at the Ubuntu Studio splash screen (spinning circle).  The drive is being accessed but no progress.  I've unplugged all the extraneous HDDs and DVDROM drives, and the error messages are gone, but no progress on the install.  Ctrl+Alt+F1 shows a red/pink letter near the upper left hand corner.

---

### Post by junglistric on 2013-04-08
The Ubuntu 12.10 to Ubuntu Studio worked, I just had to log into the other version of the OS upon startup.

Now the low-latency part - I've installed the linux-lowlatency, linux-headers-lowlatency, and linux-image-lowlatency though the software center, and when I try to boot into it, it hangs on 'Loading initial ramdisk...'  I have to boot into generic.

Is there anything specific I need to do to get low-latency kernel installed?

---

### Post by zequence on 2013-04-08
What do you mean by the other version of the OS. There's really only one version: Ubuntu. Ubuntu Studio, like all flavors of Ubuntu, as well as Ubuntu itself, are just different configurations of the same OS. In short, they just have a different set of applications preinstalled. In all other respects, they are the same.

You don't need to do anything specific to install linux-lowlatency, other than to install it. At this point, I'm a bit unsure what your problem is.

How are you creating your bootable usb stick? I usually use unetbootin, as it has proved reliable for me. I also download the ISO manually myself.

---

### Post by junglistric on 2013-04-08
Hello.  Yes, I meant that I had to choose Ubuntu Studio at login to log into that flavor.

Yes I've used unetbootin as well as Rufus in Win8.  Both methods give installation hangs at the splash page, and sometimes the error that I linked to in my first post.

---

### Post by vsg on 2013-06-08
Hello, all.

I think I am having the same problem with UbuntuStudio 12.04. I see the same symptoms, with the system hanging at various times of startup.  Sometimes I even get as far as the login screen.  I also saw similar log messages in console 7.

One thing I found is that I can run the live version of UbuntuStudio (with the default low-latency kernel) off of a flash drive if I disconnect my SATA hard drive. If the drive is connected, the live UbuntuStudio won't run. So I was wondering if it might be some sort of bios or SATA driver problem.  Here are my bios and motherboard details:
```
Motherboard:  EVGA 
Product Name: 122-CK-NF68
Serial Number: 1

BIOS: Phoenix Technologies, LTD
Version: 6.00 PG
Release Date: 09/04/2008
```

I updated my motherboard firmware, which was supposed to fix some SATA issues, but I still have the problem.

Does anyone have any thoughts on this?  Should I update my bios?  I have had trouble finding a free way to do that...

Thanks in advance for any advice.

---

