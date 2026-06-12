---
title: "So where do the games load to?"
date: 2009-03-09
forum: Wine
---

### Post by Mashuteichou on 2009-03-09
I was just curious because where I told it to load, its not there.  I checked the path from the shortcut, and its not there.  So, where did it load?  Its on the computer because I can configure everything, but when I try to run the game, it can't find the CD.  (Using ISO's)  

I wanted to add no cd executables to the games so I can run without having to put the CD in ever.  I use ISO of games because it loads faster.  Plus I usually lose half the CD's.   >_>

So if its in C:/Program Files/Squaresoft inc/final fantasy VII/ for example, and when I go to the program file part, and theres no squaresoft folder, where is it?

---

### Post by scratman on 2009-03-09
Oh come on!!!  Give us a blooming clue!

Are you using Ubuntu?  Do you have Wine installed?  Did you read the install screen to find out where it installed to, or just click next till it installed?  Have you tried to find out where the link points to?

We'll need this kind of info before anybody will even try to help you.  Sorry, but you can't treat volunteers like staff and expect us to do all the leg work!

---

### Post by mcla0203 on 2009-03-09
in your applications drop down, just look for the wine file browser.  you can look around in there as if it is your C/Program Files/whatever...

if you are terminal savvy its usually in your home/user/.wine directory

---

### Post by hikaricore on 2009-03-09
WINE installs Windows software in your /home/username/.wine/drive_c directory, often in the "Program Files" folder.

---

### Post by Woodsyx on 2009-03-09
Tap ctrl-h to show the wine folder since its hidden by default. 


If you want to manually build a shortcut for an exe file in wine use this and fix the username and progrma path parts.
```
env WINEPREFIX="/home/username/.wine" wine "C:\Program Files\program\program.exe
```

---

