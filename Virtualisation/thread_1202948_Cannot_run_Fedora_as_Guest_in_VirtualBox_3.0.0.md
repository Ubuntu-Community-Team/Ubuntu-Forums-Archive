---
title: "Cannot run Fedora as Guest in VirtualBox 3.0.0"
date: 2009-07-02
forum: Virtualisation
---

### Post by Vignesh S on 2009-07-02
I tried to install Fedora 11 by both the DVD disc and the original ISO file, but I can't seem to install it either way. After some start up thing which is text based, it came up with this:

weird, boot CPU (#0) not listed by the bios
SMP motherboard not detected
SMP disabled

After which nothing happens. Might be related to the fact that the computer that this is on was made in 2001, and support for such things might have not been made at that time. But is there a way to get this thing to say what the boot up CPU is?

Oh and by the way, what does SMP mean?

And on the first menu that came up, I clicked on Install or upgrade an existing system, or the initial option that is highlighted

---

### Post by jens_chaox on 2009-07-03
Hey there, just wanted to mention that I had the same issue with  Arch Linux. As a workaround try deactivating ACPI in the Virtual Machine's settings.

---

### Post by Vignesh S on 2009-07-11
Yep that worked. Thanks. But for some reason, when I come to the partitioning stage of the installation, even though it sees the VirtualBox partition set aside for it, it doesn't let me click on it, and when I try to advance to the next stage of the installation, it says "must select a drive to use as the bootable device". Maybe it might be the the fact that it doesn't like the virtually expanding drive. Maybe I should try the fixed drive.

UPDATE: It worked with the fixed drive (and when I clicked on enable IO APIC and disabled APIC) but now there is yet another problem

---

### Post by Vignesh S on 2009-07-12
Will Fedora cease giving me a hard time? Now when I restart it, it comes up with the last stages of the setup. But I can't finish it because the keyboard and mouse aren't working in the guest OS! I have no idea what the problem is, and I tried putting the keyboard and mouse in the USB filters, but that caused me even more problems. So I have no idea what to do now. Any help would be appreciated.

---

### Post by Vignesh S on 2009-07-14
<bump>

---

### Post by Vignesh S on 2009-07-23
<bump>

---

### Post by bodhi.zazen on 2009-07-23
I would suggest you start by upgrading virtual box. VBox is now on 3.0.2 and , IMO, 3.0.0 and 3.0.1 were a tad buggy (and thus the fast updates).

I do not know if that will fix your issue or not, but I hope so.

---

### Post by Vignesh S on 2009-08-08
Decided to move to VMware. A tonne more stable.

However, I might not stick to the concept of virtual machines because if the host stuffs up (like it has done just now [http://ubuntuforums.org/showthread.php?t=1234528](http://ubuntuforums.org/showthread.php?t=1234528)), then I can't even use the computer, let alone the guest OS. But I'll sort that mess out after I fix my computer up.

---

### Post by mywave on 2010-01-13
> **Vignesh S said:**
> Will Fedora cease giving me a hard time? Now when I restart it, it comes up with the last stages of the setup. But I can't finish it because the keyboard and mouse aren't working in the guest OS! I have no idea what the problem is, and I tried putting the keyboard and mouse in the USB filters, but that caused me even more problems. So I have no idea what to do now. Any help would be appreciated.

I have the same issue with Fedora 12 aswell using qemu (virtualbox shares code with qemu). 

I first had issues booting at all.. it stuck with 100% forever after it started X, but found that related to the guest only having default amount of memory availble: 128MB

I might try deactivating ACPI and stuff like that tonight when I retry

Stian

---

