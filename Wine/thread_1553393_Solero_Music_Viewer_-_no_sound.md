---
title: "Solero Music Viewer - no sound"
date: 2010-08-15
forum: Wine
---

### Post by Botruckle on 2010-08-15
I was able to get a copy of the Solero executable (8.0.29.370) by using my Windows computer (website won't let a Linux computer even get the exe). I transferred it to my Linux box and installed it under Wine 1.1.42, which seems to be the latest that Ubuntu has available. 

No errors, but also no sound from the program. I have the competitor program Musicnotes Player (also under Wine) and it does play scores fine through device "system default". 

Under the Solero program, I see a variety of playback devices, except instead of "system default" it shows "Inner Soft Synth". I've tried all the other devices, but no sound. 

I can't think of any other settings I could check since sound is working fine otherwise.

---

### Post by cogadh on 2010-08-15
That is most definitely not the latest available. I believe Wine 1.2 is already in the official repositories and you can get Wine 1.3.X from the [Ubuntu Wine PPA]("http://www.winehq.org/download/deb").

If updating to a more recent version of Wine doesn't fix the problem, try running the app from the terminal to get Wine's error output and post it here. It may contain messages that will lead to a cause/solution.

---

### Post by Botruckle on 2010-08-17
SOLVED
Today Update Manager installed Wine 1.2 and the Solero Music Viewer now plays the scores with sound. Yea!

However, transposing music leads to some really weird formatting of the music, to where it no longer fits on the screen and prints out the same misshapen way. But it does this in Windows also, so I can't fault Wine.

---

### Post by ecosseman on 2011-01-12
Had same problem.
Have Wine 1.2. 
Changed Wine option from Xp to Win7 ....bingo!
Thanks all, for good advice.

---

