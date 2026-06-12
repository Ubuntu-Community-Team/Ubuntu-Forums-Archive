---
title: "Darkstar one problem"
date: 2011-04-01
forum: Wine
---

### Post by smart734 on 2011-04-01
Hello, i bought DVD with darkstar one game, but it not work. Before i bought DVD i tried demo and demo work, so i bought DVD, but if i run it in terminal:

[email]martin@kluci:~/.wine[/email]/drive_c/Program Files/Darkstar One$ wine DarkStarOne.exe 
fixme:ntoskrnl:IoAllocateMdl stub: 0x1110f0, 5, 0, 0, (nil)
fixme:ntoskrnl:KeInitializeTimerEx stub: 0x110fa0 0

I tried to found anything on the internet and i found, that it work in wine 1.3.x, so i upgrade my wine, but the terminal saying samething. Please help. THX and sorry for my english, because im czech.

---

### Post by An Sanct on 2011-04-01
> **smart734 said:**
> Hello, i bought DVD with darkstar one game, but it not work. Before i bought DVD i tried demo and demo work, so i bought DVD, but if i run it in terminal:

[EMAIL="martin@kluci:%7E/.wine"]martin@kluci:~/.wine[/EMAIL]/drive_c/Program Files/Darkstar One$ wine DarkStarOne.exe 
fixme:ntoskrnl:IoAllocateMdl stub: 0x1110f0, 5, 0, 0, (nil)
fixme:ntoskrnl:KeInitializeTimerEx stub: 0x110fa0 0

I tried to found anything on the internet and i found, that it work in wine 1.3.x, so i upgrade my wine, but the terminal saying samething. Please help. THX and sorry for my english, because im czech.
Make a folder in the wine "c:" (Applications>wine>browse c: drive) and copy the whole DVD into that folder.

After you copy everything, make sure, that install/setup has the executable bit set to true, then install

If that also fails, let us know.

---

### Post by smart734 on 2011-04-02
No, it isnt work, but wine tell when installation finishing "Unable to proceed (error 32)" and the title of error window is "TAGES Drivers". Maybe i will try install it with sudo.

---

### Post by An Sanct on 2011-04-02
Have you got Winetricks installed? In the official wine page, the game is [rated gold]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=8184").

---

### Post by smart734 on 2011-04-03
I have winetricks and i know, that thig game is goldrated, because i buy it for that. Last i tried to install TAGES Drivers from downloaded exe file, but it wont install. It me ask for admin privilegies, but if i press yes, it tell me  that i dont have privileg. If i run with sudo in terminal, it tell me "The .wine is not owned to you". Are TAGES drivers in wine trricks? Witch name they have?

-----------------------------------------------------------------------------------------------
EDIT

I found Tages dirvers exe file on DVD, but for their installation i need admin privileges. I found on wine wiki, that in win98 there isnt admin privileges, but There is new error code, it is 87. Please help, i found that i get in wine only admin privileges in win98. There must be another way. please help. P.S. I have Win XP in virtualbox. I can export some dlls from there.

---

### Post by smart734 on 2011-04-04
I solved it. I changed the game for The Witcher. If you want Darkstar one, dont buy DVD version. You must buy download version.
[http://www.gog.com/en/gamecard/darkstar_one]("http://www.gog.com/en/gamecard/darkstar_one") 
On DVD there are TAGES drivers, witch you cant install.

---

