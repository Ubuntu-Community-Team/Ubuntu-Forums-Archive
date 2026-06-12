---
title: "Team Fortress 2 how to: testers needed"
date: 2007-10-25
forum: Ubuntu Gamers Arena
---

### Post by cogadh on 2007-10-25
I wrote a how-to on installing and configuring TF2 in Wine (mostly from existing sources), but I need some TF2 owners to test it. If anyone would be willing to give it a shot and let me know if it needs any changes, it would be greatly appreciated:
[http://gaming.gwos.org/doku.php/wine:team_fortress_2](http://gaming.gwos.org/doku.php/wine:team_fortress_2)

EDIT - Also, I need some good screenshots to add to the doc. They must be shots of the game running in Wine, but they don't have to be in a Wine virtual desktop (if you tell me they were done with Wine, I'll just have to trust you :) ). If anyone has any, either post them as attachments here or contact me through PM and I'll give you an e-mail addy to send them to.

---

### Post by Technophobia on 2007-10-27
Bookmarked. My computer isn't powerful enough to run TF2, but in a few months I get to build a new system and this will be the first thing I try to run with wine.

---

### Post by Brandito101 on 2007-10-27
Well I did get the valve logo the first time. Brings up error:

> 
SteamStartup() failed: SteamStartup (0xf,0x0034E134) failed with error:
1: The registry is in use by another process, timeout expired


I'm new to linux (about a month or so), so the error could be on my part. Hope this helps,

Brandon

---

### Post by cogadh on 2007-10-27
That's a problem with Steam. Usually it can be fixed by cleanly exiting out of Steam (use File > Exit, not the "X" in the upper right corner of the app), then restarting it. I'll be adding that to the troubleshooting section of the Steam installation document.

---

### Post by Brandito101 on 2007-10-27
OK, now it goes through the Vavle logo then it changes my screen res to something like 320X200 and does nothing. I tried running wine with the virtual desktop and it basicly did the same thing. This time only to the virtual desktop. I'll try researching it on my own when I have time. 

Thanks

---

### Post by n3utrino on 2007-10-29
Hi all.

The resolution problem can be solved by setting the ingame resolution to the desktop resolution.

at least that worked for me.


i installed the steam version of tf2 and after several hours of downloading and decrypting it started smooth and easy.
but as soon as i click on the button to join the server wine crashes. but this issue seems to get adressed
[http://bugs.winehq.com/show_bug.cgi?id=9878](http://bugs.winehq.com/show_bug.cgi?id=9878)
and the bug should not occur on an earlier version of wine (0.9.44).

cheerio n3utrino

---

### Post by Snub_Fighter on 2007-11-02
I have an issue where it tries to force the game to start as dx6, at this point it then errors after the loading screen saying it requires dx8 or better to properly run. I've gone into Counter Strike source and found out it started source games as dx6 but I was able to force it to run 8.1, ran smooth probably some 60 fps no lag but there was a flicker, I'm assuming because I was trying to override the dlls to fix the dx6 issue which didn't work at all. So got any ideas to fix that, I have had compiz on and I've disabled it with the same problem just to rule that out as a possible cause.

Update had to compile wine to fix this issue... not sure what the difference is. Its a bit unstable however it has the crashing problem that all source games seem to have.

---

### Post by mattmarq on 2007-11-11
I recently upgraded from 7.04 to 7.10 and was ecstatic to see that compiz now worked with my ati x1700 video card. I had not been able to run any of my favourite steam games with 7.04 and now that compiz worked I thought they might. (counterstrike source, day of defeat source, the new TF2).

I followed your TF2 tutorial but I still get the same error and Brandito101:

SteamStartup() Failed: SteamStartup(0xf,0x0034E134) failed with error
1: The registry is in use by another process, timeoout expired

I am using WineVer: 0.9.47

any tips or recommendations??

---

### Post by cogadh on 2007-11-12
First off, don't run Compiz, it will conflict with Wine. Secondly, update to the latest Wine (0.9.49), there have been significant bugfixes in the last two updates, many of them directly related to Steam. If that doesn't fix the problem, post back and I'll see what else I can come up with.

---

### Post by ddevore on 2007-11-15
I have been working on this for a couple of days now and I can't seem to find what the problem is. 

Steam works find and the game starts to the loading screen but simply shuts down with no visible warning. At first it gave a warning about my video drivers but I checked the don't warn again box and I don't remember exactly what it said so I can't give the exact text.

Anyway any suggestions?

---

### Post by ddevore on 2007-11-15
Ok I got that working, I had to add the "-dxlevel 81" to the command. Now I would like to fix another problem. I have 2 monitors and would like to get it to run in a window but couldn't seem to get it change resolution so it would fit in one window. Any help?

---

### Post by yodul on 2007-12-01
Hello ,

Im just installed steam cs css and Team fortress 2

only Team Fortress 2 is not running.

"missing Direct X 8.0 minimum..."

Tried your how to and added the lines with regedit , but I got the sme error message.

---

### Post by cogadh on 2007-12-01
What version of Wine are you using and are there any error messages output to the terminal when you run it?

---

### Post by aaargh486 on 2007-12-07
OK, dx90 works, but really slow. 
dxlevel 81, everything maxed out works fine. I can play everything without problems or hangups.

My PC:
Pentium 4 3.2 GHz
NVIDIA GeForce 7600GT
1 GB RAM
Intel DG945CGNL motherboard


Thanks for the How-To,

Kasper

---

### Post by pfx on 2007-12-08
Runs for me with  0.9.50 but it's a lot slower than in Windows, the default settings are much lower, frame rates unplayable. 

Searched around and tried 0.9.46 and it's no different.

I used the Steam Download option but I just copied the steamapps folder from my windows partition into the wine folder.


Using the following:
E2140 @ 2.4
2gb ram
7900GS

Flawless in Windows...

---

### Post by estaticd on 2007-12-26
Good to see that my [guide]("http://www.fsckin.com/2007/10/15/how-to-run-team-fortress-2-half-life-2-hl2-ep-12-in-ubuntu-using-wine/") helped out a bit.  :)

Nice work.

---

### Post by jhunter on 2007-12-27
> **cogadh said:**
> If anyone would be willing to give it a shot and let me know if it needs any changes

The step requiring you to enter the video card memory could be more clear.  Is the size of memory supposed to be entered in MB?  KB?  B?  Should those numbers be MB (in the sense of MiB) or the 'new' MB?  Do you need to enter the unit suffix (does a user type '128' or '128MB')?

Everything else is pretty clear.  What about the Tahoma font problem?

---

### Post by tedk89 on 2008-01-02
no errors for me, steam gets loaded and tf2 starts and after I am connected to a game it hangs at the screen where it shows you how to play the map...

nvidia 8600m gt runs fine with restricted drivers
t7500 2.2ghz
4gb ram

running 7.10 64bit

keep up your good work!

---

### Post by tedk89 on 2008-01-02
ok, so I thought I setup steam correctly but decided to peruse your guide anyways...I set up my steam somewhat different.. But I saw the joke about outdated video card drivers and thought hey might as well update the restricted drivers and bang! tf2 works :) so do all my steam games :) nice work!

---

### Post by tedk89 on 2008-01-02
found a problem, but no error message. My sound stops working some times while running WINE I never have this issue if I dont start wine, when sounds stops working can be fixed by a restart although I have no idea why...

---

### Post by ODF on 2008-01-03
Works fine, had some problem with 

```
SteamStartup() Failed: SteamStartup(0xf,0x0034E134) failed with error
1: The registry is in use by another process, timeoout expired
```

Thanks to your fix it worked.

I can play the game, sound is working ... but it act like I have no 3d accelerator.

My vidéo card is : GeForce 8800 GTS and all drivers are installed.

Edit : It works but damn ... thats slow. I mean with a 8800 GTS you're supposed to play on 32 players server with high graphic settings. Now I'm all alone with these settings doing something like 20 fps =(

But thx, your thread really helped me in many many ways =)

---

### Post by rmores on 2008-01-07
I followed your guide and I can't get it to work, and i've been trying to get it working for over a week or 2 now.

I'm using wine 0.9.5.2 running a network install of TF2 and my system is a dual core AMD x64 with ATI X1650 512mb graphics card, running ATI 8.44.3 proprietary drivers, and configured correctly.

Any games under steam start and after the loading intro, they crash back to desktop. That and after a second try I get the infamous "the registry is in use by another process" that only fixes after a system restart.(wineserver -k doesn't do the trick for me)


I have disabled friends and any other possible crap in Steam already. 

running "wine hl2.exe -game tf -dxlevel 70 -width 1280 -height 1024" , i get this output: 

```
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 17/02/2008, dlt (d/m/y): 12/10/2008 
fixme:win:EnumDisplayDevicesW ((null),0,0x34e2d8,0x00000000), stub! 
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub! 
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub! 
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered 
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1 
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub 
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present 
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x131918) Event query: Unimplemented, but pretending to be supported 
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x131918) Event query: Unimplemented, but pretending to be supported 
fixme:process:IsWow64Process (0xffffffff 0x34db84) stub! 
fixme:avifile:AVIFileExit (): stub!
```

---

### Post by savethejets on 2008-01-31
have you tried updating to wine 0.9.54? It solved the problem of not being able to get to the main menu for me.

However now it just crashes at the loading main menu screen. A little closer, but not quite there yet. Hopefully this will be fixed soon.

---

### Post by SoulSmasher on 2008-02-04
with wine 0.9.4.6 it's ok until game opens (i mean, it shows valve's logo , but it gets back to desktop)

now will update wine and check again... (btw, i'm using mobility radeon x1300, driver updated with envy)

edit: with wine 0.9.5.4 the loading never finishes, so i have to kill the process with "wineserver -k" command...

anyone managed to play ?

**final edit: i managed to open :) check [here]("http://ohioloco.ubuntuforums.org/showpost.php?p=4270444&postcount=11") **

---

### Post by dew5 on 2008-02-21
> **ddevore said:**
> I have been working on this for a couple of days now and I can't seem to find what the problem is. 

Steam works find and the game starts to the loading screen but simply shuts down with no visible warning. At first it gave a warning about my video drivers but I checked the don't warn again box and I don't remember exactly what it said so I can't give the exact text.

Anyway any suggestions?

hey guys

I am having the same problem as you ddevore.

Because i did not check the " don't show this message again " box, I can tell you the message reads:

"Your video drivers appear to be out of date and could cause problems if you choose to continue and run the game.  We strongly recommend that you follow the link below and update your video drivers to the latest version available from your driver vendor.


Your driver details

Windows Version:                      Windows XP
Description:                              Direct3D HAL
Version:                                    6.14.7.0"

How ever steam is running at this stage. I am able to access all options for steam (i.e Games, Store, Friends, setting etc). I have even been able to generate a servers listing. Now, at that point attempting to launch the game(cs:s, DOD, TF2) results in the game shutting down with no warning as stated above by ddevore.

Please help.
dew5

---

### Post by SoulSmasher on 2008-03-10
anyone managed to get with wine 0.9.5.7 successfully ???

---

### Post by neoMAX on 2008-03-13
TF2 runs great for me in wine except it has hiccups of 1-2second lags every 5 to 7 seconds =]

---

### Post by getup kid on 2008-05-06
once i muster up the courage to install ubuntu, and get steam and tf2 ill report back on my finds.

---

### Post by SoulSmasher on 2008-05-06
well, it still freezes at me after a couplke of time with latest version of ati drivers installed with envy and latest version with wine, hope it is solved

---

### Post by zspace on 2008-09-13
I just switched completely from windows to Ubuntu 8.04, and this was the only game I ever played so I'm glad it works.
I got it downloaded and installed, and steam itself runs fine (minus a few little bugs in the updates pop up), but when I try to launch TF2 it crashes (steam crashes too, game hasn't even shown up yet). I tried turning Compiz off and that had no effect, I'm going to try the -dxlevel 81 thing someone suggested and see if that helps, I got the latest drivers I think (just installed everything about four days ago), so I'll be back some time to let you know how it went.

---

