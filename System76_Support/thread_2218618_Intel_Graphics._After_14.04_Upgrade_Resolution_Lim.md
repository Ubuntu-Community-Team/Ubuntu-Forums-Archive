---
title: "Intel Graphics. After 14.04 Upgrade Resolution Limited"
date: 2014-04-21
forum: System76 Support
---

### Post by t-7 on 2014-04-21
I originally posted this in the ubuntu hardware forum because I didn't realize this System76 forum existed. I have a Ratel Performance I bought last year and just upgraded to 14.04.

I have a 30" Dell monitor connected through DVI to a System76 with Intel  graphics (details below). After upgrading to 14.04 my resolution is now  limited to 1920x1200, before I was running at 2560x1440 (or 2560x1600, I  don't remeber).

I read that 14.04 has the latest driver and the Intel driver installer  says trusty isn't supported. I assume it is a driver/kernel issue, is  that safe to say?

```
 *-display
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64) 

```

---

### Post by 23dornot23d on 2014-04-21
If you type xrandr into a terminal what does it give back ....... just after some more information to start with
it may help others.

[B]xrandr

[/B]as an example on my own machine it gives back the following .....> 
K53SV:~$ xrandr
Screen 0: minimum 320 x 200, current 2646 x 768, maximum 32767 x 32767
LVDS1 connected 1366x768+1280+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1280x720+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1280x720       50.0*+   60.0     59.9  
   1920x1080i     60.1     50.0     60.0  
   1440x576i      50.1  
   1440x480i      60.1     60.1  
   720x576        50.0  
   720x480        60.0     59.9  
   640x480        60.0     59.9  
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)



---

### Post by t-7 on 2014-04-22
xrandr gives:

```
$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 32767 x 32767
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 641mm x 401mm
   1920x1200      60.0* 
   1600x1200      60.0  
   1280x1024      75.0     60.0  
   1280x800       59.9  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by pxntium on 2014-04-23
Same problem and same output. My monitor supports up to 2560x1080 and with 14.04 is limited to 1920x1080
With 13.10 works fine at 2560x1080

Regards

---

### Post by pxntium on 2014-04-24
I tried with a newest Nvidia and the same results, the maximum resolution is 1920x1080. I test it with the privative Nvidia drivers.
I'm going back to 13.10 where works fine with the correct resolution.

Regards
Fran

---

### Post by sam-vilain on 2014-04-28
I experienced the same thing, and booting off the 13.10 kernel (ie, Linux Kernel version 3.11.0) at the GRUB prompt is a useful workaround.  (ie, during system bootup press escape before the splash screen, and go to "Advanced Ubuntu Options" and select a 3.11.x kernel).

This may be related to the new kernel's preference to boot with VESA support;

excerpted [FONT=courier new]/var/log/kern.log[/FONT] from 3.11.0 (high resolution output works on this kernel):

[FONT=courier new]Apr 28 12:09:27 edgar kernel: [    0.000000] Linux version 3.11.0-20-generic (buildd@aatxe) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #34-Ubuntu SMP Tue Apr 1 20:40:25 UTC 2014 (Ubuntu 3.11.0-20.34-generic 3.11.10.6)[/FONT]
[FONT=courier new]Apr 28 12:09:27 edgar kernel: [    0.268049] pci 0000:00:02.0: Boot video device[/FONT]
[FONT=courier new]Apr 28 12:09:27 edgar kernel: [    0.719416] i915 0000:00:02.0: setting latency timer to 64[/FONT]
[FONT=courier new]Apr 28 12:09:27 edgar kernel: [    0.738931] i915 0000:00:02.0: irq 44 for MSI/MSI-X[/FONT]
[FONT=courier new]Apr 28 12:09:27 edgar kernel: [    0.997483] fbcon: inteldrmfb (fb0) is primary device[/FONT]
[FONT=courier new]Apr 28 12:09:27 edgar kernel: [    2.720630] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device[/FONT]
[FONT=courier new]Apr 28 12:09:27 edgar kernel: [    2.720631] i915 0000:00:02.0: registered panic notifier[/FONT]
[FONT=courier new]Apr 28 12:09:27 edgar kernel: [    2.722477] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)[/FONT]
[FONT=courier new]Apr 28 12:09:27 edgar kernel: [    2.722501] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8[/FONT]


Output from 3.13.0:

[FONT=courier new]Apr 28 12:05:36 edgar kernel: [    0.000000] Linux version 3.13.0-24-generic (buildd@panlong) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 (Ubuntu 3.13.0-24.46-generic 3.13.9)[/FONT]
[FONT=courier new]Apr 28 12:05:36 edgar kernel: [    0.265338] pci 0000:00:02.0: Boot video device[/FONT]
[FONT=courier new]Apr 28 12:05:36 edgar kernel: [    0.638129] vesafb: mode is 1024x768x32, linelength=4096, pages=0[/FONT]
[FONT=courier new]Apr 28 12:05:36 edgar kernel: [    0.638130] vesafb: scrolling: redraw[/FONT]
[FONT=courier new]Apr 28 12:05:36 edgar kernel: [    0.638131] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0[/FONT]
[FONT=courier new]Apr 28 12:05:36 edgar kernel: [    0.638370] vesafb: framebuffer at 0xe0000000, mapped to 0xffffc90004e80000, using 3072k, total 3072k[/FONT]
[FONT=courier new]Apr 28 12:05:36 edgar kernel: [    0.741117] fb0: VESA VGA frame buffer device[/FONT]
[FONT=courier new]Apr 28 12:05:36 edgar kernel: [    0.849066] **fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver**[/FONT]
[FONT=courier new]Apr 28 12:05:36 edgar kernel: [    0.891245] i915 0000:00:02.0: irq 44 for MSI/MSI-X[/FONT]
[FONT=courier new]Apr 28 12:05:36 edgar kernel: [    1.278478] fbcon: inteldrmfb (fb0) is primary device[/FONT]
[FONT=courier new]Apr 28 12:05:36 edgar kernel: [    2.981806] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device[/FONT]
[FONT=courier new]Apr 28 12:05:36 edgar kernel: [    2.981806] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device[/FONT]
[FONT=courier new]Apr 28 12:05:36 edgar kernel: [    2.981806] i915 0000:00:02.0: registered panic notifier[/FONT]
[FONT=courier new]Apr 28 12:05:36 edgar kernel: [    2.983292] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)[/FONT]



The highlighted line is an obvious difference.  It's possibly a bug that it doesn't succeed in replacing the [FONT=courier new]vesafb[/FONT] with [FONT=courier new]inteldrmfb[/FONT] during initialization, or this might be a total red herring.  But booting off the old kernel definitely works around the issue.

---

### Post by t-7 on 2014-04-29
Thanks, I suspected it was kernel config related. 

Is there a better way to bring this to System76's attention at least? They must be shipping a working setup with these now on 14.04.

---

### Post by sam-vilain on 2014-05-08
If you go into your orders within System76, you can file a support request against the order.  However, most of the time they tell you to log faults like this upstream.

---

### Post by slinkp on 2014-11-26
I filed a bug upstream with Ubuntu here:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1391984](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1391984)

---

