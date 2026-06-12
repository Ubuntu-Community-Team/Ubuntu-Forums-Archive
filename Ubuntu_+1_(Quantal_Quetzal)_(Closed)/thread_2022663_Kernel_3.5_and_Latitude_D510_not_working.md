---
title: "Kernel 3.5 and Latitude D510 not working"
date: 2012-07-11
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by sacridex on 2012-07-11
Hello,

I am testing QQ on a Latitude D510(Pentium M730, GMA 900) and it just wont boot with the 3.5 kernel. I tested with 3.5.0-1/2/3/4. After selecting the kernel in grub, the screen turns black and nothing happens.
Kernel 3.4 works fine, I am just writing this text with it.

And I actually do not know, what logs I could or should post here, so pls tell me.  :)

---

### Post by dino99 on 2012-07-11
first check the .xsession-errors into your /home dir (ctrl+h to unhide it)
and /var/log/

which xserver-xorg-core is installed ? (1.12 or 1.11 ? see it with synaptic)

maybe you need to add some boot option, like nomodeset or noacpi (search : ubuntu boot option)

---

### Post by jfernyhough on 2012-07-11
You can also edit the boot line (Press E), remove "splash quiet" from the kernel line and then press ctrl-X to boot. This should also show which point the boot process stops.

---

### Post by jerrylamos on 2012-07-11
> **jfernyhough said:**
> You can also edit the boot line (Press E), remove "splash quiet" from the kernel line and then press ctrl-X to boot. This should also show which point the boot process stops.

If that doesn't work, add "nomodeset" to the kernel line as well.  A frequent trouble spot is the kernel turns on its version of graphics and then starts X which may or may not work with the previously started graphics mode....

Jerry

---

### Post by sacridex on 2012-07-12
Removing "quiet splash" is not helping anything. Nothing is shown, it just freezes like before. With "nomodeset" I can boot the 3.5 kernel and obviously only use Unity2D.

I booted the 3.5 kernel with regular settings, turned the device off after it froze. Then I started from an USB Live Image, but I cannot read the log files. /var/log/boot.log is empty, the xserssion-errors and xsession-errors.old is kind of binary and cannot be read by gedit. And yes I took the right files from my harddrive, not from the live image file system.

If I boot with the 3.4 kernel now, I have readable log files, but I'm not sure if they are from the crash or the working boot I just did. Anywho, here they are.

---

### Post by sacridex on 2012-07-22
Until today, the daily-live Image didnt work either, I tested it almost every day.
But today it did work, I am able to boot into live mode. Thus I was very optimistic and performed a fresh install. But sadly only the live mode works, the "real" installed mode still does not. The same problem still exists, very confusing. :(

---

### Post by sacridex on 2012-07-26
I updated to kernel 3.5.0-6 today and it works! :)

---

### Post by sacridex on 2012-08-06
RAWR, it does NOT work.
Every time I install a new kernel version, I can boot up once regularily into Unity3D. Thus I accidentally thought the problem is solved. But when I want to boot another time, it does not work any more... I have to use nomodeset to get into Unity2D...
This behaviour seems really weird to me...
It happened with kernel 3.5.0.6/7/8 and 3.6.0-030600rc1. I was able to boot once with 3D hardware support, every further time the boot freezes with a black screen and I have to use nomodeset.

---

### Post by cariboo on 2012-08-06
@scaridex, I may have missed it, but I didn't see any mention of what graphics adapter and driver you are using. Being able to run Unity 2D after using nomodest, points to a graphics driver problem.

---

### Post by sacridex on 2012-08-09
Using "nomodeset" and Unity2D:
xserver-xorg-video-intel 2:2.20.3-0ubuntu1

This is what "lspci -v" says:
> 00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
    Subsystem: Dell Device 01af
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information: Len=09 <?>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 01af
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at dff00000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at ec38 [size=8]
    Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Memory at dfec0000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [d0] Power Management version 2
    Kernel modules: intelfb, i915

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
    Subsystem: Dell Device 01af
    Flags: bus master, fast devsel, latency 0
    Memory at dff80000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [d0] Power Management version 2When I am able to boot into Unity3D again(hopefully with the next kernel release...), I will post the specific output too.

---

