---
title: "Jaunty/GuildWars question."
date: 2009-08-04
forum: Wine
---

### Post by xFlowx on 2009-08-04
I'm new to Ubutnu, been using it for a month. I'm close to giving up on it...

I'm an idiot. Just throwing that fact out there. I can't use this system very well, that is why I ask questions. But for the love of God, don't jump down my throat when I ask for help or posting it in the wrong place. I just found out today, less than ten minutes ago, what a sticky thread was. Now that I have that information out there, here's my question.

I want to play Guild Wars: Nightfall. And I installed it with Wine. It did install, at least I thought it did...When I tried to play it, all I got was the music and black screen with the cursor. It stayed like that for about half an hour before I had to restart my computer.

Next, I tried PlayOnLinux. Okay, it installed...it loaded...it patched...and now I've gotten past the black screen, to a lighter shade of black, almost coal. With that is the music, the cursor, and a small black square at the bottom, right-hand corner of my screen. And that is all I get.

I don't know how to force quit a program, so I have to restart every time this happens because I cannot alt+tab to a different screen.

What do I do? Lots of people say it plays flawlessly. This computer used to be a Windows Vista before it crashed and lost everything on it...

Please help me, I'm at my whits end and I'm tired of not having my games. .___.

Thanks for any help.

---

### Post by Grishka on 2009-08-04
hey buddy, what graphics card do you have? have you installed the proprietary drivers? also, what version of Wine are you using? the one from Ubuntu repos? it's a bit old, try the one from [here](http://www.winehq.org/download/deb), it's the newest one.

edit: PlayOnLinux shouldn't be necessary, in this case. just install and run with Wine. (from the right click menu, for example)

edit 2: also, check out the [howto](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194) at the Wine application database, perhaps one of the solutions given there will help.

---

### Post by xFlowx on 2009-08-04
> **Grishka said:**
> hey buddy, what graphics card do you have? have you installed the proprietary drivers? also, what version of Wine are you using? the one from Ubuntu repos? it's a bit old, try the one from [here]("http://www.winehq.org/download/deb"), it's the newest one.

edit: PlayOnLinux shouldn't be necessary, in this case. just install and run with Wine. (from the right click menu, for example)

edit 2: also, check out the [howto]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9194") at the Wine application database, perhaps one of the solutions given there will help.

Hmmm...I'm running on whatever version the website has. I don't remember D: 

I don't really know how to use Wine. I've read the stickies and all, but...bleh.
But it's almost like it's not worth it to play anymore D: The howto you provided is all glitchy. 

I think my Graphics card is...uuuhh...NVDIA? It used to work on this computer before I lost the original OS.

---

### Post by Grishka on 2009-08-04
> **xFlowx said:**
> Hmmm...I'm running on whatever version the website has. I don't remember D: 

I don't really know how to use Wine. I've read the stickies and all, but...bleh.
But it's almost like it's not worth it to play anymore D: The howto you provided is all glitchy. 

I think my Graphics card is...uuuhh...NVDIA? It used to work on this computer before I lost the original OS.

there's no special way to run Wine, you just run Windows programs with it. check that you have proper drivers installed. System/Administration/Hardware Drivers.

---

### Post by xFlowx on 2009-08-04
[B]Edit: Okay, so I enabled the driver and so it started to work. Now the only problem I am having is logging into my account. I can't get the password or account name correct...do you know how I can find a way to retrieve them? Because, whenever I try to click on the link it tells me to, the game minimizes and nothing happens. And I can still hear the music.
[/B]
> **Grishka said:**
> there's no special way to run Wine, you just run Windows programs with it. check that you have proper drivers installed. System/Administration/Hardware Drivers.


I didn't have any of the drivers enabled XD; I feel stupid.

I'm gonna see if that works! Thank you.

---

### Post by wubiubiubi on 2009-08-05
Are you using the "stable" version on the website or the developmental one? because of a regression, the developmental one will not let you install guild wars. if you get it to work in the stable version, i recommend you update to the developmental version. it runs faster, just won't let you install, so if GW is already installed, it should be fine.

---

### Post by HobbDogg on 2009-08-06
I have been struggling with Guild Wars for the last few weeks trying to get it to run properly in WINE version 1.1.26. I am running Jaunty 9.04 also. I have added these "registry" entries:

> HKEY_CURRENT_USER/Software/Wine/Direct3D
          DirectDrawRenderer     -> opengl
          Multisampling          -> enabled
          OffscreenRenderigMode  -> backbuffer
          opengl                 -> enabled
          RenderedTargetLockMode -> auto
          UseGLSL                -> disabled
          VideoMemorySize        -> 256

Also I have tried running in windowed mode. When I run the game from the terminal window I get this output:

> fixme:win:EnumDisplayDevicesW ((null),0,0x32eb30,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e228,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32dc04,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32dc94,0x00000000), stub!
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.


I have searched everywhere for answers so if there is any help it is much appreciated.

---

