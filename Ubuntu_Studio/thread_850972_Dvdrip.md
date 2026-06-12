---
title: "Dvd::rip"
date: 2008-07-06
forum: Ubuntu Studio
---

### Post by accodata on 2008-07-06
Hi, I need some advice please! I am running, gutsy 7.10. I have installed dvd::rip, and in the preferences, it tells me that a "rar" file is missing.
I have gone into synaptic package manager, and installed it. But dvd::rip still will not work.

Anyone, know what I am doing wrong.

Thanks for reading and be safe

---

### Post by happymellon on 2008-07-06
> **accodata said:**
> Hi, I need some advice please! I am running, gutsy 7.10. I have installed dvd::rip, and in the preferences, it tells me that a "rar" file is missing.
I have gone into synaptic package manager, and installed it. But dvd::rip still will not work.

Anyone, know what I am doing wrong.

Thanks for reading and be safe

The RAR dependency can normally be fixed by going to add/remove and selecting RAR, or going to the command line and typing in "sudo apt-get install rar". Hit "Check all settings" and it should turn in to:

rar command (for vobsub compression): /usr/bin/rar executable : Ok

If not, what does it say?

---

