---
title: "wow cd problem"
date: 2009-08-06
forum: Wine
---

### Post by jkw30 on 2009-08-06
this is my first time posting, and i'm sort of new to ubuntu. not really new, but haven't really tried playing around with installing windows games.  ok, i got the very first  WOW dvd today. I can't get it unlocked to install it. I've tried a few things from searching about it but nothing has worked. any help would be greatful please. 

Also, the trial version for world of warcraft from the website works great, so I know my computer can run it. I just cant get the dvd unlocked.

---

### Post by hikaricore on 2009-08-06
You might want to be more specific as to what you're trying to do and what you have done.
There's nothing about the dvd that can be locked or unlocked so I'm at a bit of a loss as to assist..

---

### Post by jkw30 on 2009-08-06
well, i open the cd, i get two icons, one is installer, one is direct x. they both are locked, i click to open either one and get access denied. I've mounted the drive, unmounted the drive, remounted the drive... it's still doing the same thing. I've also tried
~$ sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/

and get 
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

not sure what that means. maybe i was supposed to change something. i have a  dvd player, burner.. it should recognize the dvd. i did the dmesg and got a bunch of stuff and at the bottom said
[12076.907672] ISOFS: Unable to identify CD-ROM format.
[12101.097170] ISOFS: Unable to identify CD-ROM format.
this is driving me crazy. like i said before, i'm not sure about installing games from dvd or cds. the trial version went so easily i hoped the game itself would too.

---

### Post by hikaricore on 2009-08-07
Well your first problem is you're trying to mount a udf dvd as iso9660..

Try and follow the instructions here:

[http://ubuntuforums.org/showthread.php?t=1064891](http://ubuntuforums.org/showthread.php?t=1064891)

---

### Post by jkw30 on 2009-08-07
i'm getting this problem, it's still locked, i'll post a screenshot soon. 

joe@bubba:~$ cd /home/joe/.wine/dosdevices/d:
[EMAIL="joe@bubba:%7E/.wine"]joe@bubba:~/.wine[/EMAIL]/dosdevices/d:$ sudo wine Installer.exe
[sudo] password for joe: 
wine: /home/joe/.wine is not owned by you

how can i change the owner of the cd?

---

### Post by hikaricore on 2009-08-07
You're not following the instructions.

At some point you've run WINE with sudo and the folder has become owned by root.
If you're not going to read the walkthrough I linked you then I'm not going to help you.

Best of luck.

---

### Post by jkw30 on 2009-08-07
you are not reading what i said correctly. i read the link, it did not help me at all. how can i access a file that says owner is user53?? there is no user53 on my computer at all. thanks anyway. whatever, i decided to install it on a windows computer and copy it from there, if that doesnt work i'll download the entire game from the website.

---

