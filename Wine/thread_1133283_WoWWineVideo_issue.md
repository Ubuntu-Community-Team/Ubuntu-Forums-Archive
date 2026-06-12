---
title: "WoW/Wine/Video/??? issue"
date: 2009-04-22
forum: Wine
---

### Post by Zoquara on 2009-04-22
I've tried asking for help on this issue in other forums areas, but have yet to get any help on it...

My husband finally decided he was sick of Win Vista (to be honest, it was mostly his own fault for DLing tons of crap, and getting viruses) and asked me to install Ubuntu on his system. I installed 8.10 on his computer (Acer Aspire T690, only upgrades to out-of-box have been to the RAM), installed Wine, Ventrilo (works fine), copied WoW from my computer (works fine on my system, and the idea of installing WotLK from disc again.. no thanks) and everything appeared happy..

Triued to start WoW and log in... First thing of note: the "frame" of the game (running in Windowed mode) was missing.. but still tried to log in, since the game seemed to be running fine. It runs fine at the character selection screen, loads up into the game ok, but as soon as you load into the world, the entire computer freezes.

I'm not sure what the issue is. Do I have a setting in the game wrong? (the OpenGL line's in the config.wtf folder, tried it both with and without it.) Do I need to change a setting in Wine? Or am I lacking video drivers, or something else entirely?

Sidenote: it does the same thing to another game (Crusader) played through Wine as well.

---

### Post by lonegunman on 2009-04-22
I had the same problem with LOTRO what worked for me was turn off compiz ie select under appearance option none.
The other option I can think of is setting the video memory in the registry (usually that just makes it run choppy though and not a crash)

---

### Post by Zoquara on 2009-04-22
I tried your suggestion, and it's still crashing, but at least it's not freezing the entire system anymore.

---

### Post by lonegunman on 2009-04-22
do you have the latest driver? Is there a restricted driver available? (sorry ive never used an intel card just ati and nvidia)

---

### Post by Kidfork on 2009-04-22
> **lonegunman said:**
> do you have the latest driver? Is there a restricted driver available? (sorry ive never used an intel card just ati and nvidia)

Yes and also ensure you have the latest wine versions. If you installed it from the Ubuntu Repo's most likely you don't,
[http://www.winehq.org/download/](http://www.winehq.org/download/)

Also It would be good to list your graphics card, could be possible issues.

---

### Post by Zoquara on 2009-04-22
I have the newest Wine, but as far as drivers, I don't know. I did find a site (intellinuxgraphics.org) for them, but don't know what to download. :confused: And there aren't any restricted drivers available. :(

The graphics are integrated on an Intel 946GZ Express board.

---

### Post by Zoquara on 2009-04-23
Ok, so according to [this post]("http://ubuntuforums.org/showthread.php?t=1133945")... my problem's not the video drivers. All updates have been run. Wine's up-to-date. The game install works fine on my computer (8.04 instead of 8.10). I have Ventrilo working. I'm at a loss as to what's not functioning properly in order to play WoW. I am willing to try just about any configuration fixes if anyone can think of anything! 

 :( Why can't they just make a Linux version of World of Warcraft?

---

### Post by hikaricore on 2009-04-23
It's your video card/drivers.  It probably has very lacking OpenGL support and relies heavily on Direct3D to function in Windows.
Even with a Linux version of WoW you would probably not be able to play WoW on that card in OpenGL mode.
These intel "video" chipset are massproduced and stamped onto motherboards in the expectation that they'll be used on Windows systems.

I suggest dual booting until you get a better system or a real video card.

---

