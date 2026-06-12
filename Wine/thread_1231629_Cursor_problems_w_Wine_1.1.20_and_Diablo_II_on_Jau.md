---
title: "Cursor problems w/ Wine 1.1.20 and Diablo II on Jaunty"
date: 2009-08-04
forum: Wine
---

### Post by rokstaEnSweden on 2009-08-04
Hey guys,

So after spending the better half of yesterday with Diablo II I finally got it installed through Wine and running. But now I'm having some really odd problems with the cursor while running the game in DirectDraw.

I followed the guides located [here]("http://art.ubuntuforums.org/showthread.php?t=362457") and at the [WineHQ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=49") to get the installation up and going. No real problems except that I had to download something called the 3D Glide Wrapper to get the graphics to work properly. The downside is that the game seems laggy in the 3D Glide mode which can be selected from the video test included with Diablo 2.

SO, I switched it to Direct Draw to try to reduce the lag, but then I ran into this cursor problem. For some weird reason the game screen will display fine, but I can only move my cursor around in a small boxed area within the game screen. It's hard to explain, but it's like the window displaying the game thinks the area for the cursor to interact with the game is smaller than the window. This leads me to be unable to select options lower than the last 1/6th of the game screen or move my cursor over to the last 1/6th of the right-hand side of the game screen. When the cursor goes out of the imaginary boundary, it just reverts back to the desktop mouse despite still being inside of the game screen.

Weird problem, huh? I was messing with the resolution for emulating a virtual desktop through Wine but it didn't seem to have much effect on the cursor problem. Any suggestions you guys could give me would be great because I'm on the verge of throwing in the towel. While combing the forums I noticed [this guy ]("http://art.ubuntuforums.org/showthread.php?t=1229499")is having the same problem, but there was no solution.

**SOLVED: So after being a complete newb and trying from every possible angle to get this problem fixed, I gave up. But only for 30 minutes, because I realized that I had in fact edited the DirectDraw .dll file in order to get Diablo I working early in the week. A simple download and replacement of the ddraw.dll file in the Wine system32 directory fixed the cursor problem. Now the only problem is being annoyed with having to swap ddraw.dll files when I want to switch between Diablo 1 and 2. Totally lame. Anyone have a solution to that one?**

---

