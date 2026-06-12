---
title: "Wine, DirectX, and ATI - why so slow?"
date: 2011-04-26
forum: Wine
---

### Post by Zorgoth on 2011-04-26
As far as I can tell, NVIDIA usually beats ATI, but in particular NVIDIA is just far, far better at running DirectX games through wine.  Even when ATI performs well in other areas it is just no good at DirectX through wine.  Is this more a problem with ATI drivers (my first guess, although since they are improving I'm confused that wine performance is still so bad), ATI's hardware design, or some kind of optimizations in wine for NVIDIA?

---

### Post by cogadh on 2011-04-26
It's most likely the drivers. Wine accomplishes its Direct3D functionality by translating those D3D calls into OpenGL calls that can then be understood by the video card's drivers. Since OpenGL support is mostly a function of the drivers and not the hardware, unexpectedly poor performance with OpenGL (as in performance well below the capabilities of the hardware) can usually be traced back to something lacking in the drivers. 

With ATI, for years their Linux drivers were pretty much an afterthought that they put little to no effort into and they have only recently begun to improve. Nvidia on the other hand, has always provided drivers that are very optimized and nearly equal to their Windows counterpart. The ATI drivers are really playing catch up to the Nvidia ones in comparison. I'm sure they will eventually get there, but for now, if you want to use Linux for a gaming machine, especially Windows gaming through Wine, Nvidia is still your best bet.

---

### Post by Zorgoth on 2011-04-26
Unfortunately I use a laptop, and the one I have I bought a year ago when everyone was obsessed with ATI and no one sold NVIDIA laptops...  One day I'll have a nice stable place of residence and I can have a desktop...  Or a nice stable source of income and I'll just replace my laptop at the same time as I get my Eee pad transformer, my espresso machine, my cuisinart food processor, and my kitchenaid mixer.  And a trip to Russia.  And a trip to France.  And a trip to Italy.  I plan to be a responsible spender.

I hope that ATI catches up sooner than later.  NVIDIA and Optimus is bad news for Linux laptop gaming.

---

### Post by disabledaccount on 2011-04-26
Any numbers? test results (eg FurMark, Unigine, Phoronix test suite)?  examples in selected situations? Default driver settings or optimized? what settings in games? (because even on windows different settings are better for ATI and for NV)
Are You comparing GTX480 to HD5870? or maybe some different models...

I know that peoples are telling such things because **some years ago** ATI drivers were crappy. And in this case I suppose that Zorgoth is talking about his **mobile** HD5470. Mobile versions always have mauch lower performance comparing to the same model in "normal" version - because of lower clocking and often because of fewer shaders, lower RAM badwidth, etc, etc.

I have eg. COD MW2.0, FEAR, all UT versions and some other games working flawlessly with HD5670 - so I can tell that bad ATI performance is a myth, together with flickering or tiling video.

edit: Zorgoth: now I know that You're talking about Your mobile version, ehh

---

### Post by Zorgoth on 2011-04-26
Yeah my card is weak, but still, in Windows it could run WoW on ultra; Ubuntu directx would be like 15 fps on low.  NVIDIA tends to get 50-70% performance according to things I read.

WoW has OpenGL mode so it's not really a problem.  Majesty 2 I get less than 5 fps and it's unplayable.  Starcraft 2 is pretty slow too, although just barely playable.  I also get serious heat issues even with a cooling pad.  I've never done any benchmarks, but the performance on wine is certainly many times lower than expected windows performance, although I don't use Windows so can't compare.

I kind of wonder why there isn't an OS X compatibility layer since the OS X version of games are OpenGL...

My impression is that in non-wine things like native games and compiz it functions relatively much better.

---

### Post by disabledaccount on 2011-04-26
Have You tried to disable compiz?

Furthermore, if your laptop overheats, then be prepared for dramatically  lower performance due to thermal throttling of both CPU and GPU. Maybe  You should check cooling fans and ventilation holes.

Can You tell what is clocking of Your GPU during load and idle? and what is GPU load level?
 run: >aticonfig --odgc when the game is running, and when the laptop is getting hot.

---

### Post by cwwilson721 on 2011-04-26
Your main issue is RUNNING D3D!

As a previous poster states, wine converts D3D calls to opengl. Why, oh why, would you D3D>opengl? Best off just opengl>opengl. If you speak English, why do you want everyone to speak Korean, then translate it? That would make phone calls silly. Just speak English/English. That's the same as running WoW in D3D mode. It has to translate, so YOU WILL BE SLOWER. The other advantage is that opengl/wine is faster than D3D/Windows, even.

[Run in opengl, if you want faster than Windows/D3D FPS.]("http://www.youtube.com/watch?v=xQFBK1yNIxE") (< THAT'S A LINK! Follow it! PROOF!!!)

You won't have the eye-candy, but when everyone else is saying "Ohh..Pretty water!", you'll be ganking them.

Just add '-opengl' to the end of your launcher command. It will add the appropriate setting in your config.wtf file, and away you go.

---

