---
title: "How to make a backup of windows before wiping disk"
date: 2016-05-23
forum: Windows
---

### Post by vincent_zamora on 2016-05-23
my source drive is 1 tb and my destination drive is 120gb, could i copy an image of my disk to the 120gb? if so how? sorry if its a noob question
thanks!

---

### Post by QDR06VV9 on 2016-05-23
Hi vincent_zamora
I tend to like the Clonezilla / GParted option it has always worked for me. 
 Here is basically how it goes.....
1) You reduce the partition first using GParted (To the same size as the target or smaller)
2) You let the computer boot so it can fix any possible filesystem errors.
3) You clone the partition using [Clonezilla,]("http://clonezilla.org/") which is free and open source.

You can refer to this article:  [http://geekyprojects.com/storage/how-to-clone-hard-driv](http://geekyprojects.com/storage/how-to-clone-hard-driv)...

Hope this helps.

---

### Post by Mark Phelps on 2016-06-02
If you're still following this thread, try using Macrium Reflect -- as it allows you to compress the image to save space.  If your used space on the 1TB drive compresses to less than 120GB, you would be able to "image" it (not "clone" it) to the 120GB drive.  They also make it available for free.

---

