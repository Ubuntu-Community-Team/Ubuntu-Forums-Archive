---
title: "WOW - Lich King installation crashing in wine"
date: 2010-03-11
forum: Wine
---

### Post by Liz on 2010-03-11
hi all, 

after 4 days of fussing around and reading just about every single thread on the internet, upgrading wine and gecko, and downloading the file from blizzard, i still cant get lich king install. 

please dont ask me to use a windows machine and install it that way, i dont have one in this house at all. and i flatly refuse to put it on any of these machines. 

im running ubuntu 9.10. after losing everything recently (read last week) ive installed and upgrading from 8.04lts to 9.10. wow was the very next thing i installed after wine. 

wow and burning crusade, installed no problems. i knew lich king was a problem, so i looked around at getting it to run smoothly. i have done everything required from this site [http://gameshogun.ws/libregame/how-to-play-world-of-warcraft-on-ubuntu-linux-smoothly](http://gameshogun.ws/libregame/how-to-play-world-of-warcraft-on-ubuntu-linux-smoothly) also gone through just about all teh threads on here that pertain to lich king, and still nothing. wine crashes half way through the install process from the dvd. the install file i downloaded from blizzard site wont work at all. 

now i can get past the eula document, but it will get to 20% and crash. 

what am i missing?
i have nvidia card, with the latest driver files. 
direct rendering is working. 

wow is the only 'vice' i have and i really want to get back to playing. going through withdrawals here..

oh, also tried the work around for playonlinux. yeah, that didnt work either. 
ive had cedega when i first started playing before lich king. im not enthused by that anymore and i havent had trouble installing anything else on wine since i got it. 

any help, any help at all would be appeciated.

---

### Post by Soulcage on 2010-03-12
I understand upgrading from one version of ubuntu to another isn't a good idea and if you went from 804 straight to 910 thats even worse you might need to try a clean install of 910.
Also can you try running the install through a terminal and posting the results it might help you or someone diagnose the problem.
Do you know about the files missing from the cds some times you need to type ```
sudo mount -o remount,unhide /dev/cdrom

``` That might not do anything though, but give it a shot. Also you say your using wine 1.1.40? It might of broke the installer so try going back a version or more.

---

### Post by Liz on 2010-03-12
i know about the missing files. ive gone through this thread [http://ubuntuforums.org/showthread.php?t=1282443](http://ubuntuforums.org/showthread.php?t=1282443) and tried all those. i can get it started, but after 20% it crashes saying "wine: Unhandled page fault on write access to 0x00000262 at address 0x4c7719 (thread 002c), starting debugger..." thats from within a terminal window. 

wine about file says 1.1.40
synaptic package manager says wine1.2 installed version 1.1.40

i started from 8.04 lts. i downloaded a copy of 9.10 and burned it. but it wouldnt boot for some reason. hence why i had to go up stage by stage. you cant go from 8.04 directly to 9.10. 

i dont know what im looking for or what i should be fixing now.

i should mention, ive been through teh wine forums looking for anything they have, ive been through the wow forums, just in case. and some of that stuff is very very old. 
ill keep looking tho, cause i really really want to play. 
keeping my fingers crossed someone can help

---

