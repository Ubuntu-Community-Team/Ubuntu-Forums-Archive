---
title: "Wine App Launcher and AWN"
date: 2009-01-26
forum: Wine
---

### Post by Iwanthelp on 2009-01-26
Hi, I just installed Xubuntu a couple days ago and got AWN for a dock and went camping and left my brother to customize it, and now I got WINE and got to run Photoshop(5.0) through it, and when I added a launcher to AWN for it, and so I Googled how to do it after doing it like a normal program, and my brother told me to put "Wine [path to Photoshp.exe.]" on it, so I did that, and it didn't a appear on my dock and then I Googled some more, found an Ubuntu Forums post, I did what it said, didn't work, found another, didn't work. And so I've tried, I think three different ways, and none of them worked. I'm tired of searching around, and most of them probably won't work, so, could somebody guide me through how to do it?(Note, I'm a Linux noobie and am not a nerd, and have hardly any experience with the terminal and Windows command prompt, so you'll have to explain just about all of it in simple terms.) You can go ahead and supply links to other posts and I'll see if it's one I've read or if not, if it works, and reply to what it did.

Note: After this has been solved, don't bother contacting me through PM or post or anything, 'cause I'm only here to get this answered and maybe other questions later.

Thanks in advance! Help is very much appreciated!

---

### Post by Iwanthelp on 2009-01-27
Bump.

---

### Post by Iwanthelp on 2009-01-28
Anybody?

---

### Post by demosthenese on 2009-02-01
[https://help.ubuntu.com/community/Wine]("https://help.ubuntu.com/community/Wine")

Put the following as the launcher command

sh -c "cd '/home/USER/.wine/drive_c/Program Files/Appdir/'; wine '/home/USER/.wine/drive_c/Program Files/Appdir/program.exe'"

Of course you need to replace USER, Appdir and program.exe with proper data.


HTH

---

### Post by Iwanthelp on 2009-02-08
Ok, thanks I'll try it when I have it back up and running...

---

