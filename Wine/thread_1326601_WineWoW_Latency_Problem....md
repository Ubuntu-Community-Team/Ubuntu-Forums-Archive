---
title: "Wine/WoW Latency Problem..."
date: 2009-11-14
forum: Wine
---

### Post by geektanic on 2009-11-14
Been using Ubuntu for years now but have battled between Windows and Linux for game support for a large part of it. After hearing good things about 9.10 I decided to make the final choice for linux and now I've come to nearly regret it entirely. While all my games (Fallout, CoD4, WoW) have installed and run fine with exceptionally higher framerates I am having **severe** latency issues that only appear to be affecting WoW as it's the only one I play online. 

The game ran consistently well in 9.04 with framerates ranging from 70 FPS to 120 FPS on a regular basis and absolutely no issue with stability. 
Now in 9.10 I'm averaging 50 FPS and my latency is near guaranteed to exceed 1500 at all times. Sometimes as high as 3000
More so it only seems to be affecting my side as I can see other people move and chat real time, NPC's react as they always do however anything I do seems to take anywhere from 30 seconds to indefinite before I just get D/C'd from the game.

What confuses me is if I check my process manager I have little to no network activity taking place. It may be sheer coincidence but using the web browser to rapidly ping websites actually seems ti give me burst moments of strong connectivity.

After reading about other people having issues with IPv6 I disabled that in both GRUB and /etc/sysctl.conf in a ditch effort to get some immediate resolution but it made no difference.

I first blamed wine 1.1.32 but after downgrading to 1.1.28 (used in 9.04) it remains a problem.
I am working on a quad-core system 2.8 Ghz with 8 Gb of ram and 1 TB of main storage
I am running Ubuntu 64 bit with a 32 bit compiled version of Wine
I have disabled UFW fearing it may be the cause with no change in affect

Does anyone have any idea or am I stuck giving up a passion to settle for functionality?

---

### Post by geektanic on 2009-11-14
See:
[http://ubuntuforums.org/showthread.php?t=1317242](http://ubuntuforums.org/showthread.php?t=1317242)

For anyone else that appears to have this issue you can either use OpenDNS or follow suit by looking up your own DNS servers through your router to resolve this issue.



EDIT:
I take that back the fix was only momentary and eventually the problem returned. My wife runs a windows box directly beside mine that plays without issue so I know it's not ISP related. I'll miss you Ubuntu but let's face it, by the time you fix one issue you make another worse tenfold.

---

