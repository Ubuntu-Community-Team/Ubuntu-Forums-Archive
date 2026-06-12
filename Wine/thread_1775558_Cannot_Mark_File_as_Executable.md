---
title: "Cannot Mark File as Executable"
date: 2011-06-04
forum: Wine
---

### Post by BanannaButt on 2011-06-04
Whenever I try to run a .EXE file on my separate hard drive, I get the following message: ```
The file '/media/0810B0E010B0D5C2/Users/Sean/Downloads/uTorrent/Completed Downloads/Crysis_2_v1.8-FAiRLiGHT/Crysis_2_final_1.8n_Patch.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
```
And when I try to mark the file as executable, the check box unchecks itself.  I'm not sure if it has something to do with the permissions, but it's set to the user name I use in Windows.  Any idea how to fix this?  Running Wine 1.2.2.

Thanks.

---

### Post by matt_symes on 2011-06-04
Hi

Is the drive formatted as NTFS or FAT32 ? If it is then that is your problem.

Kind regards

---

### Post by lightstream on 2011-06-04
you've probably got your other hard disk mounted read-only.

you might need to change this in /etc/fstab

---

### Post by BanannaButt on 2011-06-04
> **matt_symes said:**
> Hi

Is the drive formatted as NTFS or FAT32 ? If it is then that is your problem.

Kind regards
The drive is formatted to NTFS.

---

### Post by BanannaButt on 2011-06-04
> **lightstream said:**
> you've probably got your other hard disk mounted read-only.

you might need to change this in /etc/fstab
I'm a fairly new user to Ubuntu.  Can you describe this process?

---

### Post by lightstream on 2011-06-04
what I said doesn't apply if it's NTFS. That file system doesn't use executable bits.

Either copy the folder to your linux drive (e.g. put it under ~/.wine/drive_c) where you can set the executable bit, and/or navigate to the folder in the terminal and then run **wine proggie.exe** from the terminal.

---

### Post by mc4man on 2011-06-04
vfat (FAT32), volumes will allow .exe's to be run as you've tried, ntfs will not.
Try just using wine instead of the default 'Wine Windows Program Loader'
Either a one time - r. click on any .exe > open with - other application > use a custom command. For command just use 
wine
Then  use wine on r. click on any .exe or set as the new left click default thru r. click > properties > open with on any .exe
or in your Ex.
```
wine '/media/0810B0E010B0D5C2/Users/Sean/Downloads/uTorrent/Completed Downloads/Crysis_2_v1.8-FAiRLiGHT/Crysis_2_final_1.8n_Patch.exe'

```

---

### Post by matt_symes on 2011-06-04
Hi

You have two options. You can either move the file onto an extX partition and set the executable bit when it is copied or you can change the umask value in fstab to 022.

EDIT:

> vfat (FAT32), volumes will allow .exe's to be run as you've triedI stand corrected. Thanks for that information.

Kind regards

---

### Post by mc4man on 2011-06-04
The only real issue here is the 'security bit policy' which as implemented has dubious value (ie. - cautious-launcher

.exe's are executable files, they don't need the x bit 'set', it's the cautious-launcher that requires it

Can be seen in wine's .desktop
> 
Type=Application
Name=Wine Windows Program Loader
clipped ...

Exec=[COLOR="Blue"]cautious-launcher[/COLOR] %f wine start /unix
MimeType=application/x-ms-dos-executable;application/x-msi;application/x-win-lnk;application/x-ms-shortcut;
Icon=wine
NoDisplay=true
StartupNotify=true
That's why you only need to start using wine as the command which bypasses the .desktop's Exec= and uses the binary itself which has no such requirement

---

### Post by BanannaButt on 2011-06-04
> **mc4man said:**
> vfat (FAT32), volumes will allow .exe's to be run as you've tried, ntfs will not.
Try just using wine instead of the default 'Wine Windows Program Loader'
Either a one time - r. click on any .exe > open with - other application > use a custom command. For command just use 
wine
Then  use wine on r. click on any .exe or set as the new left click default thru r. click > properties > open with on any .exe
or in your Ex.
```
wine '/media/0810B0E010B0D5C2/Users/Sean/Downloads/uTorrent/Completed Downloads/Crysis_2_v1.8-FAiRLiGHT/Crysis_2_final_1.8n_Patch.exe'

```
This solution has worked.  Thanks for your help.

---

