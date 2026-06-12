---
title: "WoW Weird Colours On Login Screen"
date: 2010-12-18
forum: Wine
---

### Post by Pee10 on 2010-12-18
Hi,

So, i've just made the switch from xp to Ubuntu. I'm a heavy WoW player and am trying to set up WoW on my computer. Thing is, it's only a netbook. Specs is like n450 intel atom processor, 1gb ram, laptop graphics (onboard?). So first thing is, should I be able to play it? Was working fine on xp before the switch. Though I shouldn't be experiencing the screens that I am. 

I installed it by copying the folder from an up to date folder on my desktop. All goes well just when I open it with wine (yes, its latest version) I get this login screen, and if I spend the time getting into the game, which is very difficult, it just shows as an orange screen.

I followed a installation guide, and I made sure that thing in Terminal is activated, and done what I had to do to activate it so that is working fine. I also muddled around with my wine settings as per what I had seen on other threads, etc. Also fiddled around with my config folder to no avail.

Here is my current config folder.

> SET locale "enUS" 
SET patchlist "enUS.patch.battle.net:1119/patch" 
SET hwDetect "0" 
SET gxResolution "1024x600" 
SET gxRefresh "60" 
SET gxMultisampleQuality "0.000000" 
SET gxFixLag "0" 
SET videoOptionsVersion "4" 
SET playIntroMovie "4" 
SET showToolsUI "1" 
SET Sound_MusicVolume "0.40000000596046" 
SET Sound_AmbienceVolume "0.60000002384186" 
SET farclip "507" 
SET particleDensity "40" 
SET reflectionMode "0" 
SET groundEffectDensity "40" 
SET groundEffectDist "110" 
SET environmentDetail "75" 
SET weatherDensity "1" 
SET gxAPI "OpenGL" 
SET readTOS "1" 
SET readEULA "1" 
SET enterWorld "1" 
SET Gamma "1.000000" 
SET accounttype "BC" 
SET realmName "Burning Blade" 
SET gameTip "6"I have scoured through google for the past 2 hours, still to no avail. So I have finally decided to post here.

Thanks in advance for any help, really keen on getting this working.

And loving Ubuntu so far, so good to finally have a change.

---

### Post by cwwilson721 on 2010-12-18
Well, some bad news...

WoW on wine [COLOR="Red"]will not be playable[/COLOR] with a Intel integrated graphics chip (If that's what you have).

To find out, open a terminal and type ```
lspci
``` and see what the graphics chip is. If it says 'Intel", forget it. ANY other chip will work.

Search the forum for why.

---

### Post by Pee10 on 2010-12-18
Yep, it is. That's a bummer, oh well thanks for helping (:

---

### Post by cwwilson721 on 2010-12-19
It's one of those things.

Until patch 4.x, it was BARELY playable in wine. Intel chips and opengl just don't get along.

After 4.x, Blizzard upped the graphics too much, and Intel died from the wine/WoW scene. And due to both physical (chip) and kernel driver (intel), I don't see any hope for a revival.

It is still BARELY playable on Windows right now. But I wouldn't go into a big city or a raid or even a 5man with it. Just not enough horsepower anymore, even in Windows/D3D

---

### Post by Lintnewbie on 2010-12-20
I'm having the same problem with my laptop I found this on WineHQ AppDB. So it is the integrated graphics?
 
> **intel 945 dual-tmu error**
by Bryon Gill on Sunday December 5th 2010, 9:00
I've got a laptop with intel 945 graphics that ran wow reasonably well under wine before the 4.0.x patches. Now that I've installed them, the loading screen works fine, the character selection screen works fine, but when the world loading screen bar finishes the game crashes. 
 
I found that if i *re-enable* pixel shaders and vertex shading in winecfg, the game will load, but the frame rate is unusable even for auction house and the like; it runs at about 0.5 fps in most places. 
 
This is all under d3d. If I attempt to run the game under opengl (which has never worked well on this hardware), I now get an error that I must install graphics hardware with "dual-tmu support". This is a laptop so obviously, that's impossible. 
 
Did something happen that made vertex shading/pixel shaders mandatory in the newest patches under d3d, and if so is there a way to disable it? As I said, I got usable (15-20) fps before under d3d on this machine. All graphics settings are at minimum, all the usual workarounds (ffxglow 0 etc) have been applied.

 
My post
[http://ubuntuforums.org/showthread.php?t=1649151](http://ubuntuforums.org/showthread.php?t=1649151)

---

### Post by cwwilson721 on 2010-12-20
> **Lintnewbie said:**
> I'm having the same problem with my laptop I found this on WineHQ AppDB. So it is the integrated graphics?
 

 
My post
[http://ubuntuforums.org/showthread.php?t=1649151](http://ubuntuforums.org/showthread.php?t=1649151)
Asked/answered.

READ AND LEARN

---

