---
title: "no cd drive found, .exe's not running, and WINE not actually installed?"
date: 2011-01-25
forum: Wine
---

### Post by u-noob-tu on 2011-01-25
Firstly, im using ubuntu 10.10 with the just released WINE 1.3.12. Im trying to run a game called World in Conflict, which, according to WINE hq, should run almost flawlessly. i recently had to reinstall ubuntu, and before i did i installed this game and it ran, but crashed immediately (separate driver issue). Well, now the game installs with no problems whatsoever, but when i hit "run" after its done, it tells me there is no cd detected. so i went into drive_c/program files and tried to run the .exe, and nothing happened. i looked some stuff up online and saw people had issues with their cd drives not being detected. i went into wine config and there was no disck drive (i think the default name for it is "D"). so i hit auto detect but nothing changed. so i uninstaled wine by removing .wine folder then apt-get purge. when it finished i looked at the terminal to see the words "Package is not installed, so it will not be removed". did it say that because i deleted the .wine folder? or is it because something went weird with the install (i installed through synaptic)? whats going on here?

---

### Post by Halzen on 2011-01-25
When you have Synaptic, you should never have to manually delete a program folder. I wouldn't know the specifics without trying it myself, but I'm willing to bet that's where the problem is. Try installing Wine stable (1.3 is development) to see if that works any better for you. Also, consider a no-CD patch to get your game working.

---

### Post by u-noob-tu on 2011-01-25
just installed WINE 1.2 and it still doesnt see my disc drive. i know theres nothing wrong with it because i imported a cd last night. could it be a missing driver or package?

EDIT: forgot to mention that when i hit "auto detect" in drives tab of wine cfg, it tries to add my home folder as a new drive.

EDIT 2: okay, got the game to run, but it crashes on startup saying i have no 3d hardware support. i guess my specific question is solved. ill start a thread in the games section.

---

### Post by Halzen on 2011-01-25
Well, as long as this thread is open... I poked around a bit to see how others were handling the CD issue. I found a SUSE-related forum thread that seems to have solved the problem for a lot of people, although it is from 2006: [http://www.linuxforums.org/forum/wine/61940-wine.html](http://www.linuxforums.org/forum/wine/61940-wine.html)

Obviously, your results may vary, given the age of the thread. I've never had to use my DVD drive with Wine, as I use Steam for all of my gaming needs and rip ISOs using my Windows laptop to keep anything else simple. :P

---

### Post by bubbyGlub on 2011-03-28
Hi Lads
If you have no cd/dvd drive found error try to chmod 777 of /.wine folder, it worked for me
in your home directory type
chmod 777 .wine

---

