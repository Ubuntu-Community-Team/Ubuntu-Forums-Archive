---
title: "Real Problem With Ubuntu/Grub/Windows"
date: 2007-05-09
forum: Windows
---

### Post by Mr. Soundless on 2007-05-09
Hi everyone..

INTRODUCTION:
I got a problem with my laptop (HP DV2085EA)..
I loved and still love Ubuntu especially after Feisty came out... I'm using it since December now but... (yes there is a but!!) I miss Windows.. I've always been a game addict and since I got Ubuntu the only thing I could play (live) was Second Life.. As a game addict this is pretty bad.. especially because I'm not home much so I can't be on my console (Wii)..

THE PROBLEMS BEFORE:
Now like I said I love Ubuntu except that I can't play games on it even with Wine or CrossOver. So I've tried to switch back to Windows XP.. The problem was that I couldn't install Windows.. It  did boot the cd but it couldn't detect my HDD.. After a while I found out that it didnt' boot it cause it couldn't detect my SATA HDD no clue why but it just didn't.. SOOO I ordered new Recovery DVD's from HP 2/3 weeks ago I got the DVD's I tried to install it again but this time it didn't boot.. Then I started thinking: 'I don't want to loose Ubuntu' so I've put Ubuntu on an external HDD.. Formatted the main HDD formatted it to NTFS (all with live CD). And I tried to boot the recovery disk again.. It finally booted. So after booting it asked for disk 2 started installing.. 46% asked for disk 1 and it just didn't accept it..Called HP said the disks could be broken.. So had to wait another week for the new set (free this time) got the disks 2/3 days ago.. Today I tried to boot them but they just didn't boot.. I tried reformatting setting the boot flag and stuff like that.. Still no luck... 

THE PROBLEM TO BE SOLVED:
Now like I said I can't boot the dvd's and I really need help with this.. I unplugged my external HDD and it just skipped my DVD and tried to boot my HDD with no chance cause it's empty giving a Grub Error 21 (No Hard Drive error) understandable...
Checked boot order multiple times.. SATA support on BIOS is enabled I thought maybe it's bugged and they've put enabled instead of disabled so I've set it to disabled and STILL NO LUCK
SO NOW:
PLEASE HELP ME BOOTING I really need this

---

### Post by u01p2109 on 2007-05-09
If you can - install windows fresh version, then run feysty-desktop to install Ubuntu. Then just copy needed information.
For dual boot: Windows XP OR Ubuntu
1. install or repair Windows XP installation
2. Restore all needed information to Windows (NTFS partition)
3. Boot from Ubuntu-Desktop-feisty-fown LiveCD
4. Then You Install Ubuntu, You also can import settings from Windows
5. REMEMBER, use part or all free space on disk - do not delete NTFS
6. Boot from grub and chuse your favorite OS

I have HP dv6119ea - it works good for me :) 

P.S.: I can also sent You information about Windows drivers...

---

### Post by Mr. Soundless on 2007-05-09
The problem is .. I can't install Windows cause it doesn't boot the cd..

---

### Post by goumples on 2007-05-09
take an ms-dos disk and boot it, to get to a command prompt.  Then type fdisk/mbr .  This will reset the MBR and kill off grub.  Then try booting from the windows cd again.

---

### Post by Mr. Soundless on 2007-05-10
I'm not sure if it became better or worse after that I hope it's good what happened :P.. :

I booted from my HDD with ubuntu, installed some fdisk like stuff.. ran it and removed the bootloader (Grub) tried to reboot but now...
nothing works :P I mean it doesn't load the internal HDD neither the external one + it doesn't load my HP recovery dvd .. odd but true is that it DID load the Feisty live cd (which I'm on atm)
Any ideas?

P.s. it asks for some bootdisk or something too bad I don't have a floppy drive and it doesn't load the dvd not sure what to do now

UPDATE: I just rebooted and it doesn't even give an error anymore it just gives a blank screen

---

