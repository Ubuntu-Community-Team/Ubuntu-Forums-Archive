---
title: "Any risk of autoruns in flash drives and other external media?"
date: 2010-11-09
forum: Security
---

### Post by castro1 on 2010-11-09
Hi.  I had to copy some files from a flash drive I received from a Windows user. I plugged it in the USB port and scanned it for viruses using ClamTk. It found two viruses (backdoors in files called desKTop.ini) in some hidden folders (disguised as recycle bin, but named CrAzY and Hott) in it.  I copied the files I wanted, which were simple PDFs and had nothing to do with those files. I ejected the flash drive.  My question is: Ubuntu automatically detects new media. Does it execute Autoruns from such media, as Windows does? In this specific case: could anything have been executed in the aforementioned operation--and when I plug flash drives and hard drives in the USB in general--without me noticing it?  I am also supposing that viruses that act by changing registries have no effect in Ubuntu, and that any malware would not be able to install itself or do nasty stuff without my inputing my password first, correct?  Thank you, and sorry if the question is too obvious--I am very new to Linux.

---

### Post by OpSecShellshock on 2010-11-09
This is all pretty much correct. While the drive will be mounted as soon as it's plugged in, any kind of "autorun" functionality is Windows-only, as is any malware that's likely to be hidden on it. What autorun does is set something on the drive up to execute instantly when the drive is connected to a Windows machine. On Ubuntu, even though the drive will mount, nothing will be run without the user doing so as a separate action.

---

### Post by MechaMechanism on 2010-11-09
> **OpSecShellshock said:**
> This is all pretty much correct. While the drive will be mounted as soon as it's plugged in, any kind of "autorun" functionality is Windows-only, as is any malware that's likely to be hidden on it. What autorun does is set something on the drive up to execute instantly when the drive is connected to a Windows machine. On Ubuntu, even though the drive will mount, nothing will be run without the user doing so as a separate action.
Ubuntu most certainly does have autorun.  CDs and DVDs are autorun by default.  If they contain bad or evil files they can either crash or lockup or gain root.  In Nautilus go to the menu edit/preferences then to the media tab.  Quite trivial to autolaunch software in Ubuntu from external devices.  Autoruns happen for cameras as well.

---

### Post by castro1 on 2010-11-10
Indeed, CDs are executed automatically, if you don't configure Nautilus to behave otherwise.

What about flash drives, as default? I have experienced no popups whatsoever when I inserted it, and there was no files other than the PDFs in the root of the flash drive (show hidden folders was on). Also, Autorun seems to be a Windows thing, under the form of Autorun.inf: [http://en.wikipedia.org/wiki/Autorun#Issues_and_security](http://en.wikipedia.org/wiki/Autorun#Issues_and_security) 

Under these particular circumstances, am I correct to conclude no risk at all was imposed? I add that I was not in root mode.

Thanks again.

---

### Post by uRock on 2010-11-10
It has been my experience that autoruns cannot gain root. 

 Example; Install ubuntu in a vbox, then when you mount the guest additions ISO it will offer to run the autorun, before actually doing it, then once it starts it will ask for a password.

---

