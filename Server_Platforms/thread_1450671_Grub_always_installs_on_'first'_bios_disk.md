---
title: "Grub always installs on 'first' bios disk?"
date: 2010-04-09
forum: Server Platforms
---

### Post by flyboysr71 on 2010-04-09
Interesting issue, didn't cause me any harm, but only by chance.  I was installing Ubuntu 9.04 64bit server from the CD on a machine that I normally run ESXi on.  I wanted to test disk speed on a direct install vs. the install in ESXi, so I installed a 4th hard disk, shutdown ESXi, and installed Ubuntu directly on the new disk (4th Bios disk - SCSI:3 or sdd).  When I tried to boot from this disk, nothing happened.  I rebooted from the ESXi install disk (SCSI:2 or sdc), all was fine.  Playing around, I finally found that to boot the ubuntu install, i had to boot from SCSI:0 - Grub had installed there, even though I never indicated that disk for anything during the install.  It would be much better if Grub ASKED where it should be install, rather than assuming.

---

### Post by Bachstelze on 2010-04-09
Did you use the Desktop CD to install Ubuntu?

---

### Post by volkswagner on 2010-04-09
Yeah it is the default.  I think you have to choose expert mode when booting the server CD to choose the Grub install location.  I believe there is a warning, but again not sure unless you choose expert install.

---

### Post by oldfred on 2010-04-09
Just as you finalize the partitioning during the install is an advanced button. That lets you choose which drive to install grub.

---

