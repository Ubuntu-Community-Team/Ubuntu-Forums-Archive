---
title: "Cannot boot snappy on VirtualBox on Trusty"
date: 2015-04-16
forum: Virtualisation
---

### Post by miragemonger on 2015-04-16
I downloaded the .ova for snappy and when I import it into VirtualBox and start it up, I get to the message 

systemd[1]: Failed to start Load/Save Random Seed.
piix4_smbus 0000:00:07.0: SMBus base address uninitialized - upgrade BIOS or use force_addr=0xaddr

and the image stops booting. I'd like some help to figure out where I can look next to get to the root cause for this failure to boot the image. 

The VirtualBox "Show Log" doesn't show any errors that jump out at me but is attached for reference. 

Thanks in advance!

---

### Post by miragemonger on 2015-05-15
So I have been messing around with this a little more and tried to boot the .ova on a Windows 7 machine that has virtualbox on it - no luck. Stops booting at the exact same point. At this point I'm wondering if anyone has had any luck importing the standard snappy .ova image into Virtualbox and getting it to load?

---

### Post by miragemonger on 2015-05-15
Upgraded the version of VirtualBox and that seems to have fixed the issue.

---

