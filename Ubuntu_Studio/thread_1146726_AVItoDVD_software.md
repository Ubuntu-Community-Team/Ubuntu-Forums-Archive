---
title: "AVItoDVD software"
date: 2009-05-02
forum: Ubuntu Studio
---

### Post by gillespiea on 2009-05-02
Hey everyone, i was looking about for some software to create DvD's that i can watch on my home DvD player, my other half is an actress and records alot of things that need to go onto dvd and i couldnt find software that could do it very well, or as simple. So i made my first sh script and came up with a dvd creator that only asks where the AVI file is and the name of the AVI file...then it processes it and puts it on the dvd. Thats it.

This is a pre release kinna thing. Released under the GNU lisence, so please feel free to edit it and tell me what you did with it. Hoping to make a GUI for it sometime, i just need to know how to haha.

Please tell me what you think of it :)

P.S remember this is the first software i have ever made for linux.

Downloads are on my website [http://gee.isa-geek.net/download.php?list.4]("http://gee.isa-geek.net/download.php?list.4")
Please rate it and tell me if the ntsc version works as i can't use ntsc DVD's

---

### Post by gillespiea on 2009-05-02
totally forgot to say, please run this to get the required packages to make it work right :)

```
sudo apt-get install mplayer videotrans dvdauthor mkisofs libxvidcore4
```

---

### Post by B4RR13N705 on 2009-05-02
Good! nice one! youre learning pretty well! 
Anothere good DVD burner is "DeVeDe".

---

### Post by gillespiea on 2009-05-02
Been using this and testing it. Think i'm going to add a line to delete the files that are made that are not needed once the iso is created. will post up when its done :)

---

### Post by gillespiea on 2009-05-02
Ok updated the program so that 3 files that are not required after the encoding to iso is made are deleted. The next change i will make will create a menu so that if you already made an iso from an AVI file you can just select that to burn to DVD.

---

### Post by gillespiea on 2009-05-03
Updated again because i made a very silly, and single character, coding error.

---

### Post by B4RR13N705 on 2009-05-03
Also, you can use the same estructure and programe it under python, and then add a GTK, just to make a frontend. :)

---

### Post by gillespiea on 2009-05-03
never used python before. I was looking into it last night, but i'm not too sure how to use it. will probably spend all day learning it and making a GUI then making it into a deb package if i can. The more simple the program is the better i say hehe. Any tips?

---

