---
title: "ubuntu server command : reboot from cd"
date: 2011-09-25
forum: Server Platforms
---

### Post by evarie on 2011-09-25
My old Toshiba tecra 8000 is turning on ubuntu server i386.
With a bootable cdrom Acronis True Image home, i want to make
a backup from the partition.
I want a command for the commandline on my server, to reboot from cdrom.
The bios i already try, but it do not his work.

Do you know that command?
I will command ubuntu server for a reboot from cdrom, but i do not know how?

Google not found.





Mijn oude laptop draait alleen op ubuntu server.
Met een opstart cd Acronis True Image home wil ik een backup maken.
Hier voor wil ik graag een commando invoeren op de commandline.
De bios heb ik al ingesteld dat de laptop vanaf cd moet starten.
Maar dat lukt niet.

Wie weet het?
nota bene : Google niet gevonden

---

### Post by volkswagner on 2011-09-25
If the BIOS does not have the option to boot from CD ROM then it is a hardware limitation.

Does it have a floppy?  You may be able to run SuperGrub on a floppy drive and hand off the boot process to the CD ROM.

It may be far easier to remove the hard drive from the laptop and boot Acronis from a secondary machine that can house the Tecra hard drive.

You can also create a nice backup using the tar command from a running system.

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

