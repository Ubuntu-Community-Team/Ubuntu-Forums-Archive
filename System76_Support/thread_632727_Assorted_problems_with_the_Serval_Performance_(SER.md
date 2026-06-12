---
title: "Assorted problems with the Serval Performance (SERP3)"
date: 2007-12-05
forum: System76 Support
---

### Post by Rasputin_III on 2007-12-05
I recently purchased a new Serval Performance laptop (just over a week ago, in fact) and have ran into a few problems...

Most of these I'm keeping an eye on myself, as they are distribution/kernel/driver related and not something the support folks can do much with:

With a Gutsy AMD64 installation, there is the incorrect splash screen graphics mode--
**[https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930](https://bugs.launchpad.net/ubuntu/gutsy/+source/ubiquity/+bug/150930)**
and the wireless failing to pass traffic over wpa2 (and possibly other) networks--
**[https://bugs.launchpad.net/ubuntu/+bug/159981](https://bugs.launchpad.net/ubuntu/+bug/159981)**

With a Gutsy X86 installation, there is an Intel wireless connection loss bug--
**([https://bugs.launchpad.net/ubuntu/gutsy/+source/linux-ubuntu-modules-2.6.22/+bug/139080](https://bugs.launchpad.net/ubuntu/gutsy/+source/linux-ubuntu-modules-2.6.22/+bug/139080))**
and the hitachi NCQ--
**([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/137470](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/137470))**

I am, however,  concerned about an error similar to the NCQ one that happened while burning a DVD (via command line), causing it to fail:

[    6.100000] ata4: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118a0 irq 14
[    6.444000] ata4.00: ATAPI: SlimtypeDVD A  DS8A1P, CX12, max UDMA/33
[    6.632000] ata4.00: configured for UDMA/33
[ 3637.820000] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3637.820000] ata4.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x2a data 32768 out
[ 3642.864000] ata4: port is slow to respond, please be patient (Status 0xd0)
[ 3647.848000] ata4: device not ready (errno=-16), forcing hardreset
[ 3647.848000] ata4: soft resetting port
[ 3648.360000] ata4.00: configured for UDMA/33
[ 3648.360000] ata4: EH complete

Obviously the first three lines were close to boot-up and dealt with the identification/configuration of the hardware.

Do you think this is indicative of some kind of hardware problem?

---

### Post by thomasaaron on 2007-12-06
I've seen that error sequence in the past. It had to do with a firmware problem in the CD drive that caused intermittent freezing. However, that sequence didn't have the emask error, which I've primarily seen with bad blocks.

I'd keep an eye on it and keep your data backed up. If it only happens while burning a cd from the command line, I'd not worry too much about it, as it could be software related(?). Do you get it when burning via something like nautilus?

Best,
T

---

### Post by Rasputin_III on 2007-12-06
I'll keep an eye on it and post any additional information next time I burn a "normal" dvd...  (The double layers are a bit too expensive to make repeated coasters).

Don't most of the gui burning tools simply act as front ends for growisofs?

Thanks again.

---

