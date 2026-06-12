---
title: "[WoW] Crashing when loading Dalaran?"
date: 2008-12-05
forum: Wine
---

### Post by urbancontra on 2008-12-05
I might be having trouble finding existing issues with this because the expansion is so new.  I have pretty much everything working flawlessly in wine and have logged a couple hours in while playing in the old world.  I tried teleporting into Dalaran with my mage and the game crashes do desktop immediately after the loading screen disappears.  Anyone have any advice for this issue?

---

### Post by europa on 2008-12-05
Just wanted to post and say I'm having an identical issue.  Dalaran crashes almost every time i've been there.

Sometimes I can walk around for about a minute, but then my screen turns to this:
[IMG]http://img360.imageshack.us/img360/664/screenshotjd0.png[/IMG]

Any help would be appreciated.

---

### Post by urbancontra on 2008-12-05
I was having a similar problem to that when Beryl/Compiz/enhanced graphics was enabled.  I turned them all off and didn't have that problem again.

---

### Post by europa on 2008-12-05
If I have effects turned on, WoW flickers and is unplayable. I have everything turned off.

---

### Post by hikaricore on 2008-12-05
I see you have the white minimap bug.  Perhaps this is an ATI issue?

Just guessing but what video hardware are you using?

---

### Post by urbancontra on 2008-12-05
I have ATI.  I found this, it may be unsolved as of yet:

[http://bugs.winehq.org/show_bug.cgi?id=15449](http://bugs.winehq.org/show_bug.cgi?id=15449)

---

### Post by europa on 2008-12-05
I am using ATI Radeon x9500xtx.

I do not have an issue with loading into the world. I only crash out while in Dalaran after about a minute of being there.

The minimap does not show while inside buildings, but i have never had any other issues.

I made this post a few months ago:
[http://ubuntuforums.org/showthread.php?t=930115](http://ubuntuforums.org/showthread.php?t=930115)

This occurred after updating the ATI driver. I had to rollback to an older version.  If you guys have a fix for that I will love you forever. :)

---

### Post by hikaricore on 2008-12-05
I'm not certain if it will help, but you could try fiddling with some video settings.

Turn off full screen glow effects and things of that nature relogging after each to see if it makes any difference.  You may even want to try switching between fullscreen and windowed mode as well.  Also run the game from a terminal and check to see if there are any GL errors while this is occuring, it could help you to stumble upon a work around or a fix.

Best of luck,

--Aaron

---

### Post by Ixonal on 2008-12-06
mine did that pretty much exactly. my problem was having cartographer running. maybe that's your issue too

---

### Post by europa on 2008-12-06
I don't have cartographer but i will disable to some mods to see if that helps. Thanks

---

