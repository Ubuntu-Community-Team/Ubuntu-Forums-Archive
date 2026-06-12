---
title: "WoW on Jaunty, multiple errors (crashing)"
date: 2009-08-28
forum: Wine
---

### Post by Desolator64 on 2009-08-28
Hello!

I recently installed WoW and got everything updated after many hours of hard work and troubleshooting. Everything starts up fine but once I get into the game I get a few errors. Mainly, my game will crash after a few seconds giving me this error:

```
============================================================================== 
World of WarCraft (build 10192) 
 
Exe:      C:\Program Files\World of Warcraft\WoW.exe 
Time:     Aug 28, 2009 12:52:30.887 PM 
User:     ricky 
Computer: ricky 
------------------------------------------------------------------------------ 
 
This application has encountered a critical error: 
 
ERROR #132 (0x85100084) Fatal Exception 
Program:    C:\Program Files\World of Warcraft\WoW.exe 
Exception:    0xC0000005 (ACCESS_VIOLATION) at 0073:B7CEF896 
 
The instruction at "0xB7CEF896" referenced memory at "0x00000000". 
The memory could not be "read". 
 
 
WoWBuild: 10192 
Settings:  
SET readTOS "-1" 
SET readEULA "-1" 
SET readScanning "-1" 
SET readContest "-1" 
SET hwDetect "0" 
SET gxRefresh "60" 
SET gxMultisampleQuality "0.000000" 
SET gxFixLag "0" 
SET farclip "350.000000" 
SET specular "1" 
SET movie "0" 
SET realmList "us.logon.worldofwarcraft.com" 
SET locale "enUS" 
SET expansionMovie "0" 
SET readTerminationWithoutNotice "-1" 
SET showToolsUI "1" 
SET coresDetected "2" 
SET videoOptionsVersion "2" 
SET Sound_OutputDriverName "System Default" 
SET UIFaster "2" 
SET gxApi "opengl" 
SET SoundOutputSystem "1" 
SET SoundBufferSize "100" 
SET installType "Retail" 
SET patchlist "us.version.worldofwarcraft.com" 
SET Gamma "1.000000" 
SET Sound_MusicVolume "0.40000000596046" 
SET Sound_AmbienceVolume "0.60000002384186" 
SET projectedTextures "1" 
 
---------------------------------------- 
               GxInfo 
---------------------------------------- 
GxApi: OpenGl 
Vendor: Tungsten Graphics, Inc 
Renderer: Mesa DRI Intel(R) 965GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2 
Version: 2.0 Mesa 7.4 
 
------------------------------------------------------------------------------ 
 
---------------------------------------- 
    x86 Registers 
---------------------------------------- 
 
EAX=00000000  EBX=7E16AFF4  ECX=00000003  EDX=00000001  ESI=00000000 
EDI=78249FA0  EBP=0039F8E0  ESP=0039F8A0  EIP=B7CEF896  FLG=00010246 
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B 
 
 
---------------------------------------- 
    Stack Trace (Manual) 
---------------------------------------- 
 
Address  Frame    Logical addr  Module 
 
Showing 9/9 threads... 
 
--- Thread ID: 12 --- 
**** Unable to retrieve thread context, error: 5 
 
--- Thread ID: 13 --- 
**** Unable to retrieve thread context, error: 5 
 
--- Thread ID: 11 --- 
**** Unable to retrieve thread context, error: 5 
 
--- Thread ID: 71 --- 
**** Unable to retrieve thread context, error: 5 
 
--- Thread ID: 70 --- 
**** Unable to retrieve thread context, error: 5 
 
--- Thread ID: 69 --- 
**** Unable to retrieve thread context, error: 5 
 
--- Thread ID: 68 --- 
**** Unable to retrieve thread context, error: 5 
 
--- Thread ID: 67 --- 
7B890472 01DEEA04 0001:0006F472 C:\windows\system32\KERNEL32.dll 
7B8904B5 01DEEA24 0001:0006F4B5 C:\windows\system32\KERNEL32.dll 
007071A5 01DEEA44 0001:003061A5 C:\Program Files\World of Warcraft\WoW.exe 
0071DCEA 01DEEA58 0001:0031CCEA C:\Program Files\World of Warcraft\WoW.exe 
00844C4F 01DEEA90 0001:00443C4F C:\Program Files\World of Warcraft\WoW.exe 
00844CF4 01DEEAA8 0001:00443CF4 C:\Program Files\World of Warcraft\WoW.exe 
7BC6BD60 01DEEB78 0001:0005AD60 C:\windows\system32\ntdll.dll 
7BC73F2B 01DEF3B8 0001:00062F2B C:\windows\system32\ntdll.dll 
B7DE04FF 01DEF4B8 0000:00000000 <unknown> 
 
--- Thread ID: 50 [Current Thread] --- 
B7CEF896 0039F8E0 0000:00000000 <unknown> 
7DF6DBD4 0039FA40 0000:00000000 <unknown> 
7DF793CC 0039FA70 0000:00000000 <unknown> 
7DF6CE26 0039FB00 0000:00000000 <unknown> 
7E026DD0 0039FB50 0000:00000000 <unknown> 
7EE47CEA 0039FB80 0001:00056CEA C:\windows\system32\opengl32.dll 
0061F6F2 0039FBA0 0001:0021E6F2 C:\Program Files\World of Warcraft\WoW.exe 
00428B8B 0039FBB0 0001:00027B8B C:\Program Files\World of Warcraft\WoW.exe 
00608B18 0039FCCC 0001:00207B18 C:\Program Files\World of Warcraft\WoW.exe 
0061F323 0039FCEC 0001:0021E323 C:\Program Files\World of Warcraft\WoW.exe 
0044E45F 0039FDA4 0001:0004D45F C:\Program Files\World of Warcraft\WoW.exe 
00426DE9 0039FDD4 0001:00025DE9 C:\Program Files\World of Warcraft\WoW.exe 
00423FB9 0039FE00 0001:00022FB9 C:\Program Files\World of Warcraft\WoW.exe 
0042544A 0039FE54 0001:0002444A C:\Program Files\World of Warcraft\WoW.exe 
00425491 0039FE6C 0001:00024491 C:\Program Files\World of Warcraft\WoW.exe 
00406CFD 0039FF08 0001:00005CFD C:\Program Files\World of Warcraft\WoW.exe 
7B878680 0039FFE8 0001:00057680 C:\windows\system32\KERNEL32.dll 
 
---------------------------------------- 
    Stack Trace (Using DBGHELP.DLL) 
---------------------------------------- 
 
```

I have added "SET gxApi "opengl" to my Config.wtf file so I'm running things under OpenGL just fine. When I try d3d mode everything turns black and crashes before I can get in game.

Also, once I'm in game  the whole world kind of drags across the screen while I hold down any of my mouse buttons, leaving trails of everything behind. They disappear when I release the mouse button but obviously it's still annoying.

Lastly, things are overall quite laggy. I used to play WoW on decent settings back when this was a Windows computer just fine so I know that my computer can handle the game. I'm sure the pseudo-emulation of Wine alone can't be slowing it down this drastically.

---

### Post by Desolator64 on 2009-08-28
Oh, and I also have already entered the registry key in "HKEY_CURRENT_USER\Software\Wine\" that supposedly fixes crash issues.

---

### Post by donkyhotay on 2009-08-28
Try posting this within the [wine sub-forum](http://ubuntuforums.org/forumdisplay.php?f=313). You'll get better results if you post in the correct area.

---

### Post by Desolator64 on 2009-08-28
Oh good idea. Thanks.

---

### Post by Desolator64 on 2009-08-28
Hello!

I recently installed WoW and got everything updated after many hours of hard work and troubleshooting. Everything starts up fine but once I get into the game I get a few errors. Mainly, my game will crash after a few seconds giving me this error:

```
============================================================================== 
World of WarCraft (build 10192) 
 
Exe:      C:\Program Files\World of Warcraft\WoW.exe 
Time:     Aug 28, 2009 12:52:30.887 PM 
User:     ricky 
Computer: ricky 
------------------------------------------------------------------------------ 
 
This application has encountered a critical error: 
 
ERROR #132 (0x85100084) Fatal Exception 
Program:    C:\Program Files\World of Warcraft\WoW.exe 
Exception:    0xC0000005 (ACCESS_VIOLATION) at 0073:B7CEF896 
 
The instruction at "0xB7CEF896" referenced memory at "0x00000000". 
The memory could not be "read". 
 
 
WoWBuild: 10192 
Settings:  
SET readTOS "-1" 
SET readEULA "-1" 
SET readScanning "-1" 
SET readContest "-1" 
SET hwDetect "0" 
SET gxRefresh "60" 
SET gxMultisampleQuality "0.000000" 
SET gxFixLag "0" 
SET farclip "350.000000" 
SET specular "1" 
SET movie "0" 
SET realmList "us.logon.worldofwarcraft.com" 
SET locale "enUS" 
SET expansionMovie "0" 
SET readTerminationWithoutNotice "-1" 
SET showToolsUI "1" 
SET coresDetected "2" 
SET videoOptionsVersion "2" 
SET Sound_OutputDriverName "System Default" 
SET UIFaster "2" 
SET gxApi "opengl" 
SET SoundOutputSystem "1" 
SET SoundBufferSize "100" 
SET installType "Retail" 
SET patchlist "us.version.worldofwarcraft.com" 
SET Gamma "1.000000" 
SET Sound_MusicVolume "0.40000000596046" 
SET Sound_AmbienceVolume "0.60000002384186" 
SET projectedTextures "1" 
 
---------------------------------------- 
               GxInfo 
---------------------------------------- 
GxApi: OpenGl 
Vendor: Tungsten Graphics, Inc 
Renderer: Mesa DRI Intel(R) 965GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2 
Version: 2.0 Mesa 7.4 
 
------------------------------------------------------------------------------ 
 
---------------------------------------- 
    x86 Registers 
---------------------------------------- 
 
EAX=00000000  EBX=7E16AFF4  ECX=00000003  EDX=00000001  ESI=00000000 
EDI=78249FA0  EBP=0039F8E0  ESP=0039F8A0  EIP=B7CEF896  FLG=00010246 
CS =0073      DS =007B      ES =007B      SS =007B      FS =0033      GS =003B 
 
 
---------------------------------------- 
    Stack Trace (Manual) 
---------------------------------------- 
 
Address  Frame    Logical addr  Module 
 
Showing 9/9 threads... 
 
--- Thread ID: 12 --- 
**** Unable to retrieve thread context, error: 5 
 
--- Thread ID: 13 --- 
**** Unable to retrieve thread context, error: 5 
 
--- Thread ID: 11 --- 
**** Unable to retrieve thread context, error: 5 
 
--- Thread ID: 71 --- 
**** Unable to retrieve thread context, error: 5 
 
--- Thread ID: 70 --- 
**** Unable to retrieve thread context, error: 5 
 
--- Thread ID: 69 --- 
**** Unable to retrieve thread context, error: 5 
 
--- Thread ID: 68 --- 
**** Unable to retrieve thread context, error: 5 
 
--- Thread ID: 67 --- 
7B890472 01DEEA04 0001:0006F472 C:\windows\system32\KERNEL32.dll 
7B8904B5 01DEEA24 0001:0006F4B5 C:\windows\system32\KERNEL32.dll 
007071A5 01DEEA44 0001:003061A5 C:\Program Files\World of Warcraft\WoW.exe 
0071DCEA 01DEEA58 0001:0031CCEA C:\Program Files\World of Warcraft\WoW.exe 
00844C4F 01DEEA90 0001:00443C4F C:\Program Files\World of Warcraft\WoW.exe 
00844CF4 01DEEAA8 0001:00443CF4 C:\Program Files\World of Warcraft\WoW.exe 
7BC6BD60 01DEEB78 0001:0005AD60 C:\windows\system32\ntdll.dll 
7BC73F2B 01DEF3B8 0001:00062F2B C:\windows\system32\ntdll.dll 
B7DE04FF 01DEF4B8 0000:00000000 <unknown> 
 
--- Thread ID: 50 [Current Thread] --- 
B7CEF896 0039F8E0 0000:00000000 <unknown> 
7DF6DBD4 0039FA40 0000:00000000 <unknown> 
7DF793CC 0039FA70 0000:00000000 <unknown> 
7DF6CE26 0039FB00 0000:00000000 <unknown> 
7E026DD0 0039FB50 0000:00000000 <unknown> 
7EE47CEA 0039FB80 0001:00056CEA C:\windows\system32\opengl32.dll 
0061F6F2 0039FBA0 0001:0021E6F2 C:\Program Files\World of Warcraft\WoW.exe 
00428B8B 0039FBB0 0001:00027B8B C:\Program Files\World of Warcraft\WoW.exe 
00608B18 0039FCCC 0001:00207B18 C:\Program Files\World of Warcraft\WoW.exe 
0061F323 0039FCEC 0001:0021E323 C:\Program Files\World of Warcraft\WoW.exe 
0044E45F 0039FDA4 0001:0004D45F C:\Program Files\World of Warcraft\WoW.exe 
00426DE9 0039FDD4 0001:00025DE9 C:\Program Files\World of Warcraft\WoW.exe 
00423FB9 0039FE00 0001:00022FB9 C:\Program Files\World of Warcraft\WoW.exe 
0042544A 0039FE54 0001:0002444A C:\Program Files\World of Warcraft\WoW.exe 
00425491 0039FE6C 0001:00024491 C:\Program Files\World of Warcraft\WoW.exe 
00406CFD 0039FF08 0001:00005CFD C:\Program Files\World of Warcraft\WoW.exe 
7B878680 0039FFE8 0001:00057680 C:\windows\system32\KERNEL32.dll 
 
---------------------------------------- 
    Stack Trace (Using DBGHELP.DLL) 
---------------------------------------- 
 
```I have added "SET gxApi "opengl" to my Config.wtf file so I'm running things under OpenGL just fine. When I try d3d mode everything turns black and crashes before I can get in game. I also have already entered the registry key in "HKEY_CURRENT_USER\Software\Wine\" that supposedly fixes crash issues.

Also, once I'm in game the whole world kind of drags across the screen while I hold down any of my mouse buttons, leaving trails of everything behind. They disappear when I release the mouse button but obviously it's still annoying.

Lastly, things are overall quite laggy. I used to play WoW on decent settings back when this was a Windows computer just fine so I know that my computer can handle the game. I'm sure the pseudo-emulation of Wine alone can't be slowing it down this drastically.

---

### Post by Desolator64 on 2009-08-28
Reposted:  [http://ubuntuforums.org/showthread.php?p=7861699#post7861699](http://ubuntuforums.org/showthread.php?p=7861699#post7861699)

---

### Post by HH60Gunner on 2009-08-28
Have you added winehq.orq's repository and updated your wine to the latest one possible?  I know when I first installed wow on my box I had lots of crashes and bad performance.  Than someone hinted to me to update my wine to the latest one available from winehq.org.  After doing so my wow on linux ran better than it did when I used to play it on windows.  The framerates I was getting was alot higher than it had previously been on windows.  Just make sure you don't use compiz or anything like that.  I know after I did the cube thing when I was first getting into linux it made wow run horrible.  So I took it off and now all runs good again.

---

### Post by Desolator64 on 2009-08-28
Thanks for the response!

Yes, I have the latest version of wine. I actually started the installation with the second most recent but had to update because there was a bug that wouldn't let me accept the EULA.  :P

---

### Post by hikaricore on 2009-08-28
> Vendor: Tungsten Graphics, Inc 
Renderer: Mesa DRI Intel(R) 965GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2 
Version: 2.0 Mesa 7.4 

Your chipset probably has crap OpenGL support.  There may not be much you can do.

---

### Post by Desolator64 on 2009-08-28
That does make a lot of sense. I'm going to look around and see if maybe there's a third party driver that can fix that. Think that's a possibility?

---

### Post by Desolator64 on 2009-08-28
I followed the instructions here to roll back my driver because apparently it was a lot more stable in earlier versions:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4/](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4/)

There was little effect. I was able to jump around for a good 30 seconds but it would still crash.

---

### Post by bapoumba on 2009-08-29
Threads merged.

---

### Post by jasonditz on 2009-08-30
I have the same chipset (965) and roughly the same problem. I haven't tried reverting the drivers but here's something else you can try:

Set gxApi "d3d" (I see you did that before and it crashed but bear with me) AND

Set gxResolution "" (whatever your default screen resolution is, eg "1440x900")

When I did this the game will load and is almost playable, but I'm still trying to track down a weird graphics glitch. Maybe with your revert you'll have more luck with it?

---

### Post by Desolator64 on 2009-08-31
Thank you for the merge!

I tried what you suggested. I ran it with d3d and my resolution set to 1280x800. I'm not sure if that's the resolution I should have used though. Running xrandr in terminal gives me:
```

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  

```I just set the resolution in the config file to match my current resolution. I'm going to try messing around with different resolutions and see if there's any kind of change. As of now I run the game and get this:

[IMG]http://img255.imageshack.us/img255/8500/wowd3d.png[/IMG]



If that fails to work them I'm going to try updating my driver back to the newest one and trying it again.

---

### Post by Desolator64 on 2009-08-31
I was able to get into the game just by memory of what to type and when. When I got in, the game updated my config.wtf file and replaced SET gxApi "d3d" with SET gxApi "D3D9". I don't know if this makes a difference but I'm just making note of it.

---

### Post by Desolator64 on 2009-08-31
[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#Intel%20950%20(and%20most%20certainly%20other%20DRI-based%20drivers](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#Intel%20950%20(and%20most%20certainly%20other%20DRI-based%20drivers))


Problem solved! Apparently this is some type of exception in which the game needs to be run with DirectX. The game works great with no bugs as far as I've seen. The only problem I've come across was the low framerate. I'll work on this some more and hopefully get it to be fully playable.

---

### Post by jasonditz on 2009-08-31
> **Desolator64 said:**
> [https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#Intel%20950%20(and%20most%20certainly%20other%20DRI-based%20drivers](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting#Intel%20950%20(and%20most%20certainly%20other%20DRI-based%20drivers))


Problem solved! Apparently this is some type of exception in which the game needs to be run with DirectX. The game works great with no bugs as far as I've seen. The only problem I've come across was the low framerate. I'll work on this some more and hopefully get it to be fully playable.

When you say "low framerate" what are you getting? I managed to get the game the work by disabling the shaders too (actually I think you can leave Vertex Shader on Hardware, its the other one that screws up the graphics) but even running in Windowed Mode at 800x600 with everything turned to bare minimum effects I was still getting 7 fps when I'm standing still and it drops to 1 the second I try to move.

I'm still holding out hope that somewhere in there is a secret "work better" setting that's going to make it run at least as well as it does on my dramatically inferior MacMini hardware.

---

### Post by jasonditz on 2009-08-31
> **Desolator64 said:**
> I was able to get into the game just by memory of what to type and when. When I got in, the game updated my config.wtf file and replaced SET gxApi "d3d" with SET gxApi "D3D9". I don't know if this makes a difference but I'm just making note of it.

That seems to be a weird quirk of Wow's... I had it change "d3d" to "direct3d" the first time I played then also to "D3D9"... I don't think it's changing anything in game (and certainly not doing anything to improve performance).

---

### Post by raronson on 2009-08-31
Backing when playing WoW on Linux was a hobby of mine, I found that using Cedega was the most reliable way instead of trying to wrestle with Wine directly.  There's always a problem with every update to WoW, and this causes the army of users to flood the support forums resulting in timely fixes and resumed gameplay.  It sucks spending three or four hours trying to go it alone when all you want to do is play the game--even if you get lucky from time to time with a quick fix.

---

### Post by Desolator64 on 2009-08-31
I should have been more specific. The game is certainly playable for me right now. I did some quick leveling with my friend before going to bed. While the frame rate was annoying, I was still able to function. The server lag was more of a nuisance than my video lag to be honest. One really noticeable problem I did get was that all of the other players' models were almost completely white. I'm not sure if it was because of my low settings or because of some graphical problem I was having. I'll check that out now that I've got some time.

I've never tried Cedega out to be honest. I've got mixed feelings about it. I dislike the way the developers leeched off of Wine's charitable community and used its source code to develop their software, then made Cedega proprietary.

---

### Post by jasonditz on 2009-08-31
I used to subscribe to cedega back when it was called WineX, I might check it out again at some point. 

Right now I'm sort of in that stage where my MacMini (one of the first intel based ones) is usable but getting kind of old and slow, and the 1 GB of memory is starting to feel a little cramped. I'm trying to decide if my next system is going to be another Mac or if I should switch back to Linux outright. 

The original reason I went to the Mac in the first place was because it still had all the unix tools I use plus there were commercial games. Wine sure has gotten better though so that's maybe not an obstacle anymore. 

Seems like the lesson I'm taking out of this experiment with the laptop is to get a Linux system but one with an actual video card in it. Think Best Buy will let me bring a CD-R with 9.04 with me and try to boot it on their display models?

---

### Post by Desolator64 on 2009-08-31
Right now my main computer is a desktop PC that I'm running XP on. It's my gaming machine. My laptop is kind of a hobby/work machine. I don't have my PC with me where I live right now so running WoW on Ubuntu is my only option.  :P

I'm personally not a fan of Macs. I think the coolest thing Apple ever made was the iPod and they're milking that fanbase for all its worth. I don't know if Best Buy would let you do that but it's worth a shot. Just try not to ask a manager.

I've been messing around with my settings and the only thing that I found increases my framerate is enabling triple buffering in my resolution settings (but not by much!). Setting either pixel or vertex shaders to hardware either screws up my graphics tremendously or locks the game up when I try to start it so I have to pull the battery. I think I'm going to just leave them off for now...

---

### Post by bl33d on 2009-08-31
> **Desolator64 said:**
> Right now my main computer is a desktop PC that I'm running XP on. It's my gaming machine. My laptop is kind of a hobby/work machine. I don't have my PC with me where I live right now so running WoW on Ubuntu is my only option.  :P

I'm personally not a fan of Macs. I think the coolest thing Apple ever made was the iPod and they're milking that fanbase for all its worth. I don't know if Best Buy would let you do that but it's worth a shot. Just try not to ask a manager.

I've been messing around with my settings and the only thing that I found increases my framerate is enabling triple buffering in my resolution settings (but not by much!). Setting either pixel or vertex shaders to hardware either screws up my graphics tremendously or locks the game up when I try to start it so I have to pull the battery. I think I'm going to just leave them off for now...

are you running in opengl mode when you enable triple buggering?

---

### Post by jasonditz on 2009-08-31
> **Desolator64 said:**
> 
I'm personally not a fan of Macs. I think the coolest thing Apple ever made was the iPod and they're milking that fanbase for all its worth. I don't know if Best Buy would let you do that but it's worth a shot. Just try not to ask a manager.

You kind of have to take the good with the bad with Macs. The hardware just works, which is nice, and most of the OSS that I was using on my old SuSE 8.0 PC that it replaced was available. 

The downside (besides costing a ton) is that a lot of it will only work in X11, which is really inconvenient sometimes (having to load a separate X11 server just to run GIMP for instance). Plus when Apple decides to "officially" support a program like Java watch out: you're guaranteed to have obsolete virtually unupgradable revisions of the JDK if you don't buy a new version of OSX every year. 

Well that and there's a lot of jerkasses in the Mac community (in all fairness there's some really nice people too). I got a ton of hate mail after I wrote an article mocking Macworld for one of their writers' suggestions that Apple should somehow make it totally impossible for individual users to create executable files to "cut down on piracy and make the platform more viable."

---

### Post by Desolator64 on 2009-09-02
No, I was not in opengl mode. Apparently this type of video card is an exception and can be run with directx with wine. I don't really know the reason. :P

That's ridiculous that someone would suggest that! I hate the way the Apple is trying to market the Mac as being the free and easy to use alternative to Windows yet pulls that kind of stuff. They're just as big of capitalist extortionists as Microsoft but the only difference is they're not as good at it.

---

