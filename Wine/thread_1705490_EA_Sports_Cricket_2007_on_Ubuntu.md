---
title: "EA Sports Cricket 2007 on Ubuntu"
date: 2011-03-12
forum: Wine
---

### Post by ajparag on 2011-03-12
Hi,
I want to install EA Sports Cricket 2007 on Ubuntu using wine or POL. I have wine 1.3.15 and Play on Lunix 3.8.12 installed on my laptop. 
But i am not able to figure out how to install this game. Can anybody help me out?
Also, can any of the cricket games be installed on Ubuntu? Which one?

---

### Post by ajparag on 2011-03-12
With all due respect to all the comments [above]("http://ubuntuforums.org/showthread.php?t=981053"), the question still remains whether one can play cricket 2007 on Ubuntu? so, can anyone answer it?

---

### Post by Iowan on 2011-03-12
That's a REALLY old thread - let's try a new one...

---

### Post by howefield on 2011-03-12
Have you been over to the Wine apps database ?

It got a gold some time ago...

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=15342&iTestingId=36320](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15342&iTestingId=36320) 

There may be other results.

---

### Post by cogadh on 2011-03-12
What can't you figure out? You need to provide more details if we are going to offer you any meaningful assistance.

If you want to find out what games will work in Linux, natively or with Wine, there are numerous sources available. Just to start with, [The Linux Game Tome]("http://www.happypenguin.org/") is a great source for learning about available native Linux games (just ignore the ugly and dated look of the site); for gaming with Wine, there is Wine's [Application Database]("http://appdb.winehq.org/") or the [CodeWeavers CrossOver Compatibility Center (C4)]("http://www.codeweavers.com/compatibility/") (CrossOver is the commercial version of Wine).

---

### Post by howefield on 2011-03-12
Threads merged.

---

### Post by ajparag on 2011-03-13
i have been to wine application database and it has an entry where it says cricket 2007 works (Silver) on wine version 1.0. This version is very old. Can i do something to get it working on the newer version?

Please mention what other details do you require. Thanks!

---

### Post by ajparag on 2011-03-13
> **ajparag said:**
> i have been to wine application database and it has an entry where it says cricket 2007 works (Silver) on wine version 1.0. This version is very old. Can i do something to get it working on the newer version?

Please mention what other details do you require. Thanks!

Correction. The wine version is 1.3.2

---

### Post by cogadh on 2011-03-13
If it works on 1.0, then it should also work on any version after that (usually). Try running it and if you have any problems, post back with details about what happened. See the [** Before asking for help with Wine << PLEASE READ BEFORE POSTING **]("http://ubuntuforums.org/showthread.php?t=885111") thread for the kinds of details we need.

---

### Post by ajparag on 2011-03-14
thanks for your help! :)

---

### Post by antares1974 on 2012-09-01
Hi I just thought I'd relay what I did to make this work. I'm using Ubuntu 12.04, wine 1.4. This also works using winebottler on MacOSX, but getting to the msdos command prompt through the menu. This may also work with installing windows games that require multiple cd roms, but so far I have only found it necessary for EA Sports Cricket 07.

1. Go to the wine directories, ie browse files.

2. Go to drive_c/windows/system32/cmd.exe

3. Open using wine. A msdos command window should open.

4. Type g: (or whatever drive is designated as the cd drive), then type eject.

5. Follow the prompts, replace cd with next disk.

The problem I found with this game was that the installation crashed when I tried to insert the next disk. Ubuntu wouldn't let me unmount the disk as well (in use by wine). This is a workaround for this.

---

