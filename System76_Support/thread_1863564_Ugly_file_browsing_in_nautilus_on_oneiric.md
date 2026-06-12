---
title: "Ugly file browsing in nautilus on oneiric"
date: 2011-10-17
forum: System76 Support
---

### Post by chaselee on 2011-10-17
Sometimes after a new restart or boot up I need to run ```
nautilus -q
```, which fixes the issue.  Basically, if I don't do this, I'm left with a Windows 95-looking file browser and no file association icons.

---

### Post by chriscross93 on 2011-10-18
I have the same problem.

---

### Post by isantop on 2011-10-18
When you guys installed 11.10, did you do an Upgrade using the update manager, or did you use the CD/USB? If it's an upgrade, I'm guessing that's what's caused the problem.

---

### Post by Erszebet Lunah on 2011-10-20
Same problem for me, nautilus -q fixes it.
Upgraded through the update manager.

---

### Post by isantop on 2011-10-20
If you've upgraded through Update Manager, then most likely, this is caused by a botched upgrade, which are very common within the first week after an upgrade is released. You may want to go in and re-upgrade from a CD. This will fix your issues, as it serves as a clean installation.

---

### Post by chaselee on 2011-10-20
I upgraded using the CD; however, I started out using the upgrade manager, which failed, prompting me to use the CD.

---

### Post by unholy1 on 2011-10-21
Same problem here, after upgrading from 11.04 to 11.10 using the update manager. 

Restarting nautilus as suggsted fixes the problem while i'm logged in. But is this a permanent fix or will I need to run that command every restart? Is there a better long term solution? What exactly was "botched" during the upgrade?

---

### Post by isantop on 2011-10-21
It's very difficult to tell what got messed up.

My recomendation would be to try running these commands from a terminal:
```
sudo apt-get update
sudo apt-get remove --purge nautilus
sudo apt-get install ubuntu-desktop
```
This will purge the current nautilus installation from the systm, then reinstall it and any other components that were removed becuase of it.

---

### Post by freak42 on 2011-10-25
> **isantop said:**
> It's very difficult to tell what got messed up.

My recomendation would be to try running these commands from a terminal:
```
sudo apt-get update
sudo apt-get remove --purge nautilus
sudo apt-get install ubuntu-desktop
```
This will purge the current nautilus installation from the systm, then reinstall it and any other components that were removed becuase of it.

has anybody tried this, does it work?

I also read somewhere (sorry link went missing) that it is a problem with a QT environment variable. Does someone have any info about this?

TIA
Matthias

---

### Post by chaselee on 2011-10-25
@unholy1, it's a temporary fix.  what @isantop suggested would be permanent, but I haven't tried it yet to confirm it works.

---

### Post by mexlinux on 2011-10-25
I have the same problem, BUT I made clean install from USB.

---

### Post by isantop on 2011-10-26
I would check the integrity of your USB drive. Make sure the drive itself is in good condition, then check the file you downloaded to make sure it isn't corrupt. 

One thing you can try is booting the USB, then at the purpule screen with the white symbols at the bottom, press a key. This will allow you to select a language, then you can use "Check disk for defects" to make sure the disk is good.

---

