---
title: "RA2 Yuri on Wine 1.1.37 forces Logout"
date: 2010-01-28
forum: Wine
---

### Post by Daddyo-613 on 2010-01-28
**The Problem:** Game splash screens load fine, single player new campaigns work fine as do saved games, however a problem occurs when playing a single player skirmish. The select map and options menus work fine but when a game is selected the screen showing the scenario loading will appear and when it finishes loading I get bumped out of the X session and the Ubuntu login screen appears. When I log back in RA2 is closed.

**My Settings:**
OS: Ubuntu: Karmic 9.10
      Gnome:  2.28.2
      Kernel:   2.6.31-17-generic-pae
CPU: Intel Core2 Quad @2.4GHz
Video Card: nVidia GeForece 8600,GT
Driver: nVidia 185.18.36

**My Wine Settings for RA2MD.exe:**
Version: 1.1.37
Additional Libraries: none
Sound: OSS, Hardware Acceleration=Full, 
           Default Sample Rate=48000, Default Bits Per Sample=16
Graphics: **Window Settings:** Allow window manager to decorate windows and control
              windows enabled, other options not enabled
              **Direct 3D:** Vertex Shader Support=Hardware, Allow Pixel Shader=enabled
              **Screen Resolution**=96 dpi
**Registry Edits:** DirectDrawRenderer=opengl and RenderTargetLockMode=readtex

I've tried changing Windows formats from Win98 to Win2K and WinXP and back again, no difference. Similarly, changing sound drivers from OSS to ALSA doesn't seem to make a difference either The frustrating thing is that once in a while the loading of the skirmish map will complete and the game will start and exit normally. If I try to go back in it will allow me to get all the way to the loading screen for the skirmish and then log me out of Ubuntu X session. I can't consistently reproduce a successful load of a skirmish game.

Any suggestions would be welcomed.

---

### Post by Daddyo-613 on 2010-01-28
I guess this is a bump. I wanted to add to my post above that I have StarCraft running and it works perfectly. It loads in a flash, operates seamlessly in full screen and the previous desktop resolution is restored on exiting the game.

StarCraft is older than Red Alert 2, Yuri's Revenge so I would have expected more problems with that program.

I would appreciate some suggestions. I expect that there are some RA2 fans out there and I know that there are wine experts about. I hope to hear from some of you.

Thanks in advance.

---

### Post by texaswriter on 2010-01-28
Try this website

[https://help.ubuntu.com/community/RedAlert2](https://help.ubuntu.com/community/RedAlert2)

and this one

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=252](http://appdb.winehq.org/objectManager.php?sClass=version&iId=252)

Understand that very old games, especially ones written for single cores can potentially start to have problems with multi core processors. I've had this problem with at least one of my favorite old school games: Sid Meier's Alpha Centauri and the Alien Crossfire expansion. Even on Windows it's hard to get this game running on 64bit/multicore processors. 

But, hope those above named websites help you. 

Also, if that doesn't work, try a product called POL [**P**lay **O**n **L**inux]. It has scripts for customizing individual bottles for a particular game as well as installing and running those games. There are plenty of POL scripts, so try that out. 

FWIW, Play On Linux is actually in the repository. You should use it as a compliment for Wine EVEN IF they don't have a script for your particular game because it allows you to sandbox each Windows program in its own bottle, which the original one does not have good support for. 

To me, this is actually one of the main reasons I purchased Crossover. You might consider purchasing Crossover Games if you foresee using Linux for gaming alot. Just check with their support pages to see what games you play and their level of support / functionality in the program. I play several games on Crossover just fine... Works Great... Although th eprogram is paid, they make programming contributions back to Wine...

---

### Post by Daddyo-613 on 2010-01-29
Thanks for the reply. I've been to both of the sites you listed many times. The first is written more clearly than the wineHQ app site. Unfortunately, neither address the problem I'm experiencing. My guess is that the failure of the selected game scenario to finish loading has something to do with the way RA2 and Wine are interacting with the X session settings for screen resolutions.

I've been running the game in various versions of Wine and there has been a steady improvement in performance. This last version 1.1.37 is the best yet. When it works the game operates as intended. Full screen and changing resolutions for game play and then back to the desktop settings works well...that is when it works. Sadly it only seems to work about 30% of the time. I haven't actually counted but I think that the program is slightly more likely to work after a full reboot. That's why I think the trouble lies with the X session.

In any event I'll keep hoping I stumble across something. I'm still opened to suggestions.

P.S. I had understood that Play on Linux was basically a front end for Wine. I could manually set up separate versions of wine for each game but so far that hasn't been necessary.

---

### Post by beastrace91 on 2010-01-29
> **Daddyo-613 said:**
> I get bumped out of the X session and the Ubuntu login screen appears.

Your not getting bumped out of the X session - X is crashing on you. Try downgrading your Wine version to an older one and see if it resolves the issue, many times this is the case for things such as this. Also perhaps try some newer graphics drivers if you are feeling adventurous.

Also FYI fantastic problem description in the first posting, everyone should start off their Wine questions like that :)

~Jeff

---

### Post by Daddyo-613 on 2010-01-29
Thanks for the encouragement. I just followed the guidance in the sticky as to how to ask a question. It's only common sense that you need to provide enough meaningful information about your system to allow someone to answer your question. I hope some of our friends out there will take a moment and think about how they're asking their questions. If each of us is a little more thoughtful about how we ask our questions it's more likely we'll get a thoughtful answer. 

You're quite right. I'm not being bumped out of the X session, the program is causing my X session to crash. Because the X session is crashing, even when I start RA2 using a terminal, I can't see where the sequence fails. I have suspected for some time that it's either a sound or video issue. I have noticed a greater tendency for RA2 to fail when I'm running Compiz instead of Metacity but my video card and the nVidia 185 driver should be able to handle both running at the same time.

I'll keep trying different settings and hope that I find a configuration that's stable. Wine 1.1.37 is so tantalizingly close to giving us the game design performance levels that I'm reluctant to downgrade. Please let me know if you have any other insights and thanks for your help.

~Stephen

---

### Post by beastrace91 on 2010-01-30
> **Daddyo-613 said:**
> I'm reluctant to downgrade. Please let me know if you have any other insights and thanks for your help.

Understandable, might I suggest taking a peek at the link in my signature titled "Running Multiple Wine Installs"? As following the guide there will allow you to install older Wine version(s) with out removing 1.1.37 :)

I'd be willing to bet most anything it is a Wine issue and not something with your graphics drivers causing the dump. That being said if you do any newer 3D gaming the 190.53 drivers offer a bit of a performance boost over the 185.xx.xx drivers I've noticed.

Cheers,
~Jeff

---

### Post by Daddyo-613 on 2010-03-13
**Update:** It's been over a month since I made the original post in this tread. We are now up to version 1.140 in Wine and the problem with RA2 Yuri crashing my X session has not improved. I am still unable to find a combination of settings using <winecfg> that allows RA2 to function consistently. It's particularly frustration because every once in a while a skirmish in RA2 will load properly.

**Question:** What I'd like to try is to approach the problem from the O/S side of the equation as opposed to just looking at my Wine settings. 
Can someone out there give me some information about which log files I should be looking at and what entries I should be looking for in order to determine why my X session is crashing?

There is an ".xsession-errors" file in my home directory and a long list of Log files using System->Administration->Log File Viewer, but I don't know which Logs are relevant or what type entries I should be looking for.

Any help from our friends would be appreciated.

**P.S.** I am reluctant to install Wine Tricks, mostly because it isn't consistent with the Linux open source approach, but also because I don't know which library overrides would help solve my problem. Philosophy is philosophy but getting a program to do your bidding...well that's another matter entirely. If Wine Tricks has a fix, please let me know.

---

### Post by Daddyo-613 on 2010-03-15
bump

---

### Post by Daddyo-613 on 2010-03-22
Good News! Red Alert 2 Yuri's Revenge is Back.

It appears that a combination of upgrades to Wine (now version 1.141) and installing the current nVidia driver for my GeForce 8600 GT (now NVIDIA UNIX x86 Kernel Module  195.36.15  released Thu Mar 11 21:41:46 PST 2010) has done the trick.

The game is operating normally even under Compiz with lots of eye candy configured. The Xsession no longer crashes when I exit the game.

I'll keep testing but is seems stable. Thanks everyone for your help.

---

### Post by texaswriter on 2010-03-23
Congratulations.

---

### Post by chmac on 2010-06-08
I have the same issue on Wine 1.1.42. I resolved it, quite accidentally, as follows:
Run winecfg > Graphics > Emulate a virtual desktop

Now Wine loads in a window, rather than resizing my desktop, which I much prefer. Also, when I exit, my X session survives. :-)

---

### Post by markus_b on 2010-06-12
Just to chime in and report that I have the same problem. RA2 Yuri starts up fine but starting a game makes X11 crash. I find myself back at the login screen.

RA2 works in VirtualBox, but graphics are slow.

---

### Post by texaswriter on 2010-06-12
> **markus_b said:**
> Just to chime in and report that I have the same problem. RA2 Yuri starts up fine but starting a game makes X11 crash. I find myself back at the login screen.

RA2 works in VirtualBox, but graphics are slow.

Did you try the above fix(es)?

---

### Post by markus_b on 2010-06-13
> **chmac said:**
> I have the same issue on Wine 1.1.42. I resolved it, quite accidentally, as follows:
Run winecfg > Graphics > Emulate a virtual desktop

Now Wine loads in a window, rather than resizing my desktop, which I much prefer. Also, when I exit, my X session survives. :-)
Yes, this works for me too. Performance is not better that in VirtualBox, though and there is no sound. Suppose I'll have to stop playing RA2, then. :-(

P.S. Somehow I missed the above hints, did not show up the way I came upon the thread via google.

---

### Post by chmac on 2010-06-13
markus_b, I've also decided that I need to stop playing RA2. It runs acceptably on Wine in it's own window, much better than through Virtualbox I think. I haven't experimented with the winecfg > Graphics > Allow DirectX apps to stop the mouse leaving their window setting. That might improve the gameplay slightly. I found that when the mouse was off the window, RA was scrolling endlessly.

I find the slight unresponsiveness and general slowness of the mouse as well as the squintiness of the graphics too much for me. I'm looking at Globulation and Warzone 2100, I think the gameplay is a bit easier on my setup.

---

