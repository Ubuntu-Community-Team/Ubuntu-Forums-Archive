---
title: "Why Civ 4: BTS takes so much time to start (Ubuntu only)"
date: 2011-07-04
forum: Wine
---

### Post by Neo40 on 2011-07-04
Hi,

I did re-install Ubuntu 11.04 twice then Xubuntu 11.04 and each time when I want to play the game (I have only Civ 4 BTS), it takes about 2 minutes (ok, it's 1m30s exactly) before I can see the menu of the game. Then, I can play the game fine.
I tried with Archlinux and Debian on the same PC, and I can start to play the game in 10 seconds! 
Anyone has this issue? Is it possible to fix it? 
Actually, I have Debian installed, but I would like to reinstall Ubuntu 11.04 (I pretty love Unity!) but I don't want to wait 2 minutes before playing a game.

Thanks for your help.

---

### Post by dankegel on 2011-07-04
What graphics card and drivers are you using?

Maybe you forgot to install the proprietary nvidia drivers on ubuntu.

---

### Post by Neo40 on 2011-07-09
Ok, to answer to myself I know where is the problem. During installation, I used  to choose encrypt my home directory. So, when I do that, Civ IV is longer to load. Weird, because with older version, it never happened. Today, I reinstall Ubuntu 11.04 without encryption and the game load faster now! (Just like Debian and Archlinux).
I think there is probably a bug with ecryptfs?

---

