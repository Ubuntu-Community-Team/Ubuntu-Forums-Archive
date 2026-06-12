---
title: "Games/Graphics"
date: 2010-04-20
forum: System76 Support
---

### Post by Bluebearbevis on 2010-04-20
Hello Everyone,

I am having huge trouble with graphics? in any game I install on my Pangolin (T4200's, 2G ram, Nvidia G105M.  The only game that runs in windowed mode at 1366x691 (my screen is 1366x768) is Battle for Westnoth and somehow this magically happened.  Some games I can run full screen or at a lower resolution like Scorched3d, but not at max. res. windowed mode as the bottom of the window drops off the screen.  If that makes sense?  Much worse and now with Nexius and Alien Arena, when I start the game from apps etc...first a black screen appears which is slowly invaded from the upper left by a bank of white fog that descends about 2/3 of the way down the screen and 1/4 out along the top curving concavely between the points.  This is followed by a purple haze (I'm serious) that only comes out from the same corner a few and a couple inches, same curve.  All while the audio plays.  Is there a better solution than closing the cover and uninstalling the program after restart?  I have the System76 driver installed and the xorg.conf email attachment you sent me Tom...?

Thanks,
Richard

P.S.  For some reason this "thing" keeps changing my 8) in ...x768) to a cool dude, anyway...

 P.S.S. It's a conspiracy, the "eight apostrophe" in my edit got changed to a cool dude too...

Hi again,

I installed Criticalmass and the game opened full screen mode at a very small resolution (don't remember exactly) giving me 6 windows on one screen like when I reinstalled 9.10 and before I added Tom's xorg.conf file.  I have the game configured now to run in windowed mode at the largest resolution possible before the bottom falls out (960x720.)  However, when I clicked the full screen option, blamo, the white fog/purple haze.  Fortunately,  Criticalmass seems to default to windowed mode at last selected resolution.  I'm wondering if some of these other programs are trying to open in full screen mode at a high resolution?  Any help and/or moral support appreciated.  Thanks.  Oh yes, I'm running the 64bit version of Karmic.

Richard

---

### Post by thomasaaron on 2010-04-21
Do you have your nVidia driver installed (System > Admin > Hardware Drivers)?

Do the games run better if you turn of desktop effects? (System > Prefs > Appearance > Visual Effects > None)?

---

### Post by Derath on 2010-04-21
I'm also thinking that the resolution you've specified is a little on the "odd" side... I have a panp4n runnin 1680x1050 and haven't had a problem with any game running full-screen or windowed, if you want windowed mode you also have to check the video settings in the game (i,e. running 1360x768 and the game is defaulted windowed video to 1280x1024, then the lower part won't display properly). Full screen mode should change the screen resolution automatically...

So my first bit of advice would be to check the video resolutions in each game, or in their config files (~/.game) and see if you can set them to either 800x600 or 1024x768, if you're using the 1360x768 for your desktop, I'd go with the 800x600 for all windowed modes.

---

### Post by Bluebearbevis on 2010-04-21
Good Evening,

Tom, yes and no.  Derath, I'm not sure what you mean by odd. "System Profiler and Benchmark" says my Display Resolution is 1366x768 and my Monitor is 1366x768.  Nvidia X Server Settings > Display Configuration auto detects my Display as DFP-0, 1366x768.  Some games work some don't, there doesn't appear to be any consistency.  Any game that you select a resolution ...x768 falls off the bottom of the monitor.  With the given choices, the resolution that works is 960x600, like I said, 1366x691 magically appeared in Battle for Wesnoth because it wasn't in the original list of options.  What more information can I give?  Thanks for your replies,

Richard

---

### Post by thomasaaron on 2010-04-22
Whew. I'm not a big fan of either of those games. Are there any 76ers out there who are familiar with the settings for these games?

---

