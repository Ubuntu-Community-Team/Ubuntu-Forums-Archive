---
title: "Changing E-Sword's Study-Notes Font"
date: 2010-01-03
forum: Ubuntu Christian Edition
---

### Post by Pepe Lebuntu on 2010-01-03
Hi all,

I had noticed that I couldn't change the default font in E-Sword's Study Notes. I'm not sure if anybody else has had this problem. Anyway, by a quirk of providence, I found that I now could today. I THINK it might have been one of those weird things that did it - I accidentally turned off "Paste as Formatted" by hitting F11. When I discovered in the menus what F11 did, it was in the same area as changing the default font. So I figured, what the hey, I'll try for the umpteenth time to change the default font - to my surprise, it worked this time!

Anyways, I'm curious. Have you also had the problem of not being able to change the default font? If so, how did YOU fix it? If you hadn't fixed it, could you try my quirky F11 fix, and see if that does it? If it does, then everybody can use it.

---

### Post by Pilm on 2010-01-25
I read your post and really have no idea what you did with F11 (pressing F11 on my version of eSword doesn't do anything noticeable). Maybe you could give a step by step instruction for those like me unable to follow what you did.
 
As far as study note fonts, it's driven me crazy that there is no default setting in the menus. While Georgia 11 pt is fine for the Bible display, I want something smaller and easier to read for the study notes, like Arial 10 pt. The way I modify it is to take the file study.notx (usually parked under "My Documents" in your user directory), open it with SQLite Database Browser (freeware), export the file as an SQL file. You can then directly edit the SQL file you just created with any text editor like Notepad, and do a replace of "Georgia" font with "Arial". Save the file and close, then go back to SQLite DB Browser and import the SQL file and save as study.notx. Then put this file back into your "My Documents" directory and open eSword, and you'll find all your study notes in your desired font. Note that this only modifies existing study notes, any new ones will be in the standard Georgia 11 pt font, and you'll have to repeat the above procedure again. So it's a pain but works, however if I can directly modify the default setting without having to do all this that would be great.

---

### Post by david_kt on 2010-01-25
I have no problem changing font type and size. How do you install e-Sword? Did you use the installer/method from below thread?

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

DK

---

### Post by Pilm on 2010-03-06
I figured out how to change the default font size for e-Sword's study notes, go to Options > Editor Options > Default Font, then pick whatever font you wish and next time you use study notes this will be used.

---

