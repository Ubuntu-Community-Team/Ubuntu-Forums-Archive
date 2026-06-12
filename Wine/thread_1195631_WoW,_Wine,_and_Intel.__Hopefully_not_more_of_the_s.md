---
title: "WoW, Wine, and Intel.  Hopefully not more of the same."
date: 2009-06-24
forum: Wine
---

### Post by SamikMTBSI on 2009-06-24
Hi - long time lurker first time poster etc.

I know there are a thousand WoW/wine threads (I've read most of them), but I've yet to find one that describes my symptoms exactly.  Hopefully my problem is different enough to warrant it's own thread.  If not, I apologize.

For what it's worth, I think I've done quite a lot of the legwork, so please read a bit before simply linking to one of the basic how-tos.

This is very long - for that I'm sorry.  I'm just completely flummoxed, so I thought that it would be best to include anything that might be even remotely related to the problem.

If you're up for it, then please, read on!

----------

Format:
1.) First I will list some relevant information about my system. 
2.) Then I will describe what I have tried thus far.
3.) Then, I will describe the exact behavior of the game in the best configuration.
4.) Lastly, I will ask my questions.

--------

[SIZE=2]**Part 1 - my relevant specs:**[/SIZE]


**-** Wine version 1.1.23.

**-** Ubuntu 9.04 (Issue is exactly replicatable with 8.10, which seems anomolous, from what I've read.  Game fails to even load in 8.04 under any circumstances, which seems even more anomolous.).

**-** 82g31 - intel gma 3100 - currently using the 2.7 driver.  Have used 2.6 and 2.4, with identical results.

**-** Celeron 430 - 1.8GHz - 2GB DDR2-800.  (I'm poor, have played WoW on much worse hardware, and am perfectly happy with 20fps on a good day, so please no buy-a-better-gpu comments.)

**-** glxinfo | grep direct
  get fences failed: -1 *
  param: 6, val: 0
  direct rendering: Yes
  
*(I have not been able to determine what this means.)

 **-** Using any functioning configuration, I get around 1100-1300 flawless fps in glxgears, and 60-80 in PPRacer.  Video of all varieties, and all other kind of media I've run into thus far, run beautifully.


[SIZE=2]**Part 2 - what I've done so far:**[/SIZE]


If there's a thread or guide on how to do it, I've tried it, including:

**a.)** Many winecfg tweaks: Setting to every version of Windows.  Pixel shader on and off.  Vertex shader hardware and none.  "Allow the window manager to control the windows" on and off.  "Allow the window manager to decorate the windows" on and off.  Alsa (casues no problems I've detected) and OSS.

**b.)** Many registry tweaks: OffscreenRenderingMode undefined and set to backbuffer.  UseGLSL enabled and disabled.  The OpenGL DisabledExtensions GL_ARB_vertex_buffer_object tweak.  Others I cannot remember.

**c.)** xorg.conf edits: AccelMethod set to UXA, EXA, XXA, and undefined (as well as altering a few settings with these based on recommendations, which I cannot now recall).  EXAOptimizeMigration set to true, false, and undefined.  MigrationHeuristic set to greedy and undefined.  Tiling set to true, false, and undefined.  Others I cannot now remember.

**d.)** Config.WTF edits:  SET gxApi "opengl" and "d3d" (redundant, I know).  SET ffxDeath "0".  SET ffxGlow "0".  SET Sound_SoundOutputSystem "1".  SET Sound_SoundBufferSize "150".

**e.)** terminal modifiers:  adding -opengl tag, -d3d tag, and running with WINEDEBUG=-all.

**e.)** Completely uninstalling wine and WoW, and starting again.

**f.)** Against recommendations, using winetricks to download d3dx9.

**g.)** The more complicated fixes suggested at:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) (tried "safe" and "optimal" configurations.)
[http://ubuntuforums.org/showthread.php?t=1136738](http://ubuntuforums.org/showthread.php?t=1136738)
- As well as all the basic how-to's, such as:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)
[http://www.wowwiki.com/Wine](http://www.wowwiki.com/Wine)
Etc.  (So please, no posts simply linking to these.)

**h.)** Newer drivers, older drivers.  Newer kernels, older kernels.  Ubuntu 8.10 and 8.04.

**i.)** More I'm sure I'm forgetting.


**[SIZE=2]Part 3 - My current configuration and the behavior I'm experiencing:[/SIZE]**

- As previously mentioned, everything else runs more or less beautifully.  I have compiz disabled due to personal preference (the spartan look and feel of Ubuntu was one of the primary appeals for me).  Again, ~1200fps in glxgears, and 60-80 in PPRacer.  I have no other more 3d graphically demanding games on which to test.

- I am currently using the 2.7 intel drivers, with no noticeable difference in any application over 2.6.  I am running the game in DirectX mode, because OpenGL mode exhibits the same complete garbling of graphics that many others have reported.  Nothing I've attempted has been able to fix this in the slightest.

- RE: the registry and winecfg:  I have OffscreenRenderingMode set to backbuffer.  PixelShaderMode set to disabled.  VertexShaderMode set to none.  Sound set to ALSA unproblematically.  "Allow the window manager..." options both deselected.

- RE: xorg.conf:  EXAOptimizeMigration: True.  MigrationHeuristic: greedy.  No other options defined at the moment.

I only include these settings for reference - it should be noted that, for the most part, modifying the xorg.conf with any of the recommended edits, editing the registry and winecfg, switching between drivers/kernels, and nearly all other tweaks attempted, have produced absolutely no visible difference whatsoever (with the exception of switching between opengl and d3d, and pixel and vertex shader mode - when both of these last two are enabled, the graphics are garbled badly.  When one (doesn't matter which) or none are selected, the graphics are fine).
  


*The best behavior I have been able to manage so far is as follows: *

- Perfectly clear image - none of the terrain issues, flashing, missing polygons, etc. that other have dealt with on similar hardware.
- Between 0.5 and 1 fps in unpopulated, open areas, with all grpahical settings at lowest.
- During the limited in-game testing I've been able to accomplish under these circumstances, I have not experienced any crashes (except when I try to modify some of the video settings).

I know this is not optimal for my hardware.  As previously mentioned, I've played WoW on worse, and I've read of many people with similar or worse hardware getting WoW to successfully work on Ubuntu with Wine.

I do not believe that I have any of the greater intel chip related bugs that so many have had to deal with, for two reasons:  1.) everything else works great.  Individuals tackling some of the major bugs experience degraded performance in other areas - compiz, ppracer, video playback - which I do not.  2.) None of the fixes for these bugs have resulted in any performance improvement or degradation whatsoever.

My current understanding of the problem suggests to me that the conflict is, very simply, this:

[I]- Wine doesn't cooperate with DirectX, and
- Intel chips don't cooperate with OpenGL in Ubuntu.[/I]

My testing has led me to believe that there isn't really very much else coming in to play here (please correct me if I'm wrong!).

What baffles me, if this is true, however, is this:  How is it that I can seem to have absolutely *none* of the myriad greater issues typically associated with intel chips, and yet, in wine, have performance so *much worse* than any of the others who have not had said problems?

Thus come my questions:



**[SIZE=2]Part 4 - My questions:[/SIZE]**

1.) First thing's first: if anyone out there has gotten WoW to play passably on a GMA 3100 or worse, under DirectX OR OpenGL..... what in the #&!! did you do to make it work?!  (I've read of some people using very simple fixes, such as the intel-related fixes mentioned here: [https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting).  Obviously, these and others like them did not work for me, so ideally I would like to hear from someone with similar hardware who had all sorts of trouble that couldn't be fixed by such simple modifications, like me, but was eventually able to get things working nonetheless.)

2.) Is there any way whatsoever to tackle the problem directly by either making wine understand DirectX better, or making my intel chip handle OpenGL better?  I've read of third-party intel drivers that allow OpenGL to be used more smoothly, but I have been completely unable to track such a thing down.  Any leads?

3.) Are there any other avenues of assault that I have not tried?


As always, if there's any info I've left out that could be useful, please ask, and all suggestions are welcome, no matter how off-the-wall!

---

### Post by SamikMTBSI on 2009-06-24
bump/sob


Looking back at it, perhaps I really should have made a better effort about condensing my thoughts.  Never really did take well to all the emphasis they put on 'conciseness' in school...

---

### Post by SamikMTBSI on 2009-06-25
Because I had some time to kill, and wanted some kind of baseline, I decided to go and try to boot WoW on the only other computer I had available:  

- A 2001 IBM Thinkpad 
- 1GHz Pentium III 
- 256MB RAM @ 100MHz (was 128 'til I did some scavenging)
- 8MB vidram (ATI Rage Mobility M, with some sketchy third party drivers)
- booting off an external HDD connected via USB1 (cause the thing's hard drive couldn't even fit the whole game).


The lappy overheated and shut down right as the loading screen was about to finish (in 8 years I've not cleaned out the fans once, or done any other kind of internal health maintenance, so it's running at about 55C idle 60C light load - it's been an emergency backup, hauled out of the closet once or twice a year for the last four), but it should be noted that through the login screen and character selection screen I was getting significantly better framerates than on my main machine under Wine.

So, suffice to say, I'm sufficiently convinced that the hardware described in the first post is capable of better than I've experienced.




While I wait for answers/my buddy potentially scavenging an ancient Nvidia chip from dead computers at his work, I'm going to tear the IBM apart, try to clean up and reseat the cpu fan with some better paste, and blow out those fans finally. :D





P.S. Every time I have need to drag this Thinkpad out of the closet I bemoan the fact that IBM doesn't still make their own laptops.  This thing has been absolutely beastly throughout the years.  I dropped it on a linoleum floor once from about waist height - the cd tray popped out and skipped across the room into a wall - that and much more and it keeps on ticking.  It's survived three intervening laptops, and will probably outlast the machine I'm using now...

---

### Post by SamikMTBSI on 2009-06-25
It's official.

- On 1GHz Pentium III,
- 256MB RAM @ 100 MHz
- 8MB vidram
- Windows 2000

I get about 3 fps in the wild, and 10-15 indoors (needless to say, not going to even try cities).  Seemingly stable - no crashes after a pretty fair deal of poking around and tweaking settings.


Not claiming this is playable, but hopefully some time somewhere, when someone tells someone else they can't play WoW on their Conroe Celeron and integrated Intel graphics within ANY OS, that person will be able to point back to this and say, "Oh yeah?"


I'm giving up on getting the game to run in Ubuntu for the time being (not giving up on Ubuntu - just WoW), so I'll finally let this thread sink slowly into oblivion...





(Hey, if nothing else, I had a lot more fun trying to get it to run on this machine than on my desktop!)

---

### Post by mony87 on 2009-06-30
Have X3100... Trying to play WoW... I'm very close to the moment, when i will destroy this f**** laptop.. I tried everything you did.. and nothing.. So i haven't used windows for many years and don't know if Wow+windows+x3100 runs well, but tested on the same machine OS X (well hackintosh..)+ wow(native port for OS X) and it runs perfect at low details. No lag, no crap, just runs. PS. I have Crossover installed and with it - no difference.

---

### Post by Monkey Brawler on 2009-07-13
Dude, i have tried everything, i have the same graphics chipset and i have NO luck, reg tweaks, cfg file. If theres anything i can do to help PLEASE let me know, im kinda missing my wow. The answer to the windows working on wow with the x3100 chipset is yes, i got 15-30 fps when i was running xp.

---

### Post by Monkey Brawler on 2009-07-14
You all may want to take this post into consideration tho, im doing this for sheer sport and the fact i like my Jaunty :P [http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html](http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html)

---

