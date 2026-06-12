---
title: "Avast jarbled my NTFS file system - How do I repair?"
date: 2007-08-24
forum: Windows
---

### Post by motin on 2007-08-24
Short version:
* My NTFS file system is jarbled
* I have no backup...
* Performing an image backup takes appr 660 hours(!) with numerous reportings of unreadable sectors encountered
* Other partitions on the same drive are fine so it doesn't seem like a mechanical error.

So how do I repair this jarbled data with the lowest risk of damaging the file system? Should I first wait 660 hours (about 658 hours left...) before attempting anything?

I have yet not run chkdsk /r in case I would ruin anything important - taking backup first I thought but then I do not wish to wait for several weeks for it to finish...

Big thanks for any help!

Long version:
I recently installed Avast Antivirus and responded "Yes" when asked to perform a boot time scan.

On the boot time scan, I answered "Yes move all to quarantine" on the found injected/trojaneous items.

Apparently Avast thus moved kernel32.dll, winsock.dll and wsock.dll to the quarantine - making it impossible to boot Windows...

Apparently it seem to have jarbled up the file system as well, since mounting the file system in Ubuntu (Live CD) using ntfs-3g reports free space on drive to 0 bytes. I could still delete files and also move back the three critical dll-files to it's proper location.

This didn't help since Windows just reboots no matter what boot-up option I choose - except for when I choose to inactivate the Automatic reboot on critical system failure - then it complains about an encountered stop error: UNMOUNTABLE_BOOT_VOLUME.

Booting up in BartPE shows the filesystem as Unrecognizable. All read operations are taking forever...

*Referring to short version above for questions and plea for help*

---

### Post by smoker on 2007-08-24
hi, it looks like you will have to do a windows repair before you will be able to boot windows again. a windows repair install won't overwrite your data, some info here: [http://www.michaelstevenstech.com/XPrepairinstall.htm](http://www.michaelstevenstech.com/XPrepairinstall.htm)

though, of course, as you are trying a backup is the first thing to do if you can. you don't mention what app you are using for an image backup, but you can copy partition to partition with the 'gparted live-cd' and now you can have it with 'clonezilla' included as a boot option, info here:
[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

best of luck

---

