---
title: "Heroes of Might and Magic 3 Complete"
date: 2009-04-06
forum: Wine
---

### Post by Beguiler on 2009-04-06
Not sure if this is the right place for this post... Heroes 3 isn't exactly the latest of games. Oh well, here goes...

I'm running Ubuntu 8.10, and have installed Heroes of Might and Magic 3 Complete (installer found in setup file on Disc 1) onto my laptop. Install went fine...

Running the program went fine. But it kept saying that I did not have the disc loaded that was needed for play. I used g-mount to mount both of the .iso's that were disc one and two, but each time the program gave me the same problem.

I'm totally lost, so I turn now to you. Gmount has worked fine for other games I wanted to play, including starcraft and Heroes 3(different version).

---

### Post by Grishka on 2009-04-06
> **Beguiler said:**
> Not sure if this is the right place for this post... Heroes 3 isn't exactly the latest of games. Oh well, here goes...

I'm running Ubuntu 8.10, and have installed Heroes of Might and Magic 3 Complete (installer found in setup file on Disc 1) onto my laptop. Install went fine...

Running the program went fine. But it kept saying that I did not have the disc loaded that was needed for play. I used g-mount to mount both of the .iso's that were disc one and two, but each time the program gave me the same problem.

I'm totally lost, so I turn now to you. Gmount has worked fine for other games I wanted to play, including starcraft and Heroes 3(different version).

wasn't this version only released for windows? it looks like you're trying to run this through wine, so maybe running winecfg, and setting the drives accordingly would help. also, please post windows applications related questions in the separate "wine" forum.

---

### Post by rbaleksandar on 2010-05-22
It's an old thread but still I might be able to help someone who's looking for a solution of the problem. I got the same warning and the only thing I did was to mount the mounted ISO as a drive inside Wine. Simply open the configuration of Wine, go to **Derives** and add the mounted CD2 in the list. You can do that by manually pointing where it is (for example you've mounted the ISO in /media/HOMM3 ) or by clicking on the **Autodetect**-button bellow the list (it'll display all mounted thingies along with your mounted ISO). This solved the problem for me and I've never encountered it again. :)

---

