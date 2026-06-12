---
title: "Can't figure out how to disconnect internal hard drive"
date: 2011-10-16
forum: Server Platforms
---

### Post by TBhX£2760R8@nK7§r on 2011-10-16
I've been searching for a while for a way to disconnect an internal hard drive, and have the server still boot. I've dismounted it, and the directory I mounted it from is no empty. But whenever I remove the hard drive and try to boot, the bios takes forever on "Verifying DMI Pool data...", and then gets to an error on no boot drive. Google didn't really help, the only thing I found was for some weird distribution of linux, and the instructions didn't work on ubuntu.

I'm terribly sorry if I've just been using the wrong search terms("remove hard drive linux") and this is easily findable.

Scuzz

---

### Post by oldfred on 2011-10-16
BIOS jumps to first bootable device you have specified then it goes down the line of others in the list.

If you have no hard drive what are you booting? Did you set CD or floppy as first device?

---

### Post by TBhX£2760R8@nK7§r on 2011-10-16
I think it goes USB, CD, HD. THe CD drive is unplugged, and there is no USb storage on. I'll try putting the HD first.

Nope, still doesn't' work.

---

### Post by trundlenut on 2011-10-16
are you getting as far as the grub menu?  If not I would suspect that grub is installed on the driver you disconnected.

---

### Post by TBhX£2760R8@nK7§r on 2011-10-16
I tried disconnecting the the hard drive that *should* have the OS on it, and the same thing happens.

---

### Post by Leaf on 2011-10-16
The DMI pool is a check your BIOS uses against hardware changes. 
Go to bios, check your hard drive info, set it to autodetect or disable, save your settings, and reboot, see if that helps.

---

### Post by TBhX£2760R8@nK7§r on 2011-10-16
I'm not really sure what you mean, and poking around the bios, I didn't see anything related to hard drive info.
ON every boot, the bios lists the hard drives it finds, so I know that it's seeing the right hard drives.

---

