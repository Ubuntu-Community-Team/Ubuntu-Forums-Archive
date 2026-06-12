---
title: "Problem running Western Digital autorun"
date: 2009-09-05
forum: Wine
---

### Post by chizh on 2009-09-05
Hi, I have a Western Digital external storage, which I previously used with Windows XP. I am trying to run an autorun program (WDSyncv6_3_130.exe)using Wine, to extract some files, but getting an error message "The procedure * could not be located in the DLL MFC42u.DLL". I am very new to ubuntu, so as much detail as you can provide will be very helpful. Thank you in advance.

---

### Post by ad_267 on 2009-09-05
What does this autorun program do exactly? Can't you do everything you need just by accessing the drive through the file browser?

Wine won't run all Windows applications, it's amazing that it can run any at all. You should only really expect commonly used applications to run well, and only after checking the [wine application database]("http://appdb.winehq.org/").

---

### Post by RabidWeezle on 2009-09-06
I would try googling/downloading that dll, sticking it in your ~/.wine/drive_c/windows/system32 folder, running winecfg, and adding the dll override, and see if that works.

---

### Post by hikaricore on 2009-09-06
Chances are whatever you're trying to run in WINE you don't need to or it won't work.
Please as has been mentioned let us know what you're attempting to do.

---

### Post by Bonzai11 on 2009-09-06
He is attempting to run a program for his western digital external drive that I guess is required to access the drive.
It might work if the correct pass activates a partition on the drive, but I still doubt it would.
Why people keep annoying software like this in external storage is confusing. Most of them don't even offer encryption.

---

### Post by chizh on 2009-09-07
Hi - thank you for all the replies! Downloading and placing *.dll in the system32 folder worked!

This autorun is a syncing program. I did have some files that are on the disk and can be simply accessed, but most of my files were being synced with this external hard drive, so I needed to run this program to access most of my files. This is my first external backup setup and not sure I like being dependent on this program to access files. I guess there are pros and cons - pros are that they are somewhat secure if i loose the drive and that i don't have to copy/paste every sigle document every time i sync.

I am sure everyone does their backups differently, but I will welcome any suggestions you might have. 

Thanks again!! I am new to this community and you guys/gals ROCK! :)

---

