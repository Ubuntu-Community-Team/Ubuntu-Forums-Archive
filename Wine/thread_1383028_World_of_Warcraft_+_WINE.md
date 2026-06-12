---
title: "World of Warcraft + WINE"
date: 2010-01-16
forum: Wine
---

### Post by Hotrod76 on 2010-01-16
I recently installed ubuntu 9.10 on one of my computers in hopes of migrating completely away from windows.  I do not have any real experience with linux but from what I have read ubuntu seemed the best fit.  I have read everything I could find online and even tried using options out of a couple linux magizines I purchased to install and run world of warcraft on linux.  The problem is when I use my wow disk all the files I need are hidden and when I try to unmount and then remount the cd at the terminal it just gives me a message No such file or directory.  I read that on the wrath of the lich king cds that only the direct x and installer folders would show up which is what my battle chest cd version is doing.  I have been trying to get wow up and running for over a week now and have exhausted every other possibility I can find so I would really appreciate any help you can give thanks

---

### Post by CCBalla10 on 2010-01-16
Yeah I know what you mean.  I had been trying to figure a way to get it to run in Linux and never really got any answers.  To be honest...if you want to run a game, just keep a small install of windows around just to play games.  Its honestly gonna run better in Windows than it will in Linux under Wine.  Just my .02

---

### Post by Hotrod76 on 2010-01-17
I guess my real problem is here that I need some help figuring out how to make these files show up, so that I can install them.  I know I could keep a small install of windows for the game, but am hoping to get ubuntu squared away on this computer so I can remove windows on my other computers.  When I do that there are going to be other programs that I will also need to use inside of ubuntu.  Thats why I am trying to familiarize myself with ubuntu more before I try to just drop it on my whole family.

---

### Post by CCBalla10 on 2010-01-17
I understand what you are trying to do, just giving you some insight from someone who tried to get it to run under Ubuntu and failed.  Its not a bad thing to keep a small windows partition just for the game (we all know its one of the best games out there :))

---

### Post by Sef on 2010-01-17
Moved to the WINE forum.

---

### Post by sxmaxchine on 2010-01-17
hello i have had wow wrath of lich king runing on my ubuntu 9.04 computer without any trouble at all. 
the way i got it to work was to install the the game (includes expansions and patches) on a windows pc. then i simply copied the folder onto an external hard drive then i plugged it into my computer clicked on the exe and it started playing perfectly except for a little glitch wen you need to login but i fixed that with an on screen keyboard.
also i was using wine version1.0.1

---

### Post by Hotrod76 on 2010-01-17
Not sure why this is now in the wine forum since wine isn't the problem but what the heck right.  I just need to find out how I can unhide the files on the installation cd from the battle chest set I bought for my world of warcraft game.  I haven't tried just loading the files on an external hard drive and moving them because I do not have one available to do so.  And even though I am currently dealing with this problem with a game installation cd I am hoping to find out some info on this issue in case I run into a similar problem with another program that I am atempting to use under ubuntu.  Thanks agian

---

### Post by sxmaxchine on 2010-01-17
ok il try and help with the hidden files. you can try ctrl+h as they shows hidden files but im not to sure if it only works for the ubuntu hidden files (.wow). there is also an option in the preferences menu (edit > preferences), in the view tab look for a checkbox that says show hidden and backup files. if these two options dont work you could try installing dolphin and see if that shows the files.
sorry i cant give any better help.

---

### Post by Xog on 2010-01-17
it's easier to just d/l the installer from the WoW website. Just login and download it. I never really bothered trying to install with the CD. good luck.

---

### Post by Hotrod76 on 2010-01-17
Thanks had hoped to avoid that since I have the installation cd but will give that a try

---

### Post by Dark_Stang on 2010-01-17
Wow works fine for me. Just download the installer and go.

---

### Post by Hairy_Palms on 2010-01-17
its a weird disc, the hidden files arent normal hidden, to get around it you need to remount the disc with different options

Unmount the DVD with: sudo umount /media/cdrom0
Remount the DVD: sudo mount -t udf -o ro,unhide /dev/cdrom /media/cdrom0

worked for me, if ur cd drive isnt /dev/cdrom then substitute for it there

---

### Post by painmonger on 2010-01-17
> **Hairy_Palms said:**
> its a weird disc, the hidden files arent normal hidden, to get around it you need to remount the disc with different options

Unmount the DVD with: sudo umount /media/cdrom0
Remount the DVD: sudo mount -t udf -o ro,unhide /dev/cdrom /media/cdrom0

worked for me, if ur cd drive isnt /dev/cdrom then substitute for it there

I did the same thing to copy my info from the dvd, worked just fine. I did find that updating wine to the latest version solved issues with running the installer. If you haven't come across this bit of info, don't run WoW from the default Launcher.exe as it will cause your permissions to reset on the WoW folder and shut you down. If you want to use the desktop icon just right click, go to "edit launcher" and change the last part of the command path from "...Launcher.exe" to "...WoW.exe" and you should be fine.

---

