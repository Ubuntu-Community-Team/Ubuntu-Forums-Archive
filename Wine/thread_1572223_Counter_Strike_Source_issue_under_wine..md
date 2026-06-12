---
title: "Counter Strike: Source issue under wine."
date: 2010-09-10
forum: Wine
---

### Post by Ascent_NZ on 2010-09-10
Hi there guys,

Recently I have decided to start having play round with Ubuntu and have found these forums an indispensable resource.

After a few days spent fixing my many booting issues due to my windows dual boot overriding poor grub, I've now started on trying to get wine and windows games up and running. Now, this is purely a project so its not a "OMG CSS WONT WORK I'M GONNA DIE!" issue, more just a self assigned challenge.

Right, sorry for the fluff, let's begin.

System specs:
Compaq nx9420 Laptop
Intel Core2 Duo T2200 2.00GHz
2 GB DDR2 Memory
ATI Mobility Radeon X1600
OS: Ubuntu 10.04 and Windows XP Pro SP3
Wine: 1.1.42 (terminal output off)
Graphics Drivers: Open source ones automatically installed by Ubuntu
CS:S settings: Loaded with -dxlevel 80, graphics on low, 1680x1050 resolution (resolution has no effect on my issues)
Wine sound:ALSA (as I've read OSS no longer works due to Steam having its own sound)

Now CS:S runs fine under Windows, no problems.

Under Ubuntu, Steam runs (very sluggish but I'm not worried about that) and CS:S runs fine, the menu's are smooth and nice. However when I load up into a server, whether it be an online one or a self created one, thats when the issues arrise. 

Issue 1: Running around in a map is fine, no performance issue, but when I fire it lags to within inches of a freeze.

Issue2: I can see the map textures fine, however, model textures, gun textures, door textures and prop textures are an issues. Models, guns and doors are just simply not visible and prop textures and some small details are this uniform dirty sky blue colour.

Things tried:
1. Starting CS:S with different -dxlevel's
2. Reinstalling Steam and CS:S (hell, i've even done a completely fresh install of both Windows and Ubuntu, that's how I fixed the dual boot issues)
3. Differing graphics settings and resolutions
4. Banged head against desk furiously

Things I will try when I get home from work:
1.Try running with OSS sound instead of ALSA
2.Try updateing wine to 1.2
3.Try installing the proprietary graphics drivers

Just thought I would put a thread up as I haven't been able to find similar issues posted so thought I would get some feedback and possibly help others that may be having the same issue but haven't yet posted.

Cheers,

Mike

---

### Post by Ascent_NZ on 2010-09-11
Right so none of those helped any bit.

OSS just caused a game freeze.

Wine 1.2 had no effect.

Prop Drivers for the Mobiity X1600 apparently aren't supported by 10.04.

Looks like I'm close to chalking one up against me.

---

### Post by ronnielsen1 on 2010-09-11
It's rated platinum. It should work. Did you see the page at winehq? It will give you pointers

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)

> 
[LIST]
[*]When starting a game Steam throws an error saying **The registry was in use by another process**.       
See [Steam's HOWTO]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554") for possible solutions.
[*]**Counter Strike crashes as soon as it starts or you join a game.**       
You most likely have other program(s) using sound. Run winecfg and select only **ALSA** sound driver. OSS is not the best choice anymore.       
      
For Ubuntu 8.04 and up - **kill/disable pulseaudio**. It is not compatible with Wine. And will cause all sorts of problems if left running.       
      
Another possible reason - you have "Steam Community In-Game" enabled. It  does not work properly on Wine and causes all games to crash. Please  disable it in settings -> In-game tab.
[*]**MOTD/server description is not visible**.       
This is a know bug and is not yet fixed. Some text might be visible but most is not.
[*]**Voice communication doesn't work** (for some users).       
There are no known workarounds. Try using alsa as described bellow and using other voice communication software.
[*]**Steam [COLOR=red]will not work from ntfs[/COLOR] partition mounted using ntfs-3g driver (2.6.25 kernels and older)**       
This is a known limitation of the driver. Steam requires functionality  (mmap with shared write access) which Wine can not emulate if it's not  supported on file system. To fix: Install Steam and all content into  native Linux file system.
[*]**Game crashes after a few minutes. **You can fix this by putting [this file]("http://bugs.winehq.org/attachment.cgi?id=18679")  into your "~/.wine/drive_c/Program  Files/Steam/steamapps/YOURUSERNAME/counter-strike  source/cstrike/resource" folder, or by applying [this patch]("http://bugs.winehq.org/attachment.cgi?id=6853"). See [bug #7698]("http://bugs.winehq.org/show_bug.cgi?id=7698") for more information.
[*]**Lacking fonts. **You need Tahoma and Lucida  Console fonts for every text to show properly. Use winetricks to get  them if you don't have a windows install handy.
[*]**Game crash after a while **
To fix:
Run winecfg, click "Add application...", select "hl2.exe" (doesn't  matter which one, only the filename is used, not the path) and click  Open. Select "hl2.exe" in the list and change the "Windows version" to  "Windows 98".
[/LIST]


---

### Post by Ascent_NZ on 2010-09-11
Thanks for the reply ronnielsen1.

Hmm I did check there but didn't think any of those issues fitted mine. Still getting rid of my close minded Windowsness I guess :P

Ah well, it's worth a shot.

Will try when I get home from work:
1. Disable pulseaudio.
2. Disable Community In-Game (strange though because the part is what works best)
3. The add application fix/Setting to Win98.
4. Applying the patch for bug 7698.

I'll keep you guys updated.

---

### Post by sideaway on 2010-09-11
Sorry, but I gotta ask, are you affiliated with [Ascent]("http://ascent.co.nz") at all?

---

### Post by Ascent_NZ on 2010-09-11
Hehe, no I'm not. :)

---

### Post by Ascent_NZ on 2010-09-12
So I had some mild success.

1. Removing pulseaudio had no effect.
2. Turning off community in game had no effect.
3. Adding the application and setting to Win98 just crashed the game before the menu loaded.
3. Applying that file solved the textures issues but gave me an fps of around 0.25 (rough counting between screen shifts) in game and menus.

I also can't seem to get it run in any other resolution apart from 800x600, even putting the -w1680 -h1050 in the launch options.

I brought the -dxlevel down to 80 and still no good.

So I think I can conclude that my laptop is just plain to useless lol.

---

### Post by Ascent_NZ on 2010-09-12
Alright so the issue has nothing to do with anything other than the simple fact that my hardware is simply too old.

Tried running some linux native games and got that same fps issue as CS:S.

I'm fairly certain its the drivers but as I found out earlier, the proprietary ones for the Mobility Radeon X1600 are not compatible with Ubuntu 10.04.

---

### Post by sideaway on 2010-09-15
I'm convinced my ATi card just won't play ball :P

---

### Post by Ascent_NZ on 2010-10-02
Lol I'm of much the same mind. Your's should be fine though, I mean the 5870 is hardly sluggish lol. Do you have the open source drivers installed or the proprietary one?

I'm fairly sure its just the drivers in my case.

I installed Mandriva just for comparisons sake and the open source drivers were a little better, handling Quake Online and a few other online games which Ubuntu hadn't, but the prop drivers were still too old and weren't supported.

Looks like we'll just need to keep up with the times hardware wise too if we want the latest release of and Linux distro.

I haven't tried installing an older release of Ubuntu yet. I think Heron was the last one to support the drivers I need. Might be worth a test to confirm though.

---

### Post by jrs211 on 2011-04-25
hello... I was hoping for some help with a similar CS sound issue. I have spent the last couple of hours searching on the net for possible solutions but having little success. I am running Lucid and am trying to get CS to work. I have previously had it working fine but I think it was with Karmic. Right now when I 1st run CS it crashes almost immediately on the opening screen where the options/new game tabs etc are. After some reading it appears it has something to do with sound cofiguration in winecfg. I have tried with just ALSA selected - result is it crashes immediately. WIth OSS selected it doesn't crash but there is no sound. With EsounD selected there is sound but it is delayed. All very odd and I can't work out what to do...so I thought I'd ask for some help. Any would be appreciated.

---

### Post by nairatinu on 2011-04-30
I had an issue with hl2 games crashing on opening menu screen (as working fine until about 2 weeks ago).  Using steam, ubuntu (studio) 10.04, nvidia graphics card (not too old but not the latest), amd quad core.

Bottom line is adding "-novid" as a lauch option fixed the problem, so it appears to be a video config problem for me (I have no idea what "novid" means... I'll google it).

---

