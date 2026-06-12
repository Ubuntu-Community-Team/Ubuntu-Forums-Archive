---
title: "[SOLVED] VirtualBox - no files in Guest Additions"
date: 2008-05-23
forum: Virtualisation
---

### Post by BobLand on 2008-05-23
I downloaded Guest Additions and mounted the iso to the cdrom.  However, there is nothing in the cdrom.  I tried this a few times with the same results.  

Host: Gutsy - up-to-date
Guest: Kubuntu 8.04 w KDE4

Suggestions?

bobland

---

### Post by quonsar on 2008-05-23
> **BobLand said:**
> I downloaded Guest Additions and mounted the iso to the cdrom.  However, there is nothing in the cdrom.  I tried this a few times with the same results.  

Host: Gutsy - up-to-date
Guest: Kubuntu 8.04 w KDE4

Suggestions?

bobland

if you had virtualbox installed you should find the guest additions in /usr/share/virtualbox/VBoxGuestAdditions.iso

---

### Post by maybeway36 on 2008-05-23
Try mounting the CDROM within the guest. Pressing Alt+F2 and typing
```
mount /dev/cdrom
```
should do it.

---

### Post by BobLand on 2008-05-23
In the VirturalBox OSE, is shows the cdrom "loaded" with VBoxGuestAdditions.  However, when accessing the cdrom, the drive is empty, which means, I cannot run any scrips or programs that initiate this application.

If I select mount cdrom from devices, I can select the guest additions iso.  I have a /media/cdrom but it is always empty, regardless of listing or user (sudo ls -la = zip).

bobland

---

### Post by BobLand on 2008-05-23
Fixed. I removed the 1.5 version and installed the 1.6.  BIG difference!  Got everything to work.  Found out that I don't like kubuntu so getting VirtualBox up and running is a good thing.

Installed XP with no problems other than installing XP.  That has got to be the dumbest installation routine on the planet.

Thanks for the help.
bobland

---

