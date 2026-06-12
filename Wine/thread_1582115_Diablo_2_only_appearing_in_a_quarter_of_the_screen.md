---
title: "Diablo 2 only appearing in a quarter of the screen."
date: 2010-09-26
forum: Wine
---

### Post by Zanderist on 2010-09-26
So I've gotten diablo 2 to install and work.

What happened was that I wasn't getting any sound in game and I changed some of the settings in wine (forget which now). And now diablo2 (lod) only appears in the second quadrant of the window. (where cos(x) is negative and sin(x) is positive)

Also the apply cancel button in wine config, have gone transparent, meaning I can see everything but those buttons (which have been replaced by my current back round).

How can I fix this?

---

### Post by castlefox on 2010-09-26
Please provide more info on your hardware and version of wine you are using.

---

### Post by Zanderist on 2010-09-26
I have wine version

1.1.42

And it's nothing to do with the hardware since this game does work on windows, and just before I tried figuring out what was wrong with the sound I was able to see the full window.

Belay my last, it's working.

This thread is now about not having in game sound for diablo 2.

Alright, never mind I've just fixed it.

---

### Post by Fafler on 2010-09-27
So, how did you fix it? My sound disappears after a few minutes gameplay. Havent really looked into it, as i only use my laptop for muling anyway, but a fix would be nice ;-)

---

### Post by ShadowMage on 2010-09-27
Hi,

I had the same sound problem, where the sound would disappear once I entered a game. Check out this thread for the solution that worked for me for the sound problem: [http://ubuntuforums.org/showthread.php?t=1534466](http://ubuntuforums.org/showthread.php?t=1534466)

Hope this helps.

---

### Post by Zanderist on 2011-03-22
Let me give you an update, the sound problem is easy. 

Just use ALSA sound in the config at least that worked for me.

Now for the next part, if you haven't gone into additional drivers and activated your graphics driver then you will not be able to use a fullscreen, an easy work around for this. Is create a shortcut of diablo 2 on your ubuntu desktop but add -w at the end of the target line like so

> "/host/Program Files (x86)/Diablo II/Diablo II.exe"  -w

Please note: I'm on a wubi install and I am using the Diablo II on my windows partition, instead on my ubuntu partition just to conserve space.

This will let you play it windowed and you shouldn't have any problems.

When I play in fullscreen the game tends to lag if there is a lot going on in the game. This isn't the case when I boot into my windows and play it.

---

