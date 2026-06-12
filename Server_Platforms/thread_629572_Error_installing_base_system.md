---
title: "Error installing base system?"
date: 2007-12-02
forum: Server Platforms
---

### Post by sportbikes on 2007-12-02
When tryiing to install either ubunto 7.10 or even 6.06 I receive an error message when it hits the install base system step of the install. The error message reads:

 "The installer cannot figure out how to install the base system. No installable CD-ROM was found and no valid mirror was configured."

The system boots up fine and obviously reads the cdrom since it starts the install from the bootable disk.  Am I missing something here?

Thanks!

---

### Post by koenn on 2007-12-02
are you installing from a live CD or using the alternate installer / server version / ....

The error suggests that you missed or misconfigured the 'configure apt sources' step, where you tell the installer where to get software packages from.

---

### Post by sportbikes on 2007-12-02
Both versions are .iso files I downloaded from ubuntu. I just burned them on disk and am trying to install.

---

### Post by Maxtorm on 2007-12-02
We had a bizarre issue like this a while ago an it turned out to be a faulty CD-ROM drive connection. The problem was fixed by reseating the CD-ROM connector on the motherboard. Bizarre, but true.

---

