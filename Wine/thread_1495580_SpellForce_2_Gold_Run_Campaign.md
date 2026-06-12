---
title: "SpellForce 2 Gold Run Campaign"
date: 2010-05-28
forum: Wine
---

### Post by Confused Computer User on 2010-05-28
Hi all,

First time posting a question concerning a Windows game running on Linux so please be patient (I'm a newb)

Ok so the breakdown.

Software:
Ubuntu 9.10 with latest updates.
Wine 1.2-rc1
Spell Force 2 Gold Edition (original game and add-on) 2.01 Build 125055

Hardware:
Processor        2x Intel(R) Pentium(R) 4 CPU 2.60GHz
Memory           1025MB (326MB used)
Graphic Card     ATI Radeon X1600
Resolution       1152x864 pixels
OpenGL Renderer  Mesa DRI R300 (RV530 71CE) 20090101 AGP 4x x86/MMX/SSE2 TCL

Problem:
I installed the game and to my surprise it works. Now the videos are a bit weird. There is a series of clips that run prior to game menu (these are like the one that are made by the various companies that built the game ie Nvidia and co.) But the sequence were we see the dark elves fighting is never shown. I just get to the main menu of the game.

Ok so far. Now I click on play campaign and the game goes down. No error message just I get back to the desktop and My resolution goes from 1152x864 pixels to 1024X768 pixels. Although this seems to be random. Same goes for the skirmish option.

Now the game does seem to work with Wine but with different older versions.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7040&iTestingId=52647](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7040&iTestingId=52647)

Yet the older version dealt with older game versions as well.

What should I do?

---

### Post by asdfoo on 2010-05-29
terminal output?

[http://wiki.winehq.org/FAQ#get_log](http://wiki.winehq.org/FAQ#get_log)

---

### Post by Confused Computer User on 2010-05-29
> **asdfoo said:**
> terminal output?

[http://wiki.winehq.org/FAQ#get_log](http://wiki.winehq.org/FAQ#get_log)

Thank you for the reply. I'll post the output as soon as I get back. Just one thing though.

As I get this, the command initiates the program and then uses Terminal to record a log of activity. I apologize if I got this wrong.

One thing I'm not sure. In "cd ~/.wine/drive_c/Games/Tron" the last part Tron is the name of the folder where as in "wine tron.exe &> log.txt" tron.exe is the executable found in that folder, right?

Thanks again.

Edit 29 May 2010
Ok I followed the instructions but I keep getting:

> ubuntu@ubuntu-desktop:~$ cd /home/ubuntu/.wine/dosdevices/c:/Program Files/Spellforce/Spellforce 2 Gold
bash: cd: /home/ubuntu/.wine/dosdevices/c:/Program: No such file or directory


This is the path I get when exploring the files. So what am I doing wrong?

---

