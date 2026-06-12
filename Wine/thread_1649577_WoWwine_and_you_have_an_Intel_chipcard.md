---
title: "WoW/wine and you have an Intel chip/card:"
date: 2010-12-20
forum: Wine
---

### Post by cwwilson721 on 2010-12-20
If you have a Intel videocard/chip, and you want to run World of Warcraft, I have news:

YOU CANT

It has to do with opengl (which linux/wine uses to run) and Intel not correctly/fully implementing it.

No amount of 'new' drivers will work. It is the chip AND drivers. No opengl, no WoW/wine.

While your card/chip MAY work in Windows using D3D, it WILL not work in wine/WoW with opengl.

Please, if you see a post asking about WoW using wine, point to this post.

It will clear up a few questions.

---

### Post by NightwishFan on 2010-12-20
I am inclined to agree, my Intel card works with very few higher end opengl programs. Still what does work works great so its not a loss. :)

---

### Post by damonVT on 2011-03-05
Good news WoW players with Intel chips, YOU CAN play WoW through wine.

I was doing that just now, using direct3D, by following [these instructions]("http://translate.google.com.br/translate?hl=pt-BR&langpair=pt|en&u=http://www.ladolinuxdaforca.com.br/linux/jogos/instalando-world-of-warcraft-linux-intel&prev=/translate_s%3Fhl%3Dpt-BR%26q%3Dwww.ladolinuxdaforca.com.br/linux/jogos/instalando-world-of-warcraft-linux-intel%26sl%3Den%26tl%3Dpt").

Since I already had wine and Wow installed, I just followed the regedit and Config.wtf parts, and also start Wow from the command line with: ```
wine Wow.exe -d3d
``` instead of the wow script shown in the instructions. The result is a totally playable WoW with decent framerates around 20-30 from what I've seen. The issues are a black polygon under characters and sometimes X crashes when switching away from Wow. These may be solvable, I've only just started trying to get this to work yesterday.

Also, OpenGL shows a distorted display, but I'm going to try [these instructions]("http://www.vanade.com/~blc/html/winewow/") and see if that works.

Onwards and upwards fellow users of energy-efficient and cool-running Intel graphics! Wow is an old game and not very intensive, and it's one Intel can handle, even through wine!

I have a Lenovo T500 with switchable graphics: ATI Radeon HD3650 & Intel GMA 4500MHD, but the Intel card seems to have more functional 3D acceleration for WoW, SketchUp, etc now in early 2011 and also uses much less power than the ATI. I'm using Gentoo with unstable X, drivers, mesa, etc (but not from git or cvs or whatever bleeding edge is).

---

### Post by cwwilson721 on 2011-03-05
Newer (above the 3500 level) MAY be playable. However, the "occasional crashes" and "black area" make it NOT playable, at least from a true gaming perspective.

The newest Sandy Bridge CPU/GPUs look like they may be winners, but for now, they still aren't out enough to find out.

I still say, if you want to play WoW with a Intel GMA chip, use Windows. It still doesn't let you raid. You say you have 20-30FPS, but what do you get in a 10 or 25 man raid? Or a large BG? If the only thing you can do is gather herbs or level, you're missing two thirds of the game.

If it crashes 1 out of 5 sessions, runs only 1/3 of the content, and graphics are unstable, it looks like you can only play 25% of the game.

THAT is not playable, by my definition

---

### Post by Dustin2128 on 2011-03-05
Heh, I always thought it was funny how bad the intel chipsets were, I mean before they moved up the requirements to shader 2 (early '10 I'm thinking) I played warcraft just fine (up to 50-60fps) with a GeForce 4 Ti4800 128Mb *from 2003.* Intel's been holding back graphics on the desktop for a good few years, can't wait for sandy bridge to become mainstream. Or for everyone to swap to dedicated GPUs....

---

### Post by cwwilson721 on 2011-03-06
You'll never have integrated GPUs that can keep up with discreet cards...

Example: Let's say you bought a motherboard in '06 with a G94 Nvidia Video integrated chip. (The G94 was the one that powered the 8800 thru 9800 series cards). A year or so later, it's woefully behind the 'top end', so you want a new Nvidia XXX chip, because that game you gotta play need Shader 5.956, or the newest MS "Standard" that they decided was a good idea to force upon the world. Well, you can't, not without buying a new motherboard. It's also going to look funny with the huge coolers and extra power connections.

Now, it WOULD/WILL be nice if Sandy Bridge actually works. The potential is phenomenal, just as the original 3D Intel chips were (They were actually the fastest for awhile). It will keep Intel competitive for a little bit, but eventually, they'll figure "the graphics are good enough" AGAIN, and it will go back to being the tow-headed-step-child.

I wish the best for Intel, but as of now, it can't REALLY play WoW/wine. While it may run, or not, it's NOT 'playable'. Get in a group of more than 5, and see what I mean. The hardware AND drivers are well below the curve needed. Nobody to blame but Intel.

And I agree about the bigger graphics demands, but that's part of the gaming world. At least WoW can still play on alot of NV/AMD video cards/chips still. Considering how old the game is, it still does a surprisingly good job of balance between low-end hardware and eye-candy.

But basically, you need a 8600 series and above NV(NOT GS,except the 9600 GS... Weird, but true. I have one, and it runs IDENTICAL to my old 9600GSO. Go figure)  or a 4500 and above AMD/ATi video to run WoW/wine in a playable configuration (Meaning you can raid or go in a big battleground without going to 1 FPS. I tried to go on a 10 man on my lappys Intel video ONCE...Never again).

So to you Intel Video Users: Don't. It ain't gonna really work.
IF you can get it to launch, it still might crash. 
IF you can even login, FPS will be slow.
IF FPS is 'usable', you may have odd screens (Black areas, tearing, missing features, etc.)
IF it does OK to this point, more than 5 mans will KILL you.

Let's see what Sandy Bridge brings...

---

