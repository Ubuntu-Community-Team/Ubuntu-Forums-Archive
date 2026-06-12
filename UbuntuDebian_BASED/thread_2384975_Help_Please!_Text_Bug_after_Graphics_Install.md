---
title: "Help Please! Text Bug after Graphics Install"
date: 2018-02-14
forum: Ubuntu/Debian BASED
---

### Post by tithonius on 2018-02-14
Okay, so this is my first time posting, so be gentle.

Today on my laptop i tried to install a ppa for graphics, this one here to be precise: [https://www.pcworld.com/article/2025909/gaming-on-linux-a-guide-for-sane-people-with-limited-patience.html](https://www.pcworld.com/article/2025909/gaming-on-linux-a-guide-for-sane-people-with-limited-patience.html)

I used the tutorial there to install what he said to install for the AMD drivers older then 6xxx. I did so as the laptop that I am attempting to use the drivers on is an old HP Pavilion DV7 and it has integrated Mobility Radeon HD3200. after the install went fine and everything i went to restart and everything booted fine, just like i figured, but all of the text on my desktop now has this weird shadow around it. everything else about the computer works fine, just that alot of the system text seems bugged. its unreadable if its on a white background. Ive tried to do a ppa purge (without really knowing what i was doing) for the ppa and i get a weird output from the console. I then tried to do an update and upgrade, but after a restart, the text still has issues. so what i really need to do is to get back to the stock drivers that come with the OS, they worked much better, and they didnt have the same text problem.

I am on Elementary OS 0.4.1 Loki and im on a HP Pavilion DV7-1451nr

Not sure exactly where to go from here as i am very much so a linux noob, and am trying to learn as i go. this is a littlebeyond me, and im not sure how to revert back and fix this issue. any help would be appreciated. screenshots are attached. [ATTACH=CONFIG]278525[/ATTACH][ATTACH=CONFIG]278526[/ATTACH]

---

### Post by cruzer001 on 2018-02-14
Hello and welcome to the forums :)

Why have you decided that it necessary to install the PPA?  Were you encountering graphical glitches?

A couple of easy ways to revert back...

#1 Using "ppa-purge" in terminal
[http://www.ubuntubuzz.com/2012/02/newbie-guide-how-to-use-ppa-purge.html](http://www.ubuntubuzz.com/2012/02/newbie-guide-how-to-use-ppa-purge.html)

#2 The graphical (GUI) way "y-ppa-manager"
[http://ubuntuhandbook.org/index.php/2014/01/graphical-tool-add-remove-purge-ppa/](http://ubuntuhandbook.org/index.php/2014/01/graphical-tool-add-remove-purge-ppa/)

If you still have trouble with ppa-purge or other, please post back.

---

