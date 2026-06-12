---
title: "If you have 500 MILLION files in a folder.. is it quick to open a single file..?"
date: 2016-09-10
forum: The Cafe
---

### Post by KingNeil on 2016-09-10
If you have 500 MILLION files in a folder.. is it quick to open a single file..?

500 million small .TXT files

Let's say I know the file name precisely

Is it then quick to actually open a single file, i.e. something like 

gedit file-499999999.txt

or

nano file-499999999.txt

thanks

---

### Post by DuckHook on 2016-09-10
Speed should slow a bit on HDDs. Should not make much difference on SSDs. Modern HDDs with smart caches may be quick too. A far bigger issue with so many files is running out of inodes. You may wish to *tar* them into one big file and then use *tar* utilities to look up your info instead.

---

### Post by Bucky Ball on 2016-09-11
How long's a piece of string? The speed would depend on many factors, all to do with hardware and not just whether you are using a HDD or an SSD. RAM, CPU, motherboard will all effect this and it is down to where the first 'bottleneck' occurs, if it does.

The bottleneck is a clue to the actual speed you are going to get. Without full hardware specs and the exact size of the file to be moved, any answer to this question is theoretical, and even with them, an educated approximation. ;)

---

### Post by QIII on 2016-09-11
Not only theoretical, but a bit theatrical.

Not a support question.  Moved to The Cafe.

---

### Post by pqwoerituytrueiwoq on 2016-09-11
opening the folder in a GUI file manager would be slow, but if said folder is managed by a script or program it should be fine, but i have never had over a couple thousand in a folder

---

### Post by yetimon_64 on 2016-09-11
> **pqwoerituytrueiwoq said:**
> opening the folder in a GUI file manager would be slow, but if said folder is managed by a script or program it should be fine, but i have never had over a couple thousand in a folder

I've had up to 5 or 6 thousand files in a folder and the GUI file manager access is pathetically slow (sata2 HDD in use) but as quoted above accessing a single file with a script or program (like an image viewer or music player) is absolutely fine. 

Directly accessing an individual file with, for example, gedit, nano, mplayer or gthumb, shows no noticable slowdown in accessing the file here. The only problem I notice is actually opening the folder in nautilus itself; I suspect the access would be much quicker with image thumbnailing turned off, though I've never actually tried to turn it off in nautilus to test.

---

