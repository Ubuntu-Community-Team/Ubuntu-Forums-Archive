---
title: "Cannot get past Welcome screen since moving partitions around"
date: 2008-05-05
forum: Windows
---

### Post by phenest on 2008-05-05
A couple of days ago, I decided to re-arrange my partitions. I dual boot Ubuntu and XP, and wanted Ubuntu solely on Logical partitions.

Partition arrangement before:
Extended partition:
[INDENT]Swap[/INDENT]
[INDENT]Root[/INDENT]
Primary: /home
Primary: XP

Partition arrangement after:
Extended partition:
[INDENT]Swap[/INDENT]
[INDENT]Root[/INDENT]
[INDENT]/home[/INDENT]
Primary: XP

I then used the XP CD to do chkdsk /r, just to be safe. The partition moved from /dev/sda3 to /dev/sda2, so I amended /boot/grub/menu.lst to reflect this. But XP refused to boot giving an error about not finding hal.dll. I fixed this by amending the boot.ini in XP to use partition 1 instead of 2. Now it boots fine, but goes no further than the Welcome screen, and never actually shows the Welcome message. XP hasn't crashed, but I can't do anything with it.

I'd rather not do a fresh install until I've exasperated all suggestions.

---

### Post by smoker on 2008-05-05
possibly the chkdsk /r has altered the master file table and the files required during boot sequence cannot be found where they should be. try booting the windows install cd, and entering the 'recovery console' and using the  'fixboot' and 'fixmbr' commands. bear in mind though, these commands will overwrite the grub entry in the mbr, so you will have to reinstall 'grub' afterwards.

best of luck

---

### Post by Living2007 on 2008-05-06
I don't have any tips on how to fix this, but all I can say is that partiton moving is dangerous stuff

---

### Post by phenest on 2008-05-06
I got it booting ok, but apparently it needed some registry entries changed to get it to load users settings, something to do with drive letters. But it doesn't seem possible to change the registry from a command prompt.

Damn that registry!

But don't worry. I re-installed XP instead.

---

### Post by lswest on 2008-05-06
Hmm, there is a way to edit registy entries from the command prompt, i remember reading about it somewhere, but i believe it requires a .exe file to be downloaded before hand, if i find the name again i'll post it here, so next time you can just use it from the command prompt ;)

ah, here it is: [http://home.earthlink.net/~lreynol929/ruXP/SysTools/editreg.htm](http://home.earthlink.net/~lreynol929/ruXP/SysTools/editreg.htm)

---

### Post by smoker on 2008-05-06
> I got it booting ok, but apparently it needed some registry entries changed to get it to load users settings, something to do with drive letters.

you can change drive letters through 'computer management', though, as the 'registry' required fixing, a reinstall was probably the best bet! probably faster now too!

---

