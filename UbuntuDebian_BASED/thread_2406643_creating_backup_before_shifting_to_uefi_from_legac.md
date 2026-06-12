---
title: "creating backup before shifting to uefi from legacy boot mode"
date: 2018-11-23
forum: Ubuntu/Debian BASED
---

### Post by hackmonker on 2018-11-23
well recently i have dual booted windows and elementary os in my pc. everything was working fine untill i wanted to change my grub( with something like refind) . now i realized that i installed my windows as uefi and linux as legacy
so i thought of reinstalling linux through efi boot but doing so would cause me to lose all my data. is there any way i can backup all my data and the restore it after reinstalling, that includes all my apps and and themes? will using time shifts snapshots work after reinstalling? thanks

---

### Post by oldfred on 2018-11-23
Image backup probably will not work.
Most of your settings are in /home, only if server type apps installed may those be in / somewhere.
You can export a list of installed apps to make it easy to reimport list.
But all of above should be your normal backup, so when (not if) hard drive fails or system breaks, you can easily reinstall Ubuntu and restore your data.

Are both installed on one gpt drive? Or is Ubuntu on gpt partitioned drive?
Only if on MBR partitioned drive would you need to reinstall as UEFI really recommends gpt partitioning.
If Ubuntu on gpt partitioned drive, you just need to install the UEFI version of grub to convert. 

Post this:
sudo parted -l

---

