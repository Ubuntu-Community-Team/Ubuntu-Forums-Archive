---
title: "Dual booting Win10 and Ubuntu"
date: 2016-12-19
forum: Ubuntu, Linux and OS Chat
---

### Post by tajreed on 2016-12-19
Are there any laptops that have been released in the past couple of years that truly accommodate Ubuntu and Win 10 in dual boot? I've been struggling with the process on a new Yoga 710. Doing the research seems to indicate that the laptop makers along with MS don't want this to happen. I always been able to dual-boot on older laptops but now it's a mess. Any thoughts?

---

### Post by oldfred on 2016-12-19
Are you referring to this?
 [https://linux.slashdot.org/story/16/09/21/1838252/lenovo-denies-claims-it-plotted-with-microsoft-to-block-linux-installs#comments](https://linux.slashdot.org/story/16/09/21/1838252/lenovo-denies-claims-it-plotted-with-microsoft-to-block-linux-installs#comments)
Lenovo Linux support - many obsolete versions of Linux
[https://support.lenovo.com/us/en/documents/pd031426](https://support.lenovo.com/us/en/documents/pd031426)
 Warning: Microsoft Signature PC program now requires that you can't run Linux. Lenovo Yoga 900 ISK2 UltraBook Sept 2016
[https://ubuntuforums.org/showthread.php?t=2337719](https://ubuntuforums.org/showthread.php?t=2337719)
[http://mjg59.dreamwidth.org/44694.html](http://mjg59.dreamwidth.org/44694.html)

Only seen one or two systems where it was not possible to dual boot.
Some are easier than others, but UEFI just by also making available the old BIOS boot mode using CSM means you have to set more options in UEFI.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

And, at least for now, UEFI Secure boot is not required either by vendors, Microsoft or wide spread virus, so easier not to use it.
      
 [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security 

Some require more work arounds than others. And not all models even by one vendor are the same, although usually similar.

Very new systems even back in BIOS days often had issues as vendors do not develop drivers for Linux, only Windows. So it takes a release or two before drivers catch up with very new hardware. And if not popular hardware may take even longer. Dell is one that develops new drivers and has them in a sputnik package, but it may not apply to all models.

Acer requires a unique setting of "trust" on any boot files other than Windows. But easy to set once you know you have to do that.

Many vendors violate UEFI spec that says to NOT use description as part of UEFI boot. And of course only valid description is "Windows Boot Manager". But if only booting Ubuntu you can use that description to boot Ubuntu/grub2's boot file. Or if dual booting a Fallback or hard drive boot entry usually works, but requires you  to configure it.

---

