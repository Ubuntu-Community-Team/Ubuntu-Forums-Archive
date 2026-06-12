---
title: "Black Box around cursor in WoW and SC2"
date: 2011-05-11
forum: Wine
---

### Post by brometheus on 2011-05-11
So I've successfully got World of Warcraft and Starcraft 2 up and running on my new 11.04 Natty install, I'm using the NVIDIA-Linux-x86-270.41.06 proprietary video driver, and wine 1.2.2.

Things are running smooth, I get good framerate and latency, models and animations are all working like they should, but the issue I'm having is this annoying black box around the cursor. It doesn't seem to interfere with the pointer's function, but it does obscure whats underneath.

I was able to load warcraft without the glitchy cursor after installing the experimental nouveau drivers- but the game barely ran, and Unity would not load.

Any Ideas? is this simple noob missing something obvious?

---

### Post by cwwilson721 on 2011-05-11
A few things right off the bat:

[LIST]
[*]Are you running Compiz? TURN IT OFF. (Search the forum)
[*]Are you running in opengl mode? (Add '-opengl' to end of launcher command, or edit the config.wtf file. Search the forum)
[/LIST]
Those are the 2 main culprits.

---

### Post by brometheus on 2011-05-12
So, Compiz is definitely disabled, although it doesn't seem to effect it either way- and yeah I'm running in opengl mode.

In fact, if I run the game in dx9 mode, with hardware cursor turned off, the glitch does not appear, but I get drastically reduced fps and an unplayable amount of mouse lag.


Strangest thing is, the problem disappeared for a short time while playing Warcraft the other night. I've got no clue what may have triggered it, certainly nothing I did (I had given up) and I could not reproduce it- but, for about 30 minutes, it was working fine. :confused:

I'm convinced now that the problem lies the recent implementation of opengl hardware cursor support, and something in my video drivers ability to handle it. 

Can anyone suggest a better driver for me? nvidia 9800gt (2 of 'em actually but currently only using 1 due to TwinView limitations)

---

### Post by brometheus on 2011-05-12
Minutes after the last update I actually figured it out-- 

[http://bugs.winehq.org/show_bug.cgi?id=25293](http://bugs.winehq.org/show_bug.cgi?id=25293)

describes the problem I was having, and solution to it :)

---

### Post by cwwilson721 on 2011-05-12
Think of this as 'lesson learned'. Almost as much of a wakeup call as Windows viruses trashing your C: drive. There is an 'easy' fix.

You installed some other program besides WoW and SC2, and it borked your wine/WoW install. Don't do it. WoW runs fine all by itself. Not sure about SC2.

You need to start using the 'env WINEPREFIX' variable to launch your wine apps, so that doesn't happen.

Example: For me to launch WoW, I use the following command-
```
env WINEPREFIX="/home/<USERNAME>/.wine-wow" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
```

All my 'wine apps' have separate folders to run in.

I don't actually have ANYTHING installed to the default '.wine' folder. I rename my 'want to run wine here' folder to '.wine' (or create a shortcut to where I want the particular program to install) for this, then rename back.

Notice that WoW is installed in it's own 'wine folder'. I do that to stop windows programs from messing with my WoW install.

I also have a 'clean install' of wine/WoW on a separate HDD. I do this by running 'winecfg', auto install 'gecko', then run the WoW installer from the latest DVD, then run the patches I have saved on other media. Every time there is an update to WoW, or wine, for that matter, I first run the 'play install' of WoW, making sure it works, then run the 'clean install' WoW/wine, just so I always have a 'clean', updated, and tested working copy. There are no Addons installed to this 'clean' version, just to eliminate variables. I keep d/l's of the addon .zip files on separate media, too.
Example:

```
env WINEPREFIX="/wowback/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
``` The above is my 'clean install' launcher command. Note the different 'env WINEPREFIX=' variables. This allows me to run different wine programs without the various programs 'mixing DNA', as it were.

This way, if I run into MAJOR issues with my 'play install' of WoW, it takes 5 min to delete the 'wine-wow' folder and then copy the 'clean backup' to wine-wow. Heck of a alot shorter than the 1-2 hours that a new install could take.

The 'clean install' also let me check on the link you posted earlier, and there is NO registry entry as described in the link. Thus, you have something besides WoW installed there.

Note: All of the above was learned the hard way. I've been running wine/WoW since Vanilla, and I've messed up the install many, many, many times by installing other apps, addons, IE versions, among countless other things. Vent killed me once, so I no longer use Vent, but Mangler instead.

What I have done may not work for you, but since I have 3 500GB SATAII drives in my box, I have the room to have non-compressed 'backups'

Good luck. And happy questing.

---

