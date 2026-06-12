---
title: "Do you think my disk is dying?  (not related to load_cycle_count)"
date: 2007-11-17
forum: System76 Support
---

### Post by perce on 2007-11-17
A few times my computer refused to boot with the message: "insert proper boot medium in the drive and reboot". The problem always went away after a few tries, but not today, so I decided to reinstall. 

Ubuntu refused to install: the installer couldn't find /dev/sda1, so I installed Debian, which installed fine, but didn't configure my ethernet, and even worse it refused to load because of a grub error which I don't remember. At that point I reinstalled Ubuntu and it seems to work. My question is: was my filesystem corrupted in a srange way, or the disk is doing random things and will eventually fail?

---

### Post by ofb on 2007-11-17
I'm wondering if it's a loose cable.

Generally (_generally_) harddrive failure is preceded by data corruption and followed rather quickly with outright failure. You sometimes get some marvelous crunchy noises too.

The "insert proper boot medium in the drive and reboot" suggest the BIOS didn't find a bootable harddrive, so defaulted to a dialog asking for a bootable floppy or CD.

Which isn't narrowing it down a whole lot. After checking cables I guess my next suspicion would be the drive and I'd replace it to see if that helps.

It could be something more rare. Like say a capacitor has failed on the motherboard and affecting the IDE circuit. I'd definitely be looking for leaking and swollen caps when checking cables. I suppose it could be in the power supply too - if the hd isn't getting power it won't be bootable.

Inconsistent trouble like this is always a pain in the rump to track down.

---

### Post by perce on 2007-11-18
It happened again. I also had a bunch of disk errors from Grub before I could boot, Now that I've booted everything seems to work. I'm on a clean installation, so now I'm pretty convinced that it's a hardware problem.

Tom, tell me if you think I should send it back for repair.

---

### Post by greg_g on 2007-11-18
Perce, is this a desktop machine?  Which one?

---

### Post by perce on 2007-11-18
> **greg_g said:**
> Perce, is this a desktop machine?  Which one?

It's a laptop, Darter1

---

### Post by thomasaaron on 2007-11-19
It could be. Or it could be a hosed filesystem.

Back up your data. Then, after it happens again, email the output of: cat /var/log/messages

If it looks bad, I'll go ahead and arrange a cross-shipment for a new drive.

Best,
Tom

---

