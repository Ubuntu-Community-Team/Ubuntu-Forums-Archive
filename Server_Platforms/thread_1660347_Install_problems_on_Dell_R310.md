---
title: "Install problems on Dell R310"
date: 2011-01-05
forum: Server Platforms
---

### Post by truant on 2011-01-05
I've been mostly using Debian Squeeze, but am hitting the same problems when I try Ubuntu 10.04 as well, so am posting here in case anyone has seen the same issues.  Here's what's up:

Intel Xeon X3440 quad core, 8GB RAM, etc. Storage is four 500GB drives, hardware RAID1 so shows up as two 500GB drives to the system. H/W controller is SAS1068e, Broadcom NIC, everything else is Intel chips. No DRAC.

I want RAID10, so am doing s/w RAID0 during install using both h/w R1 arrays. I have a non-raid /boot partition. All f/s are ext3.

No matter what combination of LVM, s/w RAID, no s/w RAID, no LVM, even just a single raidless partition or whatever I use, GRUB refuses to boot the installed system. Sometimes I get a "GRUB" prompt, but most of the time nothing at all past POST. No error messages are generated during the install process. If I boot rescue mode from the CD and try to manually install grub it sometimes works, sometimes fails with an assortment of errors, the googling of which gets me roughly nowhere. Even if grub reports that it's installed, on reboot it fails as above.

I've tried pinning grub to 'experimental' (or 'maverick' depending on OS at the time), I've tried downgrading to grub-legacy, I've added a rootdelay to let the RAID spin up, I've even tried lilo! No joy. One plus point is that I know a lot more about grub now than I did last month :)

I did find a few mentions of older versions of grub having a few bugs which relate to not booting off s/w RAID devices, but those bugs have been fixed a while ago as far as I can tell. But even if that were the problem, installing with no RAID/LVM should work - which it doesn't.

The most recent install attempt I've made had an empty /boot directory (despite /vmlinuz.* etc symlinking into there), despite the installer reporting no problems. I had to install a previous kernel version before I got System.map, config*, vmlinuz* etc in there, and manually running grub-update, grub-install, created right-looking device.map, menu.lst and so on. Now everything *looks* right, it just doesn't *work*

Centos installs fine. But I don't know rpm-based distros well enough to do what I need to do down the line, and anyway - this is Debi/buntu for goodness sakes!

Any help/pointers etc would be most gratefully received.

---

### Post by truant on 2011-01-05
Just tried 10.10 (rather than previous attempts with 10.04)

Same problem.  Installs OK, but then won't boot.

---

### Post by mrcase on 2011-03-16
HI! Did you solve your issue?
I´m thinking of buying the same server with a H200A controller doing Raid1.

best regards

---

### Post by truant on 2011-03-16
I "solved" the problem by buying a new RAID controller.  On the plus side, this does mean I'm doing RAID10 entirely in hardware, which is nice.

Whether you'll see problems with a controller other than the SAS1068e, I can't really say.

---

### Post by FiVAL on 2011-03-17
> **mrcase said:**
> HI! Did you solve your issue?
I´m thinking of buying the same server with a H200A controller doing Raid1.

best regards

I will recieve our R310's with the H200A controller next week...

[-o<

---

### Post by FiVAL on 2011-03-23
The R310's with the Parc H200A controller (2x 2TB SATA HDD's in mirror)
AND Ubuntu Server 10.04.2 LTS 64bit ARE working PERFECT!!!!

---

### Post by jvhaarst on 2011-11-22
After the message "Gave up waiting for boot device", you could type "exit" , and Ubuntu will continue to boot normally.
A fix might be found here : [http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html) , especially the part about rootdelay.

---

