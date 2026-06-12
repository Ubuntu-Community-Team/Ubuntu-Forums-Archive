---
title: "Ubuntu upgrade showstopper: what is with the Ubuntu 10.04 text console?"
date: 2010-05-17
forum: Server Platforms
---

### Post by Saint Dogbert on 2010-05-17
Can Ubuntu Server 10.04 on Intel x64 be set for, and hold a standard 80x25 text mode on the console?

Beginning to think I need to stay away from upgrading to Ubuntu 10.04 and changing my preferred distro.

Having two separate show-stopping problems with Ubuntu Server  10.04. Think both are related:

1) Running Ubuntu Server under Windows 2008R2 Hyper-V performance is screaming fast until right before the login prompt when the “video/text” mode changes and then until its rebooted it’s like running telnet through a 300 baud modem.

2) On native servers the IMPI card stops working at the exact same place that Hyper-V gets slow. BIOS post to right before login is screaming fast, then the video change and then no IMPI. Have to have IMPI access at all times; no SSH is not acceptable as IMPI is full out-of-band management including BIOS and remote disk mounts, SSH only works after the system is fully booted.

etc/default/grub is set to:
grub_terminal=console
grub_cmdline_linux_default=”verbose  text”
update-grub has been run many times.

Is this GFX quasi-text mode the only default for the console in 10.04? If so its time to switch distros.

Thanks!

---

### Post by BradClarke on 2010-05-20
The new "text mode" is killing me too. I'm trying to put 10.04 on a PowerEdge 1950 and I can't see part of the screen through the DRAC. 

Lets hope for a quick 10.04.1

---

### Post by andydread on 2010-07-24
I just noticed this with KVM.  I KVM installed and two VMs one guest is 8.04 and another guest is 10.04  The 10.04 guest console is as slooooow as telnet thru a 300 baud modem.  (remember those days:) ) The 8.04 guest display simply flies.  I guess when one has to meet a release schedule one doesn't bother to test these things before releasing.  This must be why such obvious things slip through.  I can't imagine Red Hat or Mandrake releasing something with such obvious blatant show stoppers such as broken intel graphics, boot services failing to start and now slow console that takes one back to the days of BBSes and dialup.

Is there a way to have a standard console instead like in 8.04?

---

### Post by CharlesA on 2010-07-24
Same thing happens if you try to run it in VirtualBox, the terminal crawls.

Unfornatuely I have no idea how you can change that behavior, but I have a feeling that it's something to do with it trying to pick the native resolution of the display.

I have a feeling you need to edit grub, but I have no idea what to change.

---

### Post by Bachstelze on 2010-07-24
Blacklist fbcon and vga16fb.

---

### Post by CharlesA on 2010-07-24
> **Bachstelze said:**
> Blacklist fbcon and vga16fb.

Thank you so much! That works wonders. :)

---

