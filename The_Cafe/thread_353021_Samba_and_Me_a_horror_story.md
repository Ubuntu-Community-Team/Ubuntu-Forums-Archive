---
title: "Samba and Me a horror story"
date: 2007-02-04
forum: The Cafe
---

### Post by sympeltun on 2007-02-04
Oh I just had a samba horror incident!! :D i tried to share a file which was on a different partition (fat 32), the next thing i know i cant access the proper file through the windows machine, so i go back to my ubuntu(6.06) machine and delete the file. the next thing i know i cant access anything from the fat-32 partition because samba deleted the entire partition(actually put it into trash), i thought it was something samba related i tried to test a bunch of things by disabling it, rebooting and checking, i even removed samba and checked it. i decided to boot up windows and confirm that my partition is still intact, and to my suprise i find all my file inside .trash-username

i usually delete my trash without checking what's inside my trashbin because i mentally keep track of the files and i was lucky to boot up windows and double check, I could have killed myself seriously if i lost those files lol.

i dunno i just wanted to post about this, thanks for taking the time to read :)

---

### Post by EdThaSlayer on 2007-02-04
Next time press ctrl-h in Nautilus.
It will reveal hidden files.

---

### Post by sympeltun on 2007-02-04
Thanks! i didnt know that, im a total noob you see :D

---

