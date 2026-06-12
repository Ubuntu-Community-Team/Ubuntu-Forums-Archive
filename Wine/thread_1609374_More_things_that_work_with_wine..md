---
title: "More things that work with wine."
date: 2010-10-30
forum: Wine
---

### Post by DirtyPC on 2010-10-30
Hello all, don't know if your still interested, but I managed to get FRAPS, Spotify, Microsoft Office 2003 installed, I will put up a how-to if enough people request it.
Harry.

---

### Post by DirtyPC on 2010-10-30
[IMG]http://i53.tinypic.com/33bd5de.png[/IMG]

[IMG]http://i52.tinypic.com/29lb7rr.png[/IMG]

Just some print screens of them in action. :-)

---

### Post by DirtyPC on 2010-10-30
The strange thing for me is, the office install froze near the end, i pressed exit, but they all work fine some how!

---

### Post by bobwyajnr on 2010-10-30
> **harrylucas1 said:**
> Hello all, don't know if your still interested, but I managed to get FRAPS, Spotify, Microsoft Office 2003 installed, I will put up a how-to if enough people request it.
Harry.

I don't think getting Fraps 'running' is that difficult!! (I certainly managed it without any bother...) But can you actually get an FPS counter up when playing games?? Then I would be interested!!

I have World In Conflict running (including multiplayer!!) via my Steam client but Battlefield 2 - now that one is proving much more difficult... :popcorn:

Bob

---

### Post by DirtyPC on 2010-10-30
> **bobwyajnr said:**
> I don't think getting Fraps 'running' is that difficult!! (I certainly managed it without any bother...) But can you actually get an FPS counter up when playing games?? Then I would be interested!!

I have World In Conflict running (including multiplayer!!) via my Steam client but Battlefield 2 - now that one is proving much more difficult... :popcorn:

Bob
Hi, if you get Battlefield 2 non-steam on PlayOnLinux, then it seems to work, And I get the fraps counter under other Wine games like Unreal or Half life

---

### Post by rjmanmac on 2010-10-30
i am using audio tuner from supernifty.com

---

### Post by DirtyPC on 2010-10-30
***_[COLOR="Red"]UPDATE[/COLOR]_***

CS4 lite, and CS4 portable both work under Wine aswell.

---

### Post by DirtyPC on 2010-10-30
> **rjmanmac said:**
> i am using audio tuner from supernifty.com

Thanks for that, once a decent list is compiled, i'll put it in the help section. :-)

---

### Post by DirtyPC on 2010-10-30
> **bobwyajnr said:**
> I don't think getting Fraps 'running' is that difficult!! (I certainly managed it without any bother...) But can you actually get an FPS counter up when playing games?? Then I would be interested!!

I have World In Conflict running (including multiplayer!!) via my Steam client but Battlefield 2 - now that one is proving much more difficult... :popcorn:

Bob
How did you fix the Tahoma font problem with Steam?

---

### Post by bobwyajnr on 2010-10-30
> **harrylucas1 said:**
> Hi, if you get Battlefield 2 non-steam on PlayOnLinux, then it seems to work, And I get the fraps counter under other Wine games like Unreal or Half life

Do you have to do anything to get the global FRAPs keybindings to work? Or can you just force on the FRAPs FPS reporting? The GUI ran fine when I tried it - it just didn't seem to do much when I ran a game in WINE...

I have got to the stage where the Battlefield 2 intro movies and menus work perfectly. Launching Singleplayer crashes the game (!!) I can play multiplayer but I get a number of more minor mipmap graphical glitches (I have the latest Nvidia blob drivers for my 8800 GTX BTW). Obviously I get kicked by Punkbuster on Punkbuster enabled servers... Problem is now I need to do regression testing on WINE. Will get around to this eventually I suppose... :)

Thanks
Bob

---

### Post by DirtyPC on 2010-10-30
I heard CoD, Unreal 3 and several other 'Games For Windows' games work very well in PlayOnLinux/Wine

---

### Post by DirtyPC on 2010-10-30
> **bobwyajnr said:**
> Do you have to do anything to get the global FRAPs keybindings to work? Or can you just force on the FRAPs FPS reporting? The GUI ran fine when I tried it - it just didn't seem to do much when I ran a game in WINE...

I have got to the stage where the Battlefield 2 intro movies and menus work perfectly. Launching Singleplayer crashes the game (!!) I can play multiplayer but I get a number of more minor mipmap graphical glitches (I have the latest Nvidia blob drivers for my 8800 GTX BTW). Obviously I get kicked by Punkbuster on Punkbuster enabled servers... Problem is now I need to do regression testing on WINE. Will get around to this eventually I suppose... :)

Thanks
Bob
The Fraps Key Bindings worked out the box, for some reason Fraps has to be emulated full screen for it to work though

---

### Post by DirtyPC on 2010-10-30
Steam works under Vista too. Games tested HL2:DM and Lost Coast

---

### Post by cwwilson721 on 2010-10-30
If I remember right (been awhile since I used FRAPS), it has to be launched in the same wine 'env WINEPREFIX' the game is launched from. (I know it's the same way with Ventrilo)

Example: 
I launch WoW using ```
[COLOR="Red"]env WINEPREFIX="/home/<USER>/.wine-wow"[/COLOR] wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
```If I prepend the part in red to my Ventrilo launcher, there is no issue with keybindings, etc.

I installed Vent to my 'wine-wow' folder, too...lol. I don't use it anymore, tho. I use Mangler now. Works perfect.

If I remember my old fraps setup, it was the same way. Install to the same  wine folder you have the game installed to, and prepend the 'env PREFIX= <foo>' and it worked.

---

### Post by DirtyPC on 2010-10-30
[IMG]http://i53.tinypic.com/23racm9.png[/IMG]

---

### Post by DirtyPC on 2010-10-30
> **cwwilson721 said:**
> If I remember right (been awhile since I used FRAPS), it has to be launched in the same wine 'env WINEPREFIX' the game is launched from. (I know it's the same way with Ventrilo)

Example: 
I launch WoW using ```
[COLOR="Red"]env WINEPREFIX="/home/<USER>/.wine-wow"[/COLOR] wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
```If I prepend the part in red to my Ventrilo launcher, there is no issue with keybindings, etc.

I installed Vent to my 'wine-wow' folder, too...lol. I don't use it anymore, tho. I use Mangler now. Works perfect.

If I remember my old fraps setup, it was the same way. Install to the same  wine folder you have the game installed to, and prepend the 'env PREFIX= <foo>' and it worked.
Hello, thanks for that, i'm sure it will be very useful for others looking on this thread

---

### Post by bobwyajnr on 2010-10-30
> **harrylucas1 said:**
> How did you fix the Tahoma font problem with Steam?

My main problem with Steam was it using up 200% CPU and bringing my Core i7 920 @4Ghz system to a standstill. Turns out the Nvidia blob driver in the Lucid repository wasn't playing nice with it. :)

Since I update to the Nvidia 256/260 drivers I haven't noticed any major problems with Steam. Obviously I have the Steam community options disabled and I haven't tried the store (which apparently is broken as well). The client appears to visually render OK. I can restore full Steam game backups/archives (using Samba) over my network, download games, change the game views, launch games, etc., etc.

What is the Tahoma font problem? I usually install 'allfonts' in **winetricks** as my first step in installing Wine - does that mask this problem perhaps?

Bob

---

### Post by DirtyPC on 2010-10-30
> **bobwyajnr said:**
> My main problem with Steam was it using up 200% CPU and bringing my Core i7 920 @4Ghz system to a standstill. Turns out the Nvidia blob driver in the Lucid repository wasn't playing nice with it. :)

Since I update to the Nvidia 256/260 drivers I haven't noticed any major problems with Steam. Obviously I have the Steam community options disabled and I haven't tried the store (which apparently is broken as well). The client appears to visually render OK. I can restore full Steam game backups/archives (using Samba) over my network, download games, change the game views, launch games, etc., etc.

What is the Tahoma font problem? I usually install 'allfonts' in **winetricks** as my first step in installing Wine - does that mask this problem perhaps?

Bob
I didnt have the problem, but before i installed it, i read that the tahoma font problem was a major issue.

---

### Post by yabbadabbadont on 2010-10-30
Just in case you didn't already know, the Wine appdb is loaded with information on applications that have been tried under wine and how well they worked.  It also often includes solutions/work-arounds in getting apps to work.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by DirtyPC on 2010-10-31
> **yabbadabbadont said:**
> Just in case you didn't already know, the Wine appdb is loaded with information on applications that have been tried under wine and how well they worked.  It also often includes solutions/work-arounds in getting apps to work.

[http://appdb.winehq.org/](http://appdb.winehq.org/)
Yeah, but its written by people and you cant trust their honesty.

---

### Post by DirtyPC on 2010-10-31
[COLOR="Red"]***_UPDATE_***[/COLOR]

Quake 3 Arena and Quake 4 both work brilliantly under Wine. Aswell as Deus Ex.

---

### Post by bobwyajnr on 2010-10-31
> **harrylucas1 said:**
> Yeah, but its written by people and you cant trust their honesty.

Don't you mean stupidity... If a game is given a 'garbage' rating by someone who doesn't know how to selectively override .dll's, etc. It can take quite a long time to get the settings right for a game and most people don't have the patience I bet.

There are also a lot of folk in the Linux community who are like 'dual-boot for gaming' and 'Wine is pointless', etc. Personally I am very impressed with the improvements in Wine over the 6 years I have tried it (off and on).

Bob

---

### Post by DirtyPC on 2010-10-31
> **bobwyajnr said:**
> Don't you mean stupidity... If a game is given a 'garbage' rating by someone who doesn't know how to selectively override .dll's, etc. It can take quite a long time to get the settings right for a game and most people don't have the patience I bet.

There are also a lot of folk in the Linux community who are like 'dual-boot for gaming' and 'Wine is pointless', etc. Personally I am very impressed with the improvements in Wine over the 6 years I have tried it (off and on).

Bob
I was trying to be polite, but in honestly, I do agree. I don't want some random guy telling me I can't play a certain game when I can. It's giving Wine a bad name, when with a little patience, it's fantastic. And with that dual booting for games thing, I only use Dual booting as a neccisary backup, if you're going to be using XP for things, why don't you just have XP not Ubuntu?

Edit: Thats is probably offensive. Better remove it
Harry,

---

### Post by DirtyPC on 2010-10-31
***_[COLOR="Red"]UPDATE.[/COLOR]_***

In order to work properly, Deus Ex needed to be set in VISTA with Screen emulation turned OFF.

Thanks, Harry

---

### Post by yabbadabbadont on 2010-10-31
> **harrylucas1 said:**
> I don't want some random guy called Ming-Ling from Asia telling me I can't play a certain game when I can.

As opposed to some random guy called harrylucas1 from the UK telling me that I can play a certain game when I can't.  :lol:

Anyway, there isn't any harm in posting your experiences here.  However, you should also add your solutions to the wine appdb for others, who may not frequent these forums, to find.

---

### Post by DirtyPC on 2010-10-31
> **yabbadabbadont said:**
> As opposed to some random guy called harrylucas1 from the UK telling me that I can play a certain game when I can't.  :lol:

Anyway, there isn't any harm in posting your experiences here.  However, you should also add your solutions to the wine appdb for others, who may not frequent these forums, to find.
And what games cant you play yabbadabbadont from 2 exits past crazy? :-). And I may do, once i've built up and extensive list.

---

### Post by marl30 on 2010-10-31
Did you have any luck getting Access 2003 or 2007 to working without any issue in Wine?

---

### Post by DirtyPC on 2010-10-31
> **marl30 said:**
> Did you have any luck getting Access 2003 or 2007 to working without any issue in Wine?
I have only tried 2003 with no problems. Would like me to try 2007 now?

---

### Post by marl30 on 2010-10-31
> **harrylucas1 said:**
> I have only tried 2003 with no problems. Would like me to try 2007 now?
I would definitely appreciate that, but any one of them working would be good enough for me since I only use Access 2003 at school. I got it to start (2003) in Wine, but it either takes forever to start or crashes on start up. What Winetricks plugins do you use, and what overrides do you recommend to have Access 2003 working perfectly? Everything else in both 2003 and 2007 work perfectly for me, barring Publisher in 2007, which freezes quite often.

---

### Post by DirtyPC on 2010-10-31
> **marl30 said:**
> I would definitely appreciate that, but any one of them working would be good enough for me since I only use Access 2003 at school. I got it to start (2003) in Wine, but it either takes forever to start or crashes on start up. What Winetricks plugins do you use, and what overrides do you recommend to have Access 2003 working perfectly? Everything else in both 2003 and 2007 work perfectly for me, barring Publisher in 2007, which freezes quite often.
unusually, I got my 2003 copy from a torrent. I installed it, but at 96 percent I received an error, Clicked cancel, and somehow everything still worked like a charm. Getting 2007. Do you know if Windows Media Player could run on Wine?

---

### Post by DirtyPC on 2010-10-31
Windows Media Player 10 works a treat.

[IMG]http://i55.tinypic.com/ab6xq0.png[/IMG]

---

### Post by marl30 on 2010-10-31
> **harrylucas1 said:**
> Windows Media Player 10 works a treat.

[IMG]http://i55.tinypic.com/ab6xq0.png[/IMG]

That's great. I usually use version 9 instead though, not for playing my media, however, as I use mainly VLC for that. I have a lot of issues with Sopcast for Linux, so I often use the Windows version in Wine. It doesn't work unless you have media player installed  though.

As for Office 2003, it usually installs perfectly for me in Wine. If you are having installation problem, maybe that's because you are using one of the development versions on Wine. It installs perfectly in Wine 1.2.1.

---

### Post by bobwyajnr on 2010-10-31
> **yabbadabbadont said:**
> As opposed to some random guy called harrylucas1 from the UK telling me that I can play a certain game when I can't.  :lol: 

Hey he 'da man. :guitar:

> **yabbadabbadont said:**
> 
Anyway, there isn't any harm in posting your experiences here.  However, you should also add your solutions to the wine appdb for others, who may not frequent these forums, to find.

Problem with AppDB is it's getting a bit of mess. For example World In Conflict runs from a Steam client (including multiplayer) but it appears that it doesn't works so good in the retail copy (I looked it up and it uses SecuROM or something similar)... A lot of the Steam run games need to be forked off because they don't have the DVD/CD copy protection.

Another problem is the guides perhaps gloss over just what steps were taken to get the darn thing running! Like exactly what .dll overrides are needed, etc. I am just as guilty as the next person...

The Wine user forum is pretty hopeless. I wanted to get some screenshots of Windows games running Wine and was getting frame tearing with **PRINT-SCREEN**. (Not just for my amusement but to submit to AppDB as an advert for Wine.) I ended asking on the Ubuntu forums and getting a response with hours. Ironically I linked my thread on the Wine forums back to my (personally created) BASH script solution in the Ubuntu forums!! This sort of common need/useful tip should have a sticky at the very least...

It's difficult to get involved in the Wine development process. Newbies are not tolerated and you go from running 
**wine steam.msi** :D in a BASH shell to downloading a Git tree of Wine source code pretty quickly... :eek:

Bob

---

### Post by DirtyPC on 2010-11-01
> **bobwyajnr said:**
> Hey he 'da man. :guitar:



Problem with AppDB is it's getting a bit of mess. For example World In Conflict runs from a Steam client (including multiplayer) but it appears that it doesn't works so good in the retail copy (I looked it up and it uses SecuROM or something similar)... A lot of the Steam run games need to be forked off because they don't have the DVD/CD copy protection.

Another problem is the guides perhaps gloss over just what steps were taken to get the darn thing running! Like exactly what .dll overrides are needed, etc. I am just as guilty as the next person...

The Wine user forum is pretty hopeless. I wanted to get some screenshots of Windows games running Wine and was getting frame tearing with **PRINT-SCREEN**. (Not just for my amusement but to submit to AppDB as an advert for Wine.) I ended asking on the Ubuntu forums and getting a response with hours. Ironically I linked my thread on the Wine forums back to my (personally created) BASH script solution in the Ubuntu forums!! This sort of common need/useful tip should have a sticky at the very least...

It's difficult to get involved in the Wine development process. Newbies are not tolerated and you go from running 
**wine steam.msi** :D in a BASH shell to downloading a Git tree of Wine source code pretty quickly... :eek:

Bob
Hello. Seems that you are right on the wine getting clustered. I am taking others advice and uploading up-to-date reviews + I have become a Super moderator of some Games.. well Q3A but I plan to do more If I feel they are not accurate.

As with your first comment, Thanks! Made me laugh.

Harry,

---

### Post by DirtyPC on 2010-11-01
***_[COLOR="Red"]UPDATE.[/COLOR]_***

Office 2007 (My LEGAL COPY) Works a Treat Under wine also.

Harry,

---

### Post by cwwilson721 on 2010-11-01
I don't know why this has been glossed over, but the biggest MMORPG works PERFECT in wine: World of Warcraft.

The wine dev team actually puts alot of effort into making sure this game runs under wine. As does Nvidia (Which has actually, in the past, put out driver updates just so WoW runs better).

The new patch (4.0.1) installs and runs fine. The new Launcher works, too (haven't had any of the 'folder permissions' issues that the older Launcher created, YET).

As long as you run it in Windows XP mode, and opengl, it is as fast, if not faster, than Windows. (Gotta love better memory management and TCP/IP stack)

Caveat: Don't try to run WoW/wine with an Intel chip. It's just plain HORRIBLE. The Intel implementation (both in hardware not supporting the full opengl spec, and the Intel kernel module not doing opengl correctly) of opengl is the culprit. So if you try to use a Intel chipset in WoW, you are better off running in Windows. Or get an Nvidia card.

---

### Post by DirtyPC on 2010-11-02
> **cwwilson721 said:**
> I don't know why this has been glossed over, but the biggest MMORPG works PERFECT in wine: World of Warcraft.

The wine dev team actually puts alot of effort into making sure this game runs under wine. As does Nvidia (Which has actually, in the past, put out driver updates just so WoW runs better).

The new patch (4.0.1) installs and runs fine. The new Launcher works, too (haven't had any of the 'folder permissions' issues that the older Launcher created, YET).

As long as you run it in Windows XP mode, and opengl, it is as fast, if not faster, than Windows. (Gotta love better memory management and TCP/IP stack)

Caveat: Don't try to run WoW/wine with an Intel chip. It's just plain HORRIBLE. The Intel implementation (both in hardware not supporting the full opengl spec, and the Intel kernel module not doing opengl correctly) of opengl is the culprit. So if you try to use a Intel chipset in WoW, you are better off running in Windows. Or get an Nvidia card.
I'm not going to even try to have a go at that time. I personally hate it and it costs wayyyy to much.

Harry

---

### Post by bobwyajnr on 2010-11-06
I have recently reinstalled my OS - switching to Kubuntu 10.04 (having got heartily fed-up with the broken rendering/poor UI on the Gnome-based desktop :) )

Anyway since I am using a Desktop Manager based on **Qt** now I thought I would try out [Q4Wine]("http://sourceforge.net/projects/q4wine/"). I mean nobody minds using **ps** & **grep**, etc. and the ol' BASH prompt to manage their WINE prefixes/applications, etc... But Q4Wine is like put on a pair of comfy slippers after walking around in less comfortable footwear (anyway I think you get the idea)... :popcorn:

I can highly recommend it!

Bob

---

### Post by Elfy on 2010-11-07
There is already a real list of things  that work with wine - [http://appdb.winehq.org/](http://appdb.winehq.org/)

If you want to let people know what works and what doesn't - join there and then more people will find out not just people who come here.

This forum is for support.

Closed.

---

