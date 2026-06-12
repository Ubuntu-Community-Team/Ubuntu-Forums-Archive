---
title: "Installing in wine w/ multiple cds trouble"
date: 2010-05-06
forum: Wine
---

### Post by valhemmer on 2010-05-06
I'm trying to install Civ4 using wine and everthing goes great until it asks me to insert the 2nd cd, it gives me a prompt to put in the address of said cd, and for the life of me i cant figure out where it is. It wont just recognise it which is frustrating but then when i browse to find it i find it everywhere. Its in the file system in media twice and in Z:\media for the my comp file twice also. sadly none of those worked. Has anybody figured out this yet b/c it feels like its a pretty obvious solution i just don't see it. thanks

---

### Post by cogadh on 2010-05-06
Usually when you run into multi-CD install problems, all you need to do is open a terminal and enter "wine eject D:" (assuming your CD/DVD drive is defined in Wine as "D:"), then put in the new CD and click OK on whatever it shows as the default drive.

---

### Post by mcamilo on 2010-12-24
The eject did not work for me, so I copied all the CD contents for all CDs to the same directory and the install worked fine.  Now I have a different issue (post-install) but at least I managed to install the game

---

