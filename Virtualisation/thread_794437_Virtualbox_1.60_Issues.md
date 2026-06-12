---
title: "Virtualbox 1.60 Issues"
date: 2008-05-14
forum: Virtualisation
---

### Post by hamhock on 2008-05-14
I'm running Ubuntu 8.04 64-bit as host - I installed Mint 4.0 as guest with no problems.

I tried to install win2000 SP4 from CD and ISO, but froze at "Setup is starting Windows 2000." I set IRQDelay to 1 and 5 to no avail.

I also can’t get windows XP to run (existing install). I get a BSOD shortly after the winXP splash screen appears : Stop: 0x0000007B (0xF7C4D524, OXC0000034, 0X00000000, OX00000000). I ran mergeIDE (bat and reg merge) and changed all 6 of of my IDE controllers to “standard.” ACPI and IO APIC are enabled. Also toggled the two vbox controllers (PIIX3, 4).

Thanks.

---

### Post by tighem on 2008-05-14
I'm running XP no problems under 64-bit hardy. Is your XP 32 or 64 bit? Have you tried enabling VT extensions?

---

### Post by EXCiD3 on 2008-05-14
I am running Virtualbox 1.60 on 32bit Ubuntu and it works just fine. Try purging your installation of Virtualbox and reinstalling it.

---

### Post by hamhock on 2008-05-15
> **tighem said:**
> I'm running XP no problems under 64-bit hardy. Is your XP 32 or 64 bit? Have you tried enabling VT extensions?
XP is 32 bit.  VT - I've tried both on and off.

> **EXCiD3 said:**
> I am running Virtualbox 1.60 on 32bit Ubuntu and it works just fine. Try purging your installation of Virtualbox and reinstalling it.
I've done that as well.

---

### Post by EXCiD3 on 2008-05-15
Hmmm thats interesting. Can you install Ubuntu in virtualbox without problems? Maybe try installing from Virtualbox's website if the packages are different from the ones in the repositories. Thats pretty odd..

---

### Post by hamhock on 2008-05-15
> **EXCiD3 said:**
> Hmmm thats interesting. Can you install Ubuntu in virtualbox without problems? Maybe try installing from Virtualbox's website if the packages are different from the ones in the repositories. Thats pretty odd..

I installed Mint 4 in Virtualbox without problems.

I installed 1.6 by downloading the binary from virtualbox.org.

It's weird that I can't even install win2000 from ISO or CD.

---

### Post by tech404 on 2008-05-15
Have you uncommented these lines in /etc/init.d/mountdevsubfs.sh

#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

If you downloaded the 1.6 bin package from the website it is the non-open package(as far as I know). This version looks for /proc/bus/usb to make USB work. I understand that it can cause errors if you don uncomment these lines.

---

### Post by hamhock on 2008-05-15
> **tech404 said:**
> Have you uncommented these lines in /etc/init.d/mountdevsubfs.sh

#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

If you downloaded the 1.6 bin package from the website it is the non-open package(as far as I know). This version looks for /proc/bus/usb to make USB work. I understand that it can cause errors if you don uncomment these lines.

yes - did that.  followed this fine guide:
[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

USB was available in Vbox and I tried it both enabled and disabled.

---

### Post by jen1963 on 2008-05-15
I have XP Pro SP3 purrin in VB under Hardy. I blogged about it here:
[http://tuxwerx.com/Blogs/?p=21](http://tuxwerx.com/Blogs/?p=21)

I haven't tried Win 2K in VirtualBox yet. I'd have to slipstream the latest service pack in to 2K before I tried it though. I just slipstreamed SP 3 in to XP Pro. Since I have XP Pro to play with in a VM I haven't given ancient 2000 much thought.
I'll fart around with Win 2000 in VB to see if I can replicate your problem. 
As for those M$ stop codes you'd have to ask the M$ Toadies. I only keep M$ Crapware around in a VM to remind me of just how GOOD I have it with Linux...

---

### Post by hamhock on 2008-05-15
> **jen1963 said:**
> I have XP Pro SP3 purrin in VB under Hardy. I blogged about it here:
[http://tuxwerx.com/Blogs/?p=21](http://tuxwerx.com/Blogs/?p=21)

I haven't tried Win 2K in VirtualBox yet. I'd have to slipstream the latest service pack in to 2K before I tried it though. I just slipstreamed SP 3 in to XP Pro. Since I have XP Pro to play with in a VM I haven't given ancient 2000 much thought.
I'll fart around with Win 2000 in VB to see if I can replicate your problem. 
As for those M$ stop codes you'd have to ask the M$ Toadies. I only keep M$ Crapware around in a VM to remind me of just how GOOD I have it with Linux...

I slipstreamed SP4 into win2k and have installed from it so I know it is good.  I'm about to build a replacement computer and I assume I won't be able to use my winXP OEM disk.

---

### Post by laharrin on 2008-05-20
I am having the same problem, and have tried the solutions recommended above with no luck.

---

### Post by hamhock on 2008-05-20
> **laharrin said:**
> I am having the same problem, and have tried the solutions recommended above with no luck.

I finally got win2k to run (still not XP) by disabling IO APIC.

---

