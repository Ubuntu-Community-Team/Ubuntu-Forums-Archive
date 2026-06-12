---
title: "Kernel Error w/reboot: Dual Port 4G-FC cards, but only with kernel &gt;=3.18"
date: 2015-12-15
forum: Server Platforms
---

### Post by danielmayer on 2015-12-15
Hi,
I've a strange situation:
With kernels up to 3.16 no problem. I never tried 3.17. But 3.18, 3.19, 4.0, 4.1 and 4.2 all show the same problem:

When installing a dual port 4G-FC card, the system begins to boot but crashes before bash and automatically reboots.
When installing a single port 4G-FC card, everything is fine.

Hardware:
Dell T630, Bios: 1.3.6, SAS H730: Firmware 25.3.0.0016, Dell Broadcom 58710S, DP 10G-Base-T: 7.10.18
- so all newest firmwares are installed.

I tried with the following cards:
Emulex LPe11002, DP 4G: Error
Qlogic QLE 2462, DP 4G: Error
Emulex LPe1150, SP 4G: Fine
Qlogic QLE 2460, SP 4G: Fine
The Emulex are both on the same firmware level and newest, the Qlogics each on newest available.

With the DP cards I tried:
Ubuntu Server 14.04 LTS: error&reboot
Ubuntu Server 15.04: error&reboot; tried with kernels 4.0, 4.1 and 4.2.3
Ubuntu Server 15.10: error&reboot; tried with kernels 4.0, 4.1 and 4.2(.4, .5 and .6)
Ubuntu Desktop Mate Live-DVD 15.10: Successful!!
CentOS 7 (Dell-Live-CD), Kernel 3.10-xxx: Successful.
Ubuntu Server 16.04alpha, Kernel 4.4rc4: error&reboot

Dell Pro Support has no knowledge about such a problem with RedHat or SLES and thus told me to question Canonical & -users.
I have no idea what Ubuntu or Kernel-team have changed with kernel 3.17 or 3.18 that could affect a dual port FC card, but not a single port...

Some attachments to show error content, as far as I was able to fetch them before reboot with screenshots over IPMI.

(Edit) I forgot: production system is now Ubuntu Server 15.10 with Kernel 4.2.6 after rel-upgrade from 15.04. But most recent default kernel of 15.10 gives same problem.

Any help is greatly appreciated!
Thanks in advance,
Daniel

---

