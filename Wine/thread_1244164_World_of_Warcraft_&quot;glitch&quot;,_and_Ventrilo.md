---
title: "World of Warcraft &quot;glitch&quot;, and Ventrilo on Ubuntu?"
date: 2009-08-19
forum: Wine
---

### Post by Hammerfaust on 2009-08-19
So here is the deal. I've just started getting back into Linux. I'm using Ubuntu v9.04 all tweaked and configured. I got WoW working perfectly with relative ease. In fact, it works better on Linux than it ever did on Windows. My frame rates on average have doubled on Linux vs. Windows. In addition, I found a WoW Matrix version for Linux, so all my updates work and are updated. Plus it makes management and installing new ones much easier...

Anyway that said. I have one issue with WoW I've yet to fix. About 99.9% of the time, regardless of the realm, character, location in game, etc. I have a "glitch". The issue is when I move forward pressing "W". If I continue to hold down "W" I will continue to move, but it appears to stutter or lag. If I press any other button to interrupt the constant "W", the issue goes away. If I use my mouse to move (both right and left buttons/auto-run), the issue doesn't exist. This also happens on my mount, for example my flying mount will continue to move, but constant "W" results in stuttering and the wings to stop moving.

Any ideas???


My Second issue, not related to WoW directly but still related, is my issue with Ventrilo. I have Vent installed and working perfectly. I can hear others in the channel, but I cannot get a mic to work. Any ideas on how to use a mic in Ubuntu or getting it configured to work with Linux and/or Vent on Linux? Just point me in a direction if you don't know yourself.


Thanks guys,
 - Joe

---

### Post by swoll1980 on 2009-08-19
You're doing better than me. I can't even get to run over a couple frames per second. I'm requesting this be moved to the Wine forum. There should be someone there that can help you out.

---

### Post by Ameneon on 2009-08-20
As far as the mic goes, I *believe* the solution at [http://ubuntuforums.org/showthread.php?t=41737&page=38](http://ubuntuforums.org/showthread.php?t=41737&page=38) have settled it finally for me, prolly will for you as well if you have gotten the mic to work in ubuntu itself as I did.

As far as the running forward thing, I never noticed that it doesn't happen if you use the mouse to move so you're doing better than me there, but otherwise I'm experiencing the same thing myself, so I'm gathering it's a fairly common issue then, I just move a little to avoid it but it's a bit of a nuisance yes. Only happened since last patch tho (3.2).

---

### Post by alexandari on 2009-08-20
about the ventrilo - I`ve seen many solutions about ventrilo on linux and prolly the most simple one did the trick for me. I could also hear the others but I couldnt talk and sometimes the audio dissapeared. So,solution is - install **alsa-oss**
**sudo apt-get install alsa-oss** in the terminal,and then you start ventrilo by typing: **aoss wine ventrilo.exe**
try if this works :) also,there were some scripts about the CTRL (talk) button. Well you dont need them since you`r running both wow and ventrilo on wine,there is no problem with the CTRL button. works perfect (at least it did for me)

---

### Post by tinkyxiii on 2009-08-20
I had the same issue with WoW! It's caused (apparently) by the way the system registers key repeats (hold 'W' and the letter is continually entered). The easy way to fix that is go to System > Preferences > Keyboard and untick the Repeat Keys box.

---

### Post by Jimleko211 on 2009-08-20
> **tinkyxiii said:**
> I had the same issue with WoW! It's caused (apparently) by the way the system registers key repeats (hold 'W' and the letter is continually entered). The easy way to fix that is go to System > Preferences > Keyboard and untick the Repeat Keys box.
Thank you so much!  That glitch drove me crazy!

---

### Post by Brebs on 2009-08-20
It's a bug in [xorg-server](http://bugs.freedesktop.org/show_bug.cgi?id=22515), rather than [wine](http://bugs.winehq.org/show_bug.cgi?id=18885).

---

