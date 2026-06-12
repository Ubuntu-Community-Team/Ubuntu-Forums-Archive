---
title: "Starcraft 2 Crashes after loading"
date: 2010-07-29
forum: Wine
---

### Post by glad. on 2010-07-29
Hey all, sorry if this is the wrong place to post this but it seemed like the best spot (I'm a newbie when it comes to linux, so I wasn't sure if I should post it in the beginners forum...)

Anyway I just got SC2 retail, and got it to install, download the patch, etc. As soon as it loads, though, it immediately crashes with the following error message: 

e_gfxGraphicsAPIError
"StarCraft II has encountered an unexpected DirectX/OpenGL error. This may indicate an issue with an out-of-date videocard driver. If the problem persists, for more information consult our support website at http://starcraft2.com/support."
Error code: D3DERR_INVALIDCALL (8876086C) 


And an option to send this data to blizzard, etc (the message is actually quite a bit longer than this--pages long, in fact--but this is the main stuff). 

Now this has me a little worried, because I'm just running my laptop with integrated graphics-- "VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)". But I would expect the game to at least be able to barely run, not crash immediately upon opening. 
As far as I know, my drivers are up-to-date, although I admit I'm not 100% sure how to check that. 

Last piece of info--after crashing, the resolution on my screen has been changed, and it looks a little crummy and I have to change it back to the old resolution. Whether that would happen if it didn't crash, and I just exited out of SC2 cleanly, I don't know, since I can't get to that point.

Any help would be greatly appreciated. Thanks.

---

### Post by asdfoo on 2010-07-30
> **glad. said:**
> Hey all, sorry if this is the wrong place to post this but it seemed like the best spot (I'm a newbie when it comes to linux, so I wasn't sure if I should post it in the beginners forum...)

Anyway I just got SC2 retail, and got it to install, download the patch, etc. As soon as it loads, though, it immediately crashes with the following error message: 

e_gfxGraphicsAPIError
"StarCraft II has encountered an unexpected DirectX/OpenGL error. This may indicate an issue with an out-of-date videocard driver. If the problem persists, for more information consult our support website at http://starcraft2.com/support."
Error code: D3DERR_INVALIDCALL (8876086C) 


And an option to send this data to blizzard, etc (the message is actually quite a bit longer than this--pages long, in fact--but this is the main stuff). 

Now this has me a little worried, because I'm just running my laptop with integrated graphics-- "VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)". But I would expect the game to at least be able to barely run, not crash immediately upon opening. 
As far as I know, my drivers are up-to-date, although I admit I'm not 100% sure how to check that. 

Last piece of info--after crashing, the resolution on my screen has been changed, and it looks a little crummy and I have to change it back to the old resolution. Whether that would happen if it didn't crash, and I just exited out of SC2 cleanly, I don't know, since I can't get to that point.

Any help would be greatly appreciated. Thanks.

I don't think your video card meets the minimum requirements under Windows:

128 MB PCIe NVIDIA® GeForce® 6600 GT or ATI Radeon® 9800 PRO video card or better


The only thing I can suggest is trying the bleeding edge stuff for intel setups which is available under ubuntu-edgers.

---

### Post by glad. on 2010-07-31
Thank you for your advice. However, I know multiple people who have this same card who have played the game (even played it well). I should be able to at least *load* the game, even if it's slow enough that it's unplayable. So it's hard for me to imagine that I can't even load the game just because my card is bad--it must have something to do with DirectX, or my drivers, right?

---

### Post by beastrace91 on 2010-07-31
> **glad. said:**
> Thank you for your advice. However, I know multiple people who have this same card who have played the game (even played it well). I should be able to at least *load* the game, even if it's slow enough that it's unplayable. So it's hard for me to imagine that I can't even load the game just because my card is bad--it must have something to do with DirectX, or my drivers, right?

Intel Linux drivers tend to produce unstable results when running 3d through Wine. If you want to game on Linux using Wine buy nVidia.

~Jeff

---

### Post by glad. on 2010-07-31
> **beastrace91 said:**
> Intel Linux drivers tend to produce unstable results when running 3d through Wine. If you want to game on Linux using Wine buy nVidia.

~Jeff
Dang... Is there anything I can do other than switching graphics cards? I'm using a laptop and (for me, anyway) that would basically entail buying a new computer. For what it's worth, running glxgears typically gives me an FPS that isn't bad from my understanding (~10k) so my card should be decent enough at 3d. Is there any way to give better results through WINE?

---

### Post by asdfoo on 2010-07-31
> **glad. said:**
> Dang... Is there anything I can do other than switching graphics cards? 

You can read my post again and follow the suggestion there.

---

### Post by glad. on 2010-08-01
> **asdfoo said:**
> You can read my post again and follow the suggestion there.
Oh sorry I completely forgot to ask this in my response to your post: 
Is that option safe for me, as a relative newbie? It seems to be a rather difficult (and risky) approach--does that mean that the only approach that will get rid of this bug is going to inherently be a risky one? I wouldn't be surprised if that were the case, of course, but obviously I'd rather exhaust all safe options before opting for one that could damage my system.

---

### Post by asdfoo on 2010-08-01
> **glad. said:**
> Oh sorry I completely forgot to ask this in my response to your post: 
Is that option safe for me, as a relative newbie? It seems to be a rather difficult (and risky) approach--does that mean that the only approach that will get rid of this bug is going to inherently be a risky one? I wouldn't be surprised if that were the case, of course, but obviously I'd rather exhaust all safe options before opting for one that could damage my system.

I think it's no more likely to damage your system than the current setup is.  You'd just be using versions of software closer to what the developers are using.  Worst case scenario would be that an update might stop Xorg from loading and you'd be dropped to a console prompt.

As far as I can see it's the last avenue of approach before going back to windows.

---

### Post by glad. on 2010-08-01
> **asdfoo said:**
> I think it's no more likely to damage your system than the current setup is.  You'd just be using versions of software closer to what the developers are using.  Worst case scenario would be that an update might stop Xorg from loading and you'd be dropped to a console prompt.

As far as I can see it's the last avenue of approach before going back to windows.
OK, thanks very much for your advice!

---

### Post by 0004tom on 2010-08-01
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20882)

Read up on some off the known work arounds for SC2. Some claim it installed fine first time, ran first time. Some claim they need a patched version of Wine..

---

### Post by Mas0ne on 2010-08-01
Here's a howto I wrote on how to get SC2 up and running almost flawlessy:
[http://www.zealouscraft.com/index.php/linux/35-gaming/48-starcraft-2-on-linux](http://www.zealouscraft.com/index.php/linux/35-gaming/48-starcraft-2-on-linux)

At the end of the guide there are links to various places that can help you in your troubleshooting

---

### Post by the3dman on 2010-08-03
I have the game up and running but want to be able to play offline with custom ai, is there anyway to get any of the offline launchers to work under wine?

---

