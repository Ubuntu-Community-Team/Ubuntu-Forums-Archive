---
title: "Installing Elementary OS corrupted the BIOS."
date: 2018-11-12
forum: Ubuntu/Debian BASED
---

### Post by automate-stuff on 2018-11-12
After installing Elementary OS JUNO, I can no longer save changes in the BIOS...

The voltmeter shows that the CMOS battery has a voltage of 3.05 ... so it can't be the CMOS battery...

My guess is that eOS has corrupted the BIOS...Any way to fix this  ?

---

### Post by Frogs Hair on 2018-11-12
Moved to Ubuntu/Debian Based.

---

### Post by yancek on 2018-11-13
That would be very surprising as a Linux installer will generally just write data to the drive(s).
What hardware (computer manufacturer) do you have?  Options vary with manufacturer.
How old is it?
From what you have posted, you have installed Elementary as the only OS on the computer, correct?
What change(s) are you trying to make.

---

### Post by automate-stuff on 2018-11-15
Dell 3179 ... 2017 Model....Only elementary OS installed...I also did apt update/upgrade after install...

---

### Post by oldfred on 2018-11-15
Have you updated UEFI from Dell for your system? 
Almost all systems need that, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.

---

### Post by kc1di on 2018-11-15
It would be highly unlikely that the installer could change the bios on that machine.

---

### Post by QIII on 2018-11-15
It is not unheard of for installation to modify the BIOS in a deleterious manner.  The original version of Ubuntu 17.10 did contain a kernel bug that changed the BIOS of a number of machines, making it impossible for users to make changes to their settings.  See [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1734147") on Launchpad.

However, I think that Juno is based on 18.04, so that probably does not apply.

---

### Post by automate-stuff on 2018-11-15
At first I tried to install in UEFI mode but I got the grub error...so I changed it to legacy mode(Here the changes were saved somehow) and the install went smooth...then the problem occurred...I tried everything to fix it, flashed the BIOS to different versions, used a voltmeter to measure the CMOS battery voltage and it showed 3.05v, Flashed the CMOS by detaching the battery and the CMOS battery...loading the default settings in the BIOS menu....No Luck

---

