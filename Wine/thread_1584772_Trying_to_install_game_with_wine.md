---
title: "Trying to install game with wine"
date: 2010-09-29
forum: Wine
---

### Post by bgast1 on 2010-09-29
I am trying to install Command & Conquer Tiberian Wars and I get this message.
 
```
The file '/media/floppy0/setup.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
```

How can I fix this or better yet how do I install the game? I really don't even know where to read to deal with this.

---

### Post by Paqman on 2010-09-29
Right click on the setup.exe, go to the permission tab and check the box to allow executing it as a program.

---

### Post by bgast1 on 2010-09-29
I tried that and and I got this message.

Could not change permissions for /media/CNC3/setup.exe.

By group it says -1  

I am guessing that might also have something to do with, but I don't want to mess with it because I think I screwed things up with it in my external drive trying to do what you suggested.

---

### Post by philinux on 2010-09-29
Moved to Wine forum.

---

### Post by Half-Left on 2010-09-29
> **bgast1 said:**
> I tried that and and I got this message.

Could not change permissions for /media/CNC3/setup.exe.

By group it says -1  

I am guessing that might also have something to do with, but I don't want to mess with it because I think I screwed things up with it in my external drive trying to do what you suggested.

Yes well it cannot change permission on something readonly. :p

It does the same thing for my wife in Xubuntu but not for me in Ubuntu.

---

### Post by mocoloco on 2010-09-29
Your culprit [explained here]("http://www.workswithu.com/2010/06/11/running-windows-files-in-ubuntu-10-04-the-wrong-approach/"), plus lots of discussion on why it's good or bad.  The easiest way to get around it is to use the command line.  Open a terminal, then
```
cd /media/floppy0
wine setup.exe
```

If you haven't already, you may want to check [winehq.org]("http://winehq.org") and see if running that game requires any tweaks.

---

### Post by bgast1 on 2010-09-29
Thank you everyone who replied. After getting frustrated trying to install with Mint KDE all day, I just finished installing Ubuntu. And I am especially grateful for the terminal instruction because I didn't know that either.

This is working ok currently. 

Does this method work for games that have 2 discs as well?

---

