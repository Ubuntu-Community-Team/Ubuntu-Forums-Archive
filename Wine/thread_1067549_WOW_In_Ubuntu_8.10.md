---
title: "WOW In Ubuntu 8.10"
date: 2009-02-12
forum: Wine
---

### Post by Matsuri on 2009-02-12
I understand that it is possible to run WOW under WINE. Anyone know of a good tutorial to get it working for the latest and greatest from Ubuntu?

My computer is dual booted with Windows XP and Ubuntu 8.10. I can run WOW in XP obviously, but having to constantly reboot is something I don't want to keep doing. I'd rather run it in windows than WINE, is there a way I can like boot both systems and play the game in windows but quickly / instantaneously change to linux when I'm done?

I know this may be a far fetched request but I'm not totally up to date on everything available for linux. I don't care how command line intensive any tutorials are, I have a good grasp of it.

Thanks in advance,
Matsuri

---

### Post by asheq on 2009-02-12
not sure how deep this tut goes into explanation
but here
[http://www.wowwiki.com/Wine](http://www.wowwiki.com/Wine)

I've been needing to try it to.

this one is outdated, but maybe it's a base to get started
[http://ubuntuforums.org/showthread.php?t=120615](http://ubuntuforums.org/showthread.php?t=120615)

---

### Post by JK3mp on 2009-02-12
Have you tried virtualbox or VMWARE? Run windows inside linux or vice versa..

---

### Post by asheq on 2009-02-12
Are they freeware?
Or do you have to pay for those? >.>

---

### Post by binbash on 2009-02-12
wrong forum

---

### Post by Matsuri on 2009-02-12
I don't think trying to virtualize a system and then trying to run a game in it is going to work. I've thought about that option, it is completely free but I think it would be too slow.

Anyone try Cedega lately? Any luck with WOW and Cedega?

---

### Post by Matsuri on 2009-02-12
Here is the scoop, move this thread to the right location or where ever it needs to go. I didn't know the best place, maybe you do. Don't just say wrong forum.

I got WOW running on my laptop. My specs:

Dell Vostro 1510
Ubuntu 8.10 Intrepid Ibex
2.1 gHz dual core
nVidia GeForce 8400MS

To get WOW running under Ubuntu 8.10 make sure that you have the proper version of wine installed. The stable package is wine-1.0.1 however, this is not the package you want. Goto the [http://www.winehq.com](http://www.winehq.com) and get the latest development package they offer. wine-1.1.14

As the guide posted earlier stated make sure you have Direct Rendering enabled. If you already have WOW installing on a windows partition, simply move the folder to your linux home partition.

To Play:
```

cd "/home/user/World of Warcraft"
wine Wow.exe -opengl

```

This will allow you to play WOW and not have it crash when you click play on the launcher screen. 

To add launcher:
[LIST]Right mouse click on desktop and select Add Launcher[/LIST]
[LIST]Title it World of Warcraft or whatever you please[/LIST]
[LIST]Command: wine "/home/user/World of Warcraft/Wow.exe" -opengl
[/LIST]

If you don't have WOW installing on a windows partition, goto: [http://www.wowwiki.com/Wine](http://www.wowwiki.com/Wine) as was stated earlier. You can also download an EXE from Blizzard that allows you to download and install WOW and all the expansions right from the website. I don't know much about these other methods as I already had wow installed.

Need help, just message me or something and I'll offer what little knowledge I have on the subject.

-Matsuri

---

### Post by Ammet on 2009-02-12
Are you noticing low frame rates running WoW via Wine?

Personally have XP at home currently and have been really itching to make the full switch to Ubuntu, but I'm fearful that I won't be able to fully enjoy my biggest time sink. Have just read several places where people running WoW in Wine experience less that ideal frame rates most of the time and this is making me a bit nervous to make the switch...

---

### Post by Matsuri on 2009-02-12
I will be able to tell you more tonight when I try playing it. But no, I did not notice any low frame rates.

I logged onto to my account, all of the animations for the login screens ran fast. Upon logging into my characters, on Durotan server, medium load in Org. I had no lag and good frame rate. I'll give you more when I get online tonight when the real load comes from me actually playing and more people being online.

---

### Post by Ammet on 2009-02-12
> **Matsuri said:**
> I will be able to tell you more tonight when I try playing it. But no, I did not notice any low frame rates.

I logged onto to my account, all of the animations for the login screens ran fast. Upon logging into my characters, on Durotan server, medium load in Org. I had no lag and good frame rate. I'll give you more when I get online tonight when the real load comes from me actually playing and more people being online.

Great! I look forward to hearing how it goes! I just kept reading posts of nothing higher than 15 fps and so on. I've gotta have my 80+. :) Thank you!!

---

### Post by Matsuri on 2009-02-14
K, played WOW last night to test out how everything runs. I have graphics set to high, using 1680x1500 screen resolution. Everything runs fine, ran through some dungeons with people and it almost runs better than how it runs in windows. I've no problem with frame rates or lag or anything.

Matsuri

---

### Post by Ammet on 2009-02-17
> **Matsuri said:**
> K, played WOW last night to test out how everything runs. I have graphics set to high, using 1680x1500 screen resolution. Everything runs fine, ran through some dungeons with people and it almost runs better than how it runs in windows. I've no problem with frame rates or lag or anything.

Matsuri

Great! Thanks for the encouraging report back! Thinking about getting a new hard drive today so I can start cleanly with Ubuntu and WoW and that's about it. :)

---

### Post by Matsuri on 2009-02-18
Just to let you guys know, I'm working on getting Ventrilo to work under linux as well. It is kind of annoying to have to type messages. I can get vent installed under wine and can hear anyone speaking but I'm having trouble getting the speaking half to work.

I've tried doing a fix for the client side and it doesn't seem to work. I think the server is going to have to have speex installed on it. I'll post when I know more about it.

---

### Post by fireflake on 2009-02-19
I recently wrote a small "review" of different OS setups for WoW on my home pc. It's a single case scenario but might interest you how this worked for me:

[http://www.fireflake.com/game/2009/02/19/wine-windows-warcraft/]("http://www.fireflake.com/game/2009/02/19/wine-windows-warcraft/")

The short version: if you want to play Warcraft with best performance, stick to WinXP. Wine works but leaves alot of things to wish for.

I'd recommend dual boot, I can still play WoW under Wine but if I go to some instance or raid I reboot to Windows to get better performance.

---

### Post by kenaro on 2009-02-19
> **Matsuri said:**
> Here is the scoop, move this thread to the right location or where ever it needs to go. I didn't know the best place, maybe you do. Don't just say wrong forum.

I got WOW running on my laptop. My specs:

Dell Vostro 1510
Ubuntu 8.10 Intrepid Ibex
2.1 gHz dual core
nVidia GeForce 8400MS

To get WOW running under Ubuntu 8.10 make sure that you have the proper version of wine installed. The stable package is wine-1.0.1 however, this is not the package you want. Goto the [http://www.winehq.com](http://www.winehq.com) and get the latest development package they offer. wine-1.1.14

As the guide posted earlier stated make sure you have Direct Rendering enabled. If you already have WOW installing on a windows partition, simply move the folder to your linux home partition.

To Play:
```

cd "/home/user/World of Warcraft"
wine Wow.exe -opengl

```

This will allow you to play WOW and not have it crash when you click play on the launcher screen. 

To add launcher:
[LIST]Right mouse click on desktop and select Add Launcher[/LIST]
[LIST]Title it World of Warcraft or whatever you please[/LIST]
[LIST]Command: wine "/home/user/World of Warcraft/Wow.exe" -opengl
[/LIST]

If you don't have WOW installing on a windows partition, goto: [http://www.wowwiki.com/Wine](http://www.wowwiki.com/Wine) as was stated earlier. You can also download an EXE from Blizzard that allows you to download and install WOW and all the expansions right from the website. I don't know much about these other methods as I already had wow installed.

Need help, just message me or something and I'll offer what little knowledge I have on the subject.

-Matsuri

So. This did *not* work. Caused a massive screen-scramble and then a black-screen crash.

---

### Post by CamF on 2009-02-19
Hi.  I'm new to Ubuntu, having committed computer heresy and renounced my faith in the church of Microsoft this past weekend.  My problem is that I can't get WoW to even start installing.

System specs are:
Ubuntu version 8.1 (intrepid)
Kernel Linux 2.6.27-11-generic
GNOME 2.24.1

749.0 MB memory
AMD Athlon 64 processor 3500+

Wine Version 1.1.15

I've moved all of the DVD contents to my desktop, unhidden the installer and downloaded and unzipped the recommended DLLs. 

Here's what Wine gives me:

cam@cam-desktop:~/Desktop/wowinstall$ wine Installer.exe
cam@cam-desktop:~/Desktop/wowinstall$ fixme:ole:OleCreateStaticFromData (not shown), stub

What am I missing here?

FIXED... WOOHOO!

---

### Post by Matsuri on 2009-02-19
> **kenaro said:**
> So. This did *not* work. Caused a massive screen-scramble and then a black-screen crash.

What is your graphics card? I'm running nVidia obviously. ATI has its own set of problems. You might also have to make sure that you opengl is installed and up to date. Also could if be your limited memory? Remember that your basically emulating windows, trying to run the game and all the graphics is kind of demanding.

---

### Post by CamF on 2009-02-21
> **CamF said:**
> Hi.  I'm new to Ubuntu, having committed computer heresy and renounced my faith in the church of Microsoft this past weekend.
... etc ...
What am I missing here?

FIXED... WOOHOO!


So here's what happened.  Re-copied my DVD to a new folder on my desktop.  No luck.  Went to Blizzard and used their downloader here:

[https://signup.worldofwarcraft.com/trial/index.html;jsessionid=8299E582E4A74DC38439483082644126.app24_01]("https://signup.worldofwarcraft.com/trial/index.html;jsessionid=8299E582E4A74DC38439483082644126.app24_01")

Download and install went smoothly, all of the patches installed without any fuss and the game started, logged in and ran.  For about 3 minutes.  Then the whole world went weird, scrambled eggs looking.  
Hell and damnation!
Shut it down and restarted it with no improvement.  3 times.
Then went here:

[http://ubuntuforums.org/showthread.php?t=12061]("http://ubuntuforums.org/showthread.php?t=12061")

and did this:
[I]
WORLD OF WARCRAFT SETUP

Ok, wine is now ready for WoW. If you do not have a working copy of WoW available, and need to install, your best bet is to copy all of the contents of every CD into a directory on your hardrive, and start the installer using wine. I haven't tested this myself.

Once you have installed WoW, the /World of Warcraft/wtf/Config.wtf file needs to be modified. Add the following lines:
SET gxApi "opengl"
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxColorBits "24"
SET gxDepthBits "24"

You should also add in the following two lines, but fill in values for the screen resolution and vertical refresh rate that are right for your setup. Mine were:
SET gxResolution "1280x1024"
SET gxRefresh "85"

Ok, now to run, you can type 'wine WoW.exe -opengl' in a terminal.[/I]

Except that I started WoW by double clicking on the desktop icon.
HOLY CRAP IT WORKS!

Here's the cool part.  Running it under Win XP I had the resolution set at 800x600 and got 12 fps max.  Usually more like 5 to 8 fps.  Some places as low as 2 or 3 fps.  Like at the Undercity zep tower.

Now running under Wine under Ubuntu I have 1024x768 resolution and 11 to 20 fps. 
Whoa... The (WoW) world is a beautiful place...
I love the whole (WoW) world! 
BOOMDIADA!  \\:D/
(google it if you don't know wtf boomdiada is)

Not sure I could answer any questions about how I done it, but I done it YAY! so ask away anyway.

---

### Post by uns3r on 2009-03-03
> **Matsuri said:**
> Here is the scoop, move this thread to the right location or where ever it needs to go. I didn't know the best place, maybe you do. Don't just say wrong forum.

I got WOW running on my laptop. My specs:

Dell Vostro 1510
Ubuntu 8.10 Intrepid Ibex
2.1 gHz dual core
nVidia GeForce 8400MS

To get WOW running under Ubuntu 8.10 make sure that you have the proper version of wine installed. The stable package is wine-1.0.1 however, this is not the package you want. Goto the [http://www.winehq.com](http://www.winehq.com) and get the latest development package they offer. wine-1.1.14

As the guide posted earlier stated make sure you have Direct Rendering enabled. If you already have WOW installing on a windows partition, simply move the folder to your linux home partition.

To Play:
```

cd "/home/user/World of Warcraft"
wine Wow.exe -opengl

```

This will allow you to play WOW and not have it crash when you click play on the launcher screen. 

To add launcher:
[LIST]Right mouse click on desktop and select Add Launcher[/LIST]
[LIST]Title it World of Warcraft or whatever you please[/LIST]
[LIST]Command: wine "/home/user/World of Warcraft/Wow.exe" -opengl
[/LIST]

If you don't have WOW installing on a windows partition, goto: [http://www.wowwiki.com/Wine](http://www.wowwiki.com/Wine) as was stated earlier. You can also download an EXE from Blizzard that allows you to download and install WOW and all the expansions right from the website. I don't know much about these other methods as I already had wow installed.

Need help, just message me or something and I'll offer what little knowledge I have on the subject.

-Matsuri

well I did this it came to a black screen then it loaded i thought it was going to crash but then it starts to go and everything is working then it crashes right as i get to the log in screen. i have been able to do the first bit of updates to

edited part
i forgot to put that the launcher thing you were saying to do did not work for me either

---

