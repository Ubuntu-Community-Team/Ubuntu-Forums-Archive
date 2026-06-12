---
title: "Can anyone help me w/ a Windows issue?? Just reinstalled Windows and it is acting up"
date: 2007-04-03
forum: Windows
---

### Post by billdotson on 2007-04-03
I just formatted my HDD, and then reinstalled Windows XP SP2.  It is weird.. Windows didn't install itself on the partition and name that partition C:\ instead it is installing on partition I:\

I have installed Steam, Office 2003, Firefox, AVG Free, Spybot S & D, Opera, Thunderbird and Adobe Reader 8.  I have also installed my videocard, soundcard and motherboard drivers.  When I installed Opera and AVG I got an error message:

There is no disk in the drive.  Please insert a disk into drive \Device\Harddisk\DR3.

Both programs installed fine after getting past that dialog box, but now every time I run them I get that same message.  Does anybody know what is going on?

Windows is really making me angry.  All I want to do is do a fresh install w/ all my PC games, firefox, thunderbird and all my other apps and have a really clean install, but Windows seems to not want to act normal.  I want to get a clean install with everything configured and then use a ghost program to completely back it up.  Although, I do not want to pay for Norton Ghost or Device Image, and PartImage just doesn't seem to be working.  Ghost 4 Unix sounds great and all, but you have to have an FTP server to send it to.  Why??

Anyway though.. the main priority is that I get Windows configured and working correctly.

Thanks again.

---

### Post by aysiu on 2007-04-03
This is on a fresh reinstall? Because the only two threads I found on a Google search for *\Device\Harddisk\DR3* had to do with trojans and viruses.
[http://forums.techguy.org/security/485343-help-hijackthis-log-included.html](http://forums.techguy.org/security/485343-help-hijackthis-log-included.html)
[http://forums.spywareinfo.com/lofiversion/index.php/t33641.html](http://forums.spywareinfo.com/lofiversion/index.php/t33641.html)

---

### Post by billdotson on 2007-04-03
yes I literally just installed it ~4 hours ago.  I did not even have it hooked up to the internet when I was installing drivers and programs because I did not yet have AVG Free virus scanner installed.

---

### Post by samadams on 2007-04-24
When you did this fresh install - EXACTLY how did you go about it?  (and what problems were you having that prompted it?)

I've done this several times myself in several different ways.  In my experience, the only 100% sure fire way to get a good clean install is with a full version (no upgrade) CD and to set my bios to boot from CD on power up.  Then when the DOS installer begins, I use the options to delete ALL partitions on the drive I want to install Windows to, create a new partition for Xp and install it there with NTFS  (It also works best if that drive is the ONLY drive in the system - I had this problem when trying to reinstall after putting Ubuntu on a new HD I installed that was set to be the master drive - I had to temporarily remove the linux drive and reboot with only my XP drive as the master drive and the CD set to boot first in the BIOS - then after the clean install, I reattached the linux drive and set it to slave - everything has worked fine since)  If you have linux on the same drive you may be able to salvage it but I don't know how.  I would back up linux, accept having to fresh install it too, and then do the above though someone more savvy with linux than I may know how to avoid that.

Also, you stated you 'formated the drive' - how did you go about this?  what software did you use?  perhaps that is the problem.  When you went to install XP what partitions did it list as available along with their drive letters?  Does your bios reflect a drive letter "I" ?  I've found that using the XP DOS installer does the job very well if I delete all partitions and format them for NTFS (which is I think how MS intended it - although they allow for other methods and saving pre-existing partitions, they really want theirs to be the only OS on your system)

---

### Post by samadams on 2007-04-24
After doing a little research on your DR3 issue...

What is your EXACT hardware configuration?

How many physical HD's with how many partitions each?

How many floppy, CD, DVD drives etc. in the case?

How many and what types of external devices? (mice, keyboards, {are they USB?}  printers, cameras, memory sticks, etc.)

From what I've found, if you pare down the system to only essential internal devices, do a clean install and get fully updated, then add your externals one at a time starting with a printer (if it is USB) this should solve the DR3 error.

The point here as well as my above post is to eliminate all non-essential issues and all possibilities FIRST, then start compounding the problem.  It is much easier to work forward by adding software and devices than backward by eliminating them.

---

### Post by Imsati on 2007-04-24
>In my experience, the only 100% sure fire way to get a good clean install is with a full version (no upgrade) CD and to set my bios to boot from CD on power up.

An Upgrade CD will work fine also. XP Upgrade CD's actually contain the entire OS on them. When booting into the CD from BIOS, you'll have the option to 'Upgrade' or 'New Installation'. If you choose the 'New Installation' option, the CD will look for evidence of a valid previous upgradable Windows OS.

In my experience, the BEST way to do a fresh perfectly clean install of XP is as follows...

1-Backup ALL of your files (I cannot even BEGIN to stress this enough)

2-Using either your HDD's Utility CD Rom or a disk containing 'Fdisk' (WinME boot disks are nice, if not severely outdated, but they do the trick very nicely), run 'Fdisk' on the drive in question to wipe everything giving you one raw-formatted drive with no partitions.

3-Set up your partitions however you want and format them all to FAT32.

4-Once all that super-fun stuff is finished (yes, very sarcastic), Put in the XP CD and Reboot. From BIOS, boot into the CD and select 'New Installation'. Since the installer will search for and not find a previous version of Windows, it will ask for a valid OEM Windows Disk containing a Full Version of any Upgradable OS (Win 98, 98SE, ME, etc.).

5-When prompted for the above-mentioned disk, open the CD tray and remove the XP Upgrade disk and insert the Upgradable OS disk (the XP Upgrade will have already copied part of itself to the freshly-formatted HDD so you won't ruin anything by taking the disk out).

6-After the XP Upgrade program accepts the previous-versioned disk, it will prompt you to remove it and once again insert the XP Upgrade disk. After that, just follow the instructions on-screen and let it do it's thing. At this point, the XP Upgrade disk is basically a 'pseudo-Live CD', and anything from this point on will be done solely from the CD. That being said, when it gives you the option to format the FAT32 partitions (from when you ran Fdisk) to NTFS partitions, do it as XP runs better with NTFS.

--Jay

---

### Post by Imsati on 2007-04-24
>it will ask for a valid OEM Windows Disk containing a Full Version of any Upgradable OS (Win 98, 98SE, ME, etc.).

Oh yeah, just to clarify...the Full Version doesn't have to be from M$. **So if you had a Windows CD from let's say...Dell, or HP (from when you purchased your Dell or HP of course...)** it would work perfectly ;)

---

### Post by billdotson on 2007-04-25
issue fixed.. just reinstalled.

---

