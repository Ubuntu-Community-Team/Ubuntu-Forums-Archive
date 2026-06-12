---
title: "WoW will only run in opengl mode"
date: 2009-04-02
forum: Wine
---

### Post by pinkspice on 2009-04-02
Hi, I am having problems getti wine to run under ubuntu with wine. i managed to install everything fine and installed directx on it as well. when i forst tryed to run wow i just got wow critical errors. after looking on the forums i found a suggestion to add -opengl to the command to run wow, which i presume then means i am usin opengl rather than directx to run wow. This worked fine whilst i was in lower level places but when i went on my higher lvl character in northrend my screen just went mad with my framerates dropping to like 10 or less and eventually again giving me the wow critical error. what can i do to fix this and preferably get wow to run under dirctx rather than opengl. Thanks xxx

---

### Post by Brynster on 2009-04-02
> **pinkspice said:**
> Hi, I am having problems getti wine to run under ubuntu with wine. i managed to install everything fine and installed directx on it as well. when i forst tryed to run wow i just got wow critical errors. after looking on the forums i found a suggestion to add -opengl to the command to run wow, which i presume then means i am usin opengl rather than directx to run wow. This worked fine whilst i was in lower level places but when i went on my higher lvl character in northrend my screen just went mad with my framerates dropping to like 10 or less and eventually again giving me the wow critical error. what can i do to fix this and preferably get wow to run under dirctx rather than opengl. Thanks xxx


Righty hoo

Firstly you need to completely remove wine as you have broken it potentially by forcing directx to be installed. As wine has its own implimentation of directx built into it. Then reinstall wine from synaptec or winehq.org.

I use the latest release version 1.1.18 and i seem to have improved my frame rates.  

Secondly many/most(me included) people have to run WoW in opengl mode as some of the directx effects used in the game cause poor performance/crashes. 

Also you have not included any system details, so i would guess that your running an ATi based card as the sympton toy have described is also very common with ATi drivers.....


If you need more help please post some system specs.

---

### Post by pinkspice on 2009-04-02
of course, my graphics card isnt ati its a nvidia geforce 9800 GX2, my cpu is an intel q600 quad core and my motherboard is a striker II extreme and imm currently using 2g ddr3 ram. 

as for the directx, i followed a guide on the internet to install it in wine, i didnt realise it had it built in. xx

---

### Post by hikaricore on 2009-04-02
You should be running WoW in opengl mode for best results anyway...

---

### Post by pinkspice on 2009-04-02
i was happy to run it in opengl mode but like i said when i logged on in northrend it just crashed every time.

---

### Post by pinkspice on 2009-04-03
ok, update. last night i reinstalled wine and wow. i ca now run wow with or without opengl and had no critical errors, what its now doing is occasionally just randomly closin wow. no errors or anything, wow just disappears and i need to start it again? has anyone any ideas what would be making it do this? thanks for the help btw :)

---

### Post by Bios Element on 2009-04-03
> **pinkspice said:**
> i was happy to run it in opengl mode but like i said when i logged on in northrend it just crashed every time.

One of my friends on Linux ran through clear to level 80 including northrend and most instances.  So it's not a problem with opengl mode itself.

---

### Post by bofh80 on 2009-04-05
hey, just to point out a slight bug
i had corruptions (others reported crashing) when moving from inside to outside in opengl mode.  
the trick was to turn the mini map (radar ghey thing) off. press M or whatever.
that might solve other problems.

as said above, opengl mode appears to work best. but the dev's of wow have pointed out that it's not supported, and graphical tears and corruptions are to be expected.
but it runs flawlessy in opengl mode on my bro's 8.10 . he only has a gf8400.
amd x2 6000+.

---

### Post by gjoellee on 2009-04-05
WINE dopes not run Direct X well, so you should stick to OpenGl

---

