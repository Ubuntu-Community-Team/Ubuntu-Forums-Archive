---
title: "Crappy USB 3.0 support"
date: 2013-03-30
forum: Server Platforms
---

### Post by szafran on 2013-03-30
Hi,

I'm getting pretty irritated off with linux and it's USB3.0 support (or maybe it's just Ubuntu ?).
I have a Gigabyte Gigabyte GA-890GPA-UD3H (rev 2.1) with integrated USB3.0:
```
szafran@NAS:/var/log$ lspci | grep -i nec
03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
```

And since about 1,5 years (that's how long I have my MoBo) NOTHING has changed, and from what I've read NEC chips should run fine since linux support for USB3.0 was based on them.
Now... 1,5 years later I'm in exactly the same spot - my HDD in external USB3.0 enclosure (I've tried about 10 different enclosures) works like a charm when it's connected to the USB 3.0 controller while the OS is up and running. The things change when I try to boot with the drive connected:
```
[    5.956736] usb 9-1: Device not responding to set address.
[    6.160358] usb 9-1: Device not responding to set address.
[    6.363895] usb 9-1: device not accepting address 2, error -71
[    7.661586] usb 9-1: Device not responding to set address.
[    7.865197] usb 9-1: Device not responding to set address.
[    8.068760] usb 9-1: device not accepting address 3, error -71
[    9.366443] usb 9-1: Device not responding to set address.
[    9.570049] usb 9-1: Device not responding to set address.
[    9.773594] usb 9-1: device not accepting address 4, error -71
[   11.071286] usb 9-1: Device not responding to set address.
[   11.274894] usb 9-1: Device not responding to set address.
[   11.478403] usb 9-1: device not accepting address 5, error -71
[   11.478449] hub 9-0:1.0: unable to enumerate USB device on port 1

```

The drive works fine on USB2.0 (doesn't matter when I connect it).

I've updated my 12.04 server kernel to 3.5.0-27-generic #46~precise1-Ubuntu and that didn't help either.
Does anyone have a fix/patch that will make it work on boot ?

---

### Post by The Spectre on 2013-03-30
You might need to Flash the Firmware for the NEC USB 3.0 Controller...

[http://askubuntu.com/questions/161862/nec-upd720200-usb-3-0-not-working-on-ubuntu-12-04](http://askubuntu.com/questions/161862/nec-upd720200-usb-3-0-not-working-on-ubuntu-12-04)

---

### Post by szafran on 2013-04-03
Done that allready some time ago, right after some kernel update the USB3.0 ports stopped working (used exactly the same post you linked to).
Anyways my USB3.0 ports work fine (and at full speed), after bootup, but not during.

---

### Post by The Spectre on 2013-04-11
You indicated that you tried different Enclosures but did you also try different USB 3.0 Cables?

---

### Post by szafran on 2013-04-12
Yep, each enclosure had it's own cable (but if the cable was faulty the enclosures wouldn't work properly after bootup completes)

---

### Post by kurt18947 on 2013-04-12
I suspect the reason is that the USB 3 chipset requires a driver loaded during boot to run at USB 3 speeds.  I have a PCI card that adds PS2 ports.  It is seen as a USB device and the PS2 ports don't work until the O.S. is loaded.  Perhaps the O.P. has a similar situation.

---

### Post by szafran on 2013-04-12
That's what I think too.
But the main problem is that the machine stops booting, because it says that it can't mount the drive, and I mount it using:
UUID=e8038119-3654-4fd3-992d-7e5789767395       /home/szafran/Backup            ext4    user,exec,noatime,nofail,errors=continue                0       0
from what I know the 'nofail' should prevent that, but it doesn't.
I'd have no problems if it mounted later, but the machine is headless and kinda remote, and a lot of times that I reboot it (eg. after updates etc.) I'm not on site to connect a keyboard and press 'S' to skip the mounting error.

I've bought an expansion card with 4x USB 3.0 ports that's using NEC [COLOR=#000000][FONT=Tahoma]D720201, but I'm waiting for some cables to power to it. Maybe it'll work, but still I'd like to connect more things to my USB 3.0 ports, and if they are not available during boot then I think more errors will come.[/FONT][/COLOR]

---

### Post by CharlesA on 2013-04-12
Use nobootwait instead of nofail.

[http://unix.stackexchange.com/questions/53456/what-is-the-difference-between-nobootwait-and-nofail-in-fstab](http://unix.stackexchange.com/questions/53456/what-is-the-difference-between-nobootwait-and-nofail-in-fstab)

---

### Post by szafran on 2013-04-13
Thanks, I'll check that on next reboot.
But still - is there any way to make the drivers for the controller to be up earlier ?

---

### Post by szafran on 2013-04-14
nobootwait helped for the bootup error, but the drive still isn't mounted properly - I have to replug it to the controller to make it work.

My whole dmesg is attached - maybe someone will find something in there.

---

### Post by szafran on 2013-04-29
Nothing works. I've even tried installing Windows on that machine to check - on Windows everything is fine.
So the reason is still crappy linux USB 3.0 support. Both controllers behave exactly the same.

---

### Post by CharlesA on 2013-04-29
USB3 works fine for me, but I am running a different controller than you are.
```
05:00.0 USB controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)

```

With that said, I was running a "cheap" BestBuy USB 3 card before and it was running fine as well. *shrugs*

Have you filed a bug report?

---

### Post by szafran on 2013-04-29
03:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
04:00.0 USB controller: Renesas Technology Corp. Device 0014 (rev 03)

Those are mine. Both on different chips from NEC. Both working fine until reboot. After reboot none of the connected device work until physically replugged (disconnected/connected by hand), which is unacceptable on a basic PC, not to mention on my NAS server (which this topic is all about). And this didn't happen when I runned the hardware on Windows on the whole last weekend, and done reboots/shutdowns on it many many times.
From this I can only speculate that USB3.0 device are not corrently handled on system shutdown (don't really know how it's done - but "me thinks" that they are not properly closed/released or whatever it's called)

No I didn't fill a bug report, because from I remember it involves installing a bunch of additional stuff, which I really don't want.

---

### Post by CharlesA on 2013-04-29
I'm still running the 3.2 kernel on 12.04, but did you do any updates before the reboot broke things?

---

### Post by szafran on 2013-04-29
This is happening for over 1,5 years now, since I've bought the hardware on all kernel version on the way. So it never did work properly on linux.

---

### Post by CharlesA on 2013-04-29
Best thing to do would be to report it as a bug, especially if it hasn't worked at all on Linux. It could be the chipset that is the issue or something else, but my bet is on the chipset.

Check this page out:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by szafran on 2013-04-29
I've bought my NAS's MoBo mainly because I've read that most of the linux's USB3.0 support was developed on the NEC[COLOR=#000000] [/COLOR]720200 chip (mainly because it was one of the first stable USB3.0 chips).

And yes I know that there's a page on creating bug reports etc. I just don't want nor need a launchpad account (this is where my reading of the page always ends - to report a bug I MUST create an account, sorry but no ;) )

---

### Post by CharlesA on 2013-04-29
I found this, but I don't know if it will be of any help as you said you already updated the firmware of the USB card.
[http://askubuntu.com/questions/161862/nec-upd720200-usb-3-0-not-working-on-ubuntu-12-04](http://askubuntu.com/questions/161862/nec-upd720200-usb-3-0-not-working-on-ubuntu-12-04)
[http://askubuntu.com/questions/187784/nec-usb-3-0-controller-drops-connection-ubuntu-12-04-1/227942#227942](http://askubuntu.com/questions/187784/nec-usb-3-0-controller-drops-connection-ubuntu-12-04-1/227942#227942)

---

### Post by szafran on 2013-04-29
Unfortunatelly they do not apply.
First one I've used some time ago to update the firmware of the MoBo's integrated chip.
Second one doesn't apply because occupying all ports doesn't change anything.

---

### Post by JohnH on 2013-05-06
I can confirm this same problem with my USB3 on a gigabyte board running 13.04. I suspect it is a kernel problem though. I say this because I noticed after a kernel upgrade (during the 12.10 cycle) it booted perfectly. But then there was another kernel upgrade and it stuffed it again. 

I can get it to run by unplugging and then plugging in the USB3 device.

---

