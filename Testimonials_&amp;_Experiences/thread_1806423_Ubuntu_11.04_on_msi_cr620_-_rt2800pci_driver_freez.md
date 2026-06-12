---
title: "Ubuntu 11.04 on msi cr620 - rt2800pci driver freezed boot up"
date: 2011-07-17
forum: Testimonials &amp; Experiences
---

### Post by khaan on 2011-07-17
I Just would like to share my experience on installing Ubuntu 11.04 on a msi cr620 laptop, as it could spare some frustration to someone in a similar case.

The Ubuntu 11.04 install/live CD freezes during boot up with the splash screen progress bar. Ctrl+Alt+F1 or anything I can think of simply not working. No way I could find to get the reason.

Tried 32bit / 64bit, tried CD / USB stick. None worked.
Memory test and disk integrity completed without any issue.

I then downloaded the alternative install ISO, which does not boot an Ubuntu to install Ubuntu onto your hard drive. Old style text-based install... That worked pretty well.

Time to boot the installed Ubuntu 11.04 for the first time. Same freezing during splash screen. Disappointing...

There I was able to ask Grub to boot in recovery mode and I got the last output before the system died, which was:

```
phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
```

After some googling I found the following helpful comment:

> This is the wireless driver, you can disable it to at least get the machine to boot by pressing 'e' on the grub boot screen and editing the boot commands...

Find the 'linux' command, it should look something like this:
linux /boot/vmlinuz-2.6.32-24-generic root=UUID=c5b47225-1a42-4dd0-991c-0d883040689d ro quiet splash

There may be some other parameters in there, add the following:
rt2800pci.blacklist=yes

put it after the 'ro'

This disables the driver and allows your machine to boot.


Which allowed me to boot the system, and when I applied all the software updates (mainly kernel updates I suppose) the issue was fixed and things have been working well since (including the wireless, which turned out to be the reason of the freezing).

Hope this helps anyone !
Cheers.

---

