---
title: "Desktop graphic influence on fps"
date: 2011-06-19
forum: Wine
---

### Post by nismolinux on 2011-06-19
Hi guys. Im new to linux and I kind have some problems running game, like WoW. Ive bought a new card, a GeForce GTS 450 1g GDDR5 OC and when I run WoW on wine i got like 20 fps in 5man dongeon. I got the lastest driver (270.xx.xx) available from nvidia-current. My question is, if Im using a distro with gnome(3 menu) , kde or Unity, will it affect my gaming fps? Cause with this card I saw a lot of ppl (on windows) running over 80 fps. Ive tried a lot of distro (ubuntu 10,11, mint 10,11). I did all the tricks Ive saw on google too! Thank for your answer every1! 

P.S. Sorry for my english! lol

---

### Post by Perfect Storm on 2011-06-19
Moved to UF Wine section.

---

### Post by desktorp on 2011-06-19
Did you check [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) ..?  The very first part about direct rendering may be your key, if you haven't tried that.

Though it varies greatly, many games seem to prefer either window or fullscreen mode, but seldom do both modes share equal quality.  Try both, but then start looking at video settings, both in WoW and in your desktop's settings.  Have you tried running WoW at the lowest possible settings and gradually tweaking them upward to see where the problems begin?  

Such a low frame rate with such a nice card - I would suspect there are some errors happening.  If you run WoW from the terminal, you may get a better insight.  Also, when you say you have tried many distros, do you mean with this card and this game?  Has each distro given you the same problem?

Check against settings like "Vsync" (which may be listed in more than one place, with different names like "Sync with Video" "Sync with Audio" "Wait for Vertical Blank" etc..)  Sometimes if there are conflicting settings between programs and the environment's overall video, it can cause slowdowns and flickering.  While you're hunting around there, you might check nvidia-settings (under the power settings/powermizer) to see if you're running in some sort of adaptive/low power mode.  Most modern cards have throttling features so they're not always running at full blast.. but sometimes they seem like they need to be manually set.  This probably is not the problem.

Also, know that sound, even when it seems to be working, can cause problems.  If you're feeling adventurous enough, try switching Wine to ALSA, OSS, etc and see if anything ever changes.

**These are merely guesses.  When you run a program from the terminal, the terminal stays open, while the program does its thing.  Use it as you normally would and then check the terminal when you're done.  It will probably be full of crazy errors and fixme messages and may even be a bit scary, but this is the best bet to diagnose problems.**

---

### Post by bobwyajnr on 2011-06-19
> **nismolinux said:**
> My question is, if Im using a distro with gnome(3 menu) , kde or Unity, will it affect my gaming fps?

Generally if you are running games fullscreen you want to turn off Desktop effects for fullscreen applications when using the KVM and Compiz window managers. The Compiz setting is a bit obscure: **CompizConfig Settings Manager**->**General**(tab)->*Undirect Fullscreen Windows*(check) !!

I would recommend not using Gnome 3 or Unity (in their current state) as these are turning out to be Alpha quality releases. Give these a few months to mature and the bug fixes to roll in! KDE 4.6 or Gnome 2+Compiz FTW at present!

Also I would recommend turning off console debugging completely for your games -to get maximum performance... ( Guide for this is in the Wine user documentation - see the stickies for this thread - sure you've read them through a few times - right? ;) )

Bob

---

### Post by nismolinux on 2011-06-19
thanks guys for your advice! I'll try this tommorow!

---

### Post by nismolinux on 2011-06-30
hi guys

Just for an updated.. I did something and I went from 50fps max (high settings) to 113fps max (ultra settings). I created 2 icons on my desktop.. one with metacity --replace that I run before I play, and the other one compiz --replace when I'm done! Maybe there's an other way to do it, but for me, it works!

later dudes!

---

### Post by cwwilson721 on 2011-06-30
Thus, the reason why it says in almost EVERY HOWTO on running WoW in wine with Ubuntu:

DISABLE COMPIZ
RUN IN OPENGL
INTEL DOESN'T REALLY WORK FOR WOW/WINE

This same 'issue', along with 'black areas' or using an Intel graphics chip, accounts for 95% of the WoW issues.

If you DON'T do the first two, you will have lousy or odd graphics and low framerates.
If you DO use the third, you'll never have it running well. Blame the hardware and the drivers.

I think I'll bookmark this post, and refer people here.

---

