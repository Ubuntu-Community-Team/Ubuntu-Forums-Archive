---
title: "World of warcraft and"
date: 2011-05-03
forum: Wine
---

### Post by linisth on 2011-05-03
Hello, I'm trying to run World of Warcraft on my Ubuntu 11.04 Laptop. I looked online for some help, and they all prety much say the same thing, I get to run the Launcher and the Wow.exe but when i get to the login screen the whole screen goes crazy, like if it had a faulty video card or something, I can hear the music and the sound effects, but the video is all screwed up. Here's one of my many sources on what I've done: 

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Here's my laptops specs:

Intel i5 2.6 Quad Core
6 GB Ram
1 GB Dedicated DDR5 graphics card (ATI Mobility Radeon HD 5730)

I've played wow on linux before, I want to do it again, can someone else please help me? 

Thanks in advance.

---

### Post by Pluxii on 2011-05-03
I use play on linux personally and it works like a dream.
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)
Pretty much walks you through everything.

---

### Post by cwwilson721 on 2011-05-04
Have/are you running:
[LIST]
[*]The latest proprietary drivers from Ubuntu?
[*]Compiz? (Turn it off)
[*]In OpenGL mode? (Just add '-opengl' at the end of the launcher)
[*]The latest wine 1.3? (Look at the wine homepage, or search this forum on how to get/install it)
[/LIST]

This is the basics.

And NO, you DON'T need to use Play On Linux (POL). WoW runs perfectly fine on wine 1.3 without the added 'complexity layers' of POL. Install wine 1.3, install WoW, add your addons, and away you go. Using POL just adds one more 'cook to the pot' that can make troubleshooting an issue VERY difficult.

---

### Post by _outlawed_ on 2011-05-04
> **cwwilson721 said:**
> Have/are you running:
[LIST]
[*]The latest proprietary drivers from Ubuntu?
[*]Compiz? (Turn it off)
[*]In OpenGL mode? (Just add '-opengl' at the end of the launcher)
[*]The latest wine 1.3? (Look at the wine homepage, or search this forum on how to get/install it)
[/LIST]

This is the basics.

And NO, you DON'T need to use Play On Linux (POL). WoW runs perfectly fine on wine 1.3 without the added 'complexity layers' of POL. Install wine 1.3, install WoW, add your addons, and away you go. Using POL just adds one more 'cook to the pot' that can make troubleshooting an issue VERY difficult.

I would also suggest:

1. Trying out the open source drivers (if applicable) and proprietary drivers to see which works best.
2. You can also set OpenGL mode with config.wtf by adding this line:

```
set gxApi "OpenGL"
```

3. I would recommend trying the latest stable 1.2 version of Wine first, since the beta 1.3 does run the risk of regressions from build to build.

---

### Post by cwwilson721 on 2011-05-05
WoW now "automagically' adds the relevant line in the Config.wtf file when you run the command with '-opengl' appended (at least since 4.0 came out), so no need to manually edit for that particular issue.

wine 1.3 runs WoW best, even better then 1.2, especially for video issues. Always try to run 1.3 first. WoW regressions are so few and far between now, and if they DO happen, the wine devs fix them VERY quickly (WoW is one of the top apps run under wine. I can't blame the devs for quick fixes just for WoW)

USE OF PROPRIETARY DRIVERS IS ALMOST A MUST! Otherwise, your FPS drops and graphical glitches will be even more evident. The opensource drivers, while making better and better progress, are nowhere near the level of the proprietary drivers in OpenGL 3D. In 2D (regular apps, not graphic games) they are very close. I applaud the strides they are making in 3D, but a game like WoW, or for that matter, any game that has even higher requirements for 3D video, needs the Linux proprietary drivers for their respective cards, if available. Have you ever tried to run WoW in Windows using the VESA drivers? Good luck. The same basic concept holds true here, at least for the forseeable future.

If proprietary drivers are not available for your card/chip, then use the opensource (You hear that, Intel users? WoW still is not really 'playable'with older non-Sandy Bridge Intel chips, and since Sandy Bridge still hasn't really hit the market in big enough numbers, the jury is still out on them...).

So, to summarize ALL installs of WoW running in wine:
[LIST]
[*]Use wine 1.3
[*]Disable Compiz (It can/does/will cause issues/glitches. Use the fusion-icon to disable Compiz before firing up WoW)
[*]If you want reliable sound in WoW/wine, use XP mode. No idea why, but it seems to work the easiest. If you need other apps to share sound at the same time, install the Pulse Audio enabled wine versions, available in different repos. Google it
[*]Append '-opengl' to the end of the Launcher command.
[*]Install the proprietary drivers for your videocard/chip, if available.
[*]If you need a Vent client, use Mangler. It's a Linux vent client that WORKS. Forget trying to install Ventrilo in wine and all the headaches that come with it.
[/LIST]

Dang, this got quite a bit longer than I thought it would. But if you follow the bullet points above, 95% of any issues will be taken care of, and WoW/wine will run as reliably as you can make it. There may be other issues, but most of those have to do with individual hardware, settings, sound cards, etc.

And, don't forget the NUMBER ONE RULE!

HAVE FUN!

---

