---
title: "Not sure where to post or who to ask..."
date: 2018-03-26
forum: The Cafe
---

### Post by Jedwinjim on 2018-03-26
Hi hi, basically it's time to buy a new my laptop after a few years, my current laptop (Asus zenbook ux31e) was purchased second hand and I immediately wiped windows off and installed Ubuntu. Now it's time to sell I realise I will get more money for it if I have Windows on it than I would selling it with linux or OS free. If I were to buy a new laptop with Windows 10 pre-installed would it be possible to transfer the Windows license/download to my zenbook (as obviously I'll be putting Ubuntu on the new one) or does it not work like that anymore? (the last time I really used Windows was in the days of getting a back-up CD-ROM and à Windows key and installing it on different machines was easy so I'm massively out of touch).

Many thanks for your help. 

Joseph

---

### Post by QIII on 2018-03-26
Moved to The Cafe.

No, that wouldn't work.  When pre-installed, the hardware OEMs use the OEM version of Windows.  That is locked to a particular machine (the activation process does some hocus pocus to build a hash from an inventory of the hardware).  Change the hardware and the OS will complain and refuse to work without activation.  You won't be able to activate Windows on the new machine because the hash will be checked against Microsoft's master database.  They'll tell you to contact the OEM, who will refuse to do anything because you moved the drive.

---

### Post by Jedwinjim on 2018-03-26
Not the answer I wanted but I appreciate it all the same!

Thanks 

Joseph

---

### Post by oldfred on 2018-03-26
If UEFI, your product key is in UEFI.
Do not know if then you can install standard Windows ISO which requires payment in 30 days if you do not have key, or an Asus OEM image.
Vendors sometimes have the OEM image at nominal cost, since they do not provide DVDs anymore.
Difference may just be what drivers are included.
 Windows 10 ISO
[https://www.microsoft.com/en-us/software-download/windows10ISO](https://www.microsoft.com/en-us/software-download/windows10ISO) 

Did you also erase the Windows recovery partition on drive?

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

One of our standard suggestions is a full backup of Windows just for this case. 
You may want to do that for new system also.
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

