---
title: "cd roms wont recognize"
date: 2011-06-11
forum: Wine
---

### Post by zaphodbblx on 2011-06-11
I've tried to install several games (diablo 2, diablo 2 LOD, dinerdash and plants vs zombies) and everythings fine up right up to the point where the disk either checks itself for validation or asks you to insert disk and it just wont recognize the disk
1) yes they are REAL and not burnt
2) all games worked in older versions
3)the disk is mounted and shows on desktop
any idea why?

---

### Post by christoph411 on 2011-06-11
So you are trying to install these games in wine, and some of the larger games are spread across 2 cds, correct? :)

---

### Post by zaphodbblx on 2011-06-11
yep! diablo 2 and diablo 2 LOD...they used to run in older versions but now im butting my head against a wall
ps
I'm on natty but this problem also occurred in the last 2 releases

---

### Post by christoph411 on 2011-06-11
I've run into this problem before! In wine, I have never gotten an install to work be inserting the second cd, so my solution was to copy ALL of the contents of both cds into 1 folder (yes... it may be slightly illegal to copy the contents of the cd like that, but as long as you aren't redistributing it, no harm done right? :D ) Then, once the contents of both cds are copied into that one folder, just run the setup exe and it should never ask you to insert a second cd. And of course, delete the folder with the cd contents when you are done ;)

---

### Post by zaphodbblx on 2011-06-12
> **christoph411 said:**
> I've run into this problem before! In wine, I have never gotten an install to work be inserting the second cd, so my solution was to copy ALL of the contents of both cds into 1 folder (yes... it may be slightly illegal to copy the contents of the cd like that, but as long as you aren't redistributing it, no harm done right? :D ) Then, once the contents of both cds are copied into that one folder, just run the setup exe and it should never ask you to insert a second cd. And of course, delete the folder with the cd contents when you are done ;)

didnt work..oh well

---

### Post by christoph411 on 2011-06-12
Sorry, then I'm out of ideas...  :(

---

### Post by Driger on 2011-06-13
> **christoph411 said:**
> I've run into this problem before! In wine, I have never gotten an install to work be inserting the second cd, so my solution was to copy ALL of the contents of both cds into 1 folder (yes... it may be slightly illegal to copy the contents of the cd like that, but as long as you aren't redistributing it, no harm done right? :D ) Then, once the contents of both cds are copied into that one folder, just run the setup exe and it should never ask you to insert a second cd. And of course, delete the folder with the cd contents when you are done ;)

How did you copy all the contents?

when i tried to do this i recieved "There was an error copying the file into /home/scott/Downloads. Error opening file: Permission denied

---

### Post by desktorp on 2011-06-13
Wine supports multi-disc installers, but you have to tell it what to do sometimes.  I think eject has some purpose in this regard.
[http://wiki.winehq.org/eject](http://wiki.winehq.org/eject)

---

