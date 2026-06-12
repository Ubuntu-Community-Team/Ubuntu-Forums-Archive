---
title: "Failed boot"
date: 2013-10-10
forum: Ubuntu Development Version
---

### Post by drfox on 2013-10-10
I'm running the current nightly of xubuntu x64, and have been experiencing this problem for a number of weeks.
My PC is an HP with Win8 dual boot efi. Default boot is xubuntu.
If I go through the standard boot, I get a gui login screen. When I log in, after several seconds, the screen goes black.
I have to press the power button to restart.
If I go to grub and select recovery mode, wait for the next menu and then select resume boot, I get the same gui login, but when I log in, I can successfully see my desktop and everything works as expected. 
How do I find out what is hanging up the machine?
Thanks.

---

### Post by oldfred on 2013-10-10
The recovery mode has nomodeset built in as a boot parameter.

You should be able to manually add the nomodeset to grub's boot line, but that still is a temporary fix until you install proprietary drivers or if Intel add boot parameters for that.

What video card/chip are you using?

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by drfox on 2013-10-11
> **oldfred said:**
> The recovery mode has nomodeset built in as a boot parameter.

You should be able to manually add the nomodeset to grub's boot line, but that still is a temporary fix until you install proprietary drivers or if Intel add boot parameters for that.

What video card/chip are you using?


Thanks for the reply, oldfred. The nomodeset didn't work until I stopped being a dummy and remembered to update grub. <slaps forehead>

Hardware information:

Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz

video card:
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Subsystem: Hewlett-Packard Company Device 181c
        Flags: fast devsel, IRQ 16
        Memory at c2000000 (64-bit, non-prefetchable) [size=4M]
        Memory at b0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 4000 [size=64]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
Should I add something other than nomodeset to the boot parameters?
Thanks for your continued help.

---

### Post by oldfred on 2013-10-11
Intel only has one set of drivers, but some of the newest chips seem to need settings. It may depend on which version you have on what works but users have reported these:

 Older Intel video card: i915.modeset=1 or i915.modeset=0 
newer:  i915.i915_enable_rc6=1

      
 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

Some of the new laptops needed this:

 Some other boot options
acpi_osi=Linux  acpi_backlight=vendor

Some with the very new Haswell processors have said that 13.10 which is still beta till later this monthm, works when the older versions did not. New systems often need the very newest version of Linux and supporting drivers and software.

---

