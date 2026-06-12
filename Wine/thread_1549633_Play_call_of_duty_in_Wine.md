---
title: "Play call of duty in Wine"
date: 2010-08-10
forum: Wine
---

### Post by wrix on 2010-08-10
Hello, I installed Call of Duty in Virtual Box and copied the install to Wine C:\. According to the some sources it should work. How ever even I have the CD-ROM inserted the game shows an error:

"Please insert the correct and, select OK to restart the application" 

I have assigned my CD-ROM in Winecfg, but still unable to play the game.

---

### Post by realzippy on 2010-08-10
According to which sources?Do you have a link?

It may run in wine,but I doubt that it runs in a virtual machine due to the lack of full 3D acceleration.

---

### Post by wrix on 2010-08-10
I need it to run it on Wine. I just copied the install from Virtual Box.

---

### Post by realzippy on 2010-08-10
Why don't you install it "natively" with wine?
Why copying from virtualbox?
Again,do you have a link to that "sources" ?








[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1812](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1812)

---

### Post by wrix on 2010-08-10
The game has 2 CDs installing directly don't work because it ask for the 2nd disc and the 1st CD cannot be ejected. I watched a video in youtube, its for crossover games in Mac.

[http://www.youtube.com/watch?v=fbD_nUH7ugs]("http://www.youtube.com/watch?v=fbD_nUH7ugs")

---

### Post by realzippy on 2010-08-10
To eject a disc during a wine game installation type in terminal:

```
wine eject
```

[http://wiki.jswindle.com/index.php/Wine_eject](http://wiki.jswindle.com/index.php/Wine_eject)

---

### Post by wrix on 2010-08-10
Sorry it didn't work, the first disc ejected but the second disc cannot be mounted. Is there any way to disable the copy protection, actually that is what I want. It runs when copy-pasted but ask for the disc, when inserted it cannot detect it.

---

### Post by realzippy on 2010-08-10
Sorry,no idea  ;)

---

### Post by 0004tom on 2010-08-10
> **wrix said:**
> The game has 2 CDs installing directly don't work because it ask for the 2nd disc and the 1st CD cannot be ejected. I watched a video in youtube, its for crossover games in Mac.

Thats not true.. just mount both ISOs then with winecfg map both mounted iso as drives, when you asked to change tell it to load from the second mounted drive. I just installed MW2 yesterday using this method.

---

