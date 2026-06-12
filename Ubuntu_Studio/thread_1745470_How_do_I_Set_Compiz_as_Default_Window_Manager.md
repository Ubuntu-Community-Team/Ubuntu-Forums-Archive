---
title: "How do I Set Compiz as Default Window Manager"
date: 2011-05-01
forum: Ubuntu Studio
---

### Post by guitarMan666 on 2011-05-01
Since the new version of Ubuntu Studio defaults to GNOME Classic and the Ubuntu devs removed the "Desktop Effects" tab from the Appearance settings, I can't seem to enable Compiz to be the default WM. Is there another way? I know my computer can run it and the graphics drivers are up to snuff since Compiz worked in Debian 6.0 (Squeeze) just prior to this and I can get Compiz to turn on temporarily but when I log off and back on it is back to Metacity. Any thoughts and help are certainly appreciated, I've grown attached to the Scale and Expo plugins.

---

### Post by xwindowsfan on 2011-05-01
you could try fusion icon if you haven't already.

---

### Post by jfeist1 on 2011-06-14
@xwindowsfan - Fusion Icon worked great - thank you. 

I just wanted to point out that it took a "Reload Windows Manager" to finally fix everything for me, and now everything works great. (Phew! I was just short of going back to Lucid because of this!)

---

### Post by c-1000 on 2011-06-14
if youre going to be switching back and forth between compiz and other WMs, fusion-icon is the way to go...
i havent used it in a long time, but if i remember right, it has a couple of other neat tricks it can do as well.

if youre looking for more of a "set it and forget it" solution, go to 'system > preferences > startup applications' and click 'add'.
under name, i usually just put 'compiz' but you can name it whatever.
in the 'command' box type:

```
compiz --replace
```...you can enter a 'comment' as well, but its not necessary.

done and done.

---

### Post by rajinkajun86 on 2011-06-14
I tried what you suggested C-1000, but the command is not running at startup for some reason.  Or maybe it is, but I found that my default WM is compiz through the gconf-editor.  The problem I'm running into is that for some reason my desktop effects keeps reverting back to NONE.  Any suggestions?

---

### Post by jfeist1 on 2011-06-14
Thanks c-1000, I had tried compiz --replace before trying fusion-icon too, I just ran it in Terminal to see if it would work, it ran well enough at first, but did not finish itself off, so when I Ctrl-c (or force close) Terminal, it crashed the entire WM, requiring hard restart. 

Before I run my own tests, any idea if it would wreck things for me to add to startup? Is my error above because I ran in Terminal? Should I have run sudo compiz --replace?

---

### Post by VcDeveloper on 2011-08-03
Anybody solved this yet?

---

### Post by jfeist1 on 2011-08-03
Hey VcDeveloper,   I don't know about solved, but I am basically just doing what c-1000 suggested. I already have a "start-up Scripts" file, set to "allow executing file as program". I run this using c-1000's instructions for Start-up applications. 

I have other stuff in my file (for my mouse etc) but I added c-1000's ```
compiz --replace
``` and everything is great. 

Also, I prefer to use a file instead of just putting the code directly into Start-up Apps so that I can just easily take the file with me when I move to a new machine, or quickly run it manually when needed.

  Good luck.

---

### Post by VcDeveloper on 2011-08-03
Thanks jfeist1!  That did it for me also!...__

---

### Post by trungvkvk on 2011-08-04
sorry. I am a newbie to use ubuntu.
 hopefully I'll get experience from people.
 What people experience when using ubuntu addiction please share.
 thanks.
[http://ubuntuforums.org/showthread.php?p=11004029](http://ubuntuforums.org/showthread.php?p=11004029)

---

