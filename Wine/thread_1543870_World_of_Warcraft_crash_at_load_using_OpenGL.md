---
title: "World of Warcraft crash at load using OpenGL?"
date: 2010-08-01
forum: Wine
---

### Post by stephlar on 2010-08-01
Hello everyone!  I've been up and down these forums and beating my head on my desk because it seems I have tried nearly everything!

Current Hardware/Software:
HP Mini 210
Intel Atom Processor N455 (1.66GHz, 512KB L2)
1GB DDR3 RAM
Ubuntu 10.04 - Lucid Lynx
Intel GMA 3150 "Pineview" (graphics card)*
Wine 1.2

*I understand that Intel SUCKS for drivers on Linux, and you (as the reader) are probably going to guffaw and say "why are you trying to run WoW on a netbook with that kind of hardware?!" and I will only respond with: It's an experiment!


Here's my issue:

World of Warcraft runs under it's default "DirectX" mode, but is rather laggy and there are missing texture/polygons (even with settings all the way down).  Other users recommend switching to OpenGL mode to reduce lag and increase FPS.  However, if I add the line "SET gxApi "opengl"" to the config.wtf file, the game will automatically crash at start up with the following error:

> ==============================================================================
World of WarCraft (build 12340)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Aug  1, 2010  5:13:11.072 PM
User:     stephie
Computer: tstrubl1-laptop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:    C:\Program Files\World of Warcraft\Wow.exe
Exception:    0xC0000005 (ACCESS_VIOLATION) at 0073:376CB490

The instruction at "0x376CB490" referenced memory at "0x376CB490".
The memory could not be "read".


WoWBuild: 12340
Settings: 
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "3"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.20000000298023"
SET Sound_AmbienceVolume "0.20000000298023"
SET farclip "177"
SET gxWindow "1"
SET gxResolution "800x600"
SET gxApi "opengl"
SET mouseSpeed "1.3999999761581"
SET accounttype "LK"
SET VoiceActivationSensitivity "0.39999997615814"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET groundEffectDist "70"
SET environmentDetail "0.5"
SET gameTip "53"
SET realmName "Eldre'Thalas"
SET Sound_MasterVolume "0.20000000298023"
SET Sound_SFXVolume "0.20000000298023"
SET timingTestError "0"
SET uiScale "0.89999997615814"
SET useUiScale "1"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET Sound_EnableSFX "0"
SET particleDensity "0.10000000149012"
SET lastCharacterIndex "8"
SET ffxDeath "0"
SET ffxGlow "0"
SET portal "us"
SET textureFilteringMode "0"
SET baseMip "1"
SET weatherDensity "0"

----------------------------------------
               GxInfo
----------------------------------------
GxApi: OpenGL
Vendor: Tungsten Graphics, Inc
Renderer: Mesa DRI Intel(R) IGD GEM 20091221 2009Q4 x86/MMX/SSE2
Version: 1.4 Mesa 7.7.1

------------------------------------------------------------------------------

----------------------------------------

[and so on...]



I have already tried the follow things:
1. Configuring Wine to run under Windows XP, Windows 7, and Windows Vista... same thing happens.
2. Checking XORG updates...  (sorry I don't remember the exact Terminal command) but it gives me that all drivers are up to date.  However, opening up xorg.conf is a blank file?
3. Running the command "glxinfo | grep rendering" in Terminal DOES give "direct rendering: Yes".


So my main question is...
Why would WoW crash in OpenGL mode and not in DirectX mode?  Any suggestions on what else to try?

---

### Post by saisake on 2010-08-01
hi, i have the same issue, i can run wow on my netbook MSI Wind under windows xp doing 6-15 fps. just yesterday i decided to install ubuntu 10.04 lts on the netbook, and trying to run wow thru wine.

it runs at 2-3 fps with opengl disabled, and crashes at launch with opengl enabled.

I have other faster hardwares that runs wow smoothly under ubuntu. its my preference that it runs on my netbook for mobility purposes, so when i go out with my netbook i can still login on wow.

i have searched some solutions, and found some infos that can be factor as to why this happens, under intel graphics, the opengl version is 1.2-1.3ish, with my nvidia cards opengl version is around 2.1ish

if we could find a workaround to have our intel drivers upgrade to this 2.1+ version. it could work for us, using intel graphics to run wow. just my opinion TS.

ill subscribe to this thread, so we can work together to have a solution for our issue.

---

### Post by stephlar on 2010-08-06
Today I have done the following:

1. Updated to Wine 1.3 using the following .deb package found near the bottom of this thread:
[http://ubuntuforums.org/showthread.php?t=1546123&page=2](http://ubuntuforums.org/showthread.php?t=1546123&page=2)

2. Tried running Wine 1.3 through a virtual desktop.

3. Looked at this page about Ubuntu video card driver repository, and did some tweaks to the code to do this for Lucid Lynx (10.04):
[http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html](http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html)


And results?  Still no luck.

---

### Post by stephlar on 2010-08-06
I decided to try a WineDebug command, see if it could give me more specifics.

I used this page:
[http://wiki.winehq.org/3DDriverIssues?highlight=%28driver%29](http://wiki.winehq.org/3DDriverIssues?highlight=%28driver%29)

With the following Terminal command:
> WINEDEBUG=+wgl wine "C:\\Program Files\\World of Warcraft\\Wow.exe" &> wine.log

You can find the wine.log file in:
~/.wine/dosdevices/z:/home/username/

Turns out I got this:
> trace:wgl:wglGetProcAddress func: 'wglGetIntegerv'
trace:wgl:X11DRV_WineGL_InitOpenglInfo GL version             : 1.4 Mesa 7.7.1.
trace:wgl:X11DRV_WineGL_InitOpenglInfo GL renderer            : Mesa DRI Intel(R) IGD GEM 20091221 2009Q4 x86/MMX/SSE2.
trace:wgl:X11DRV_WineGL_InitOpenglInfo GLX version            : 1.2.
trace:wgl:X11DRV_WineGL_InitOpenglInfo Server GLX version     : 1.2.
trace:wgl:X11DRV_WineGL_InitOpenglInfo Server GLX vendor:     : SGI.
trace:wgl:X11DRV_WineGL_InitOpenglInfo Client GLX version     : 1.4.
trace:wgl:X11DRV_WineGL_InitOpenglInfo Client GLX vendor:     : Mesa Project and SGI.
trace:wgl:X11DRV_WineGL_InitOpenglInfo Direct rendering enabled: True
trace:wgl:has_opengl GLX is up and running error_base = 166
trace:wgl:register_extension_string ''
trace:wgl:register_extension     - 'wglGetIntegerv'
trace:wgl:register_extension     - 'wglFinish'
trace:wgl:register_extension     - 'wglFlush'
trace:wgl:register_extension_string 'WGL_ARB_extensions_string'
trace:wgl:register_extension     - 'wglGetExtensionsStringARB'
trace:wgl:register_extension_string 'WGL_ARB_multisample'
trace:wgl:register_extension_string 'WGL_ARB_pixel_format'
trace:wgl:register_extension     - 'wglChoosePixelFormatARB'
trace:wgl:register_extension     - 'wglGetPixelFormatAttribfvARB'
trace:wgl:register_extension     - 'wglGetPixelFormatAttribivARB'
trace:wgl:register_extension_string 'WGL_EXT_extensions_string'
trace:wgl:register_extension     - 'wglGetExtensionsStringEXT'
trace:wgl:register_extension_string 'WGL_EXT_swap_control'
trace:wgl:register_extension     - 'wglSwapIntervalEXT'
trace:wgl:register_extension     - 'wglGetSwapIntervalEXT'
trace:wgl:register_extension_string 'WGL_WINE_pixel_format_passthrough'
trace:wgl:register_extension     - 'wglSetPixelFormatWINE'
trace:wgl:X11DRV_wglGetProcAddress ('wglGetIntegerv'):                  (0x68f6c1f0) - WineGL
trace:wgl:wglGetProcAddress func: 'wglFinish'
trace:wgl:X11DRV_wglGetProcAddress ('wglFinish'):                       (0x68f74ad0) - WineGL
trace:wgl:wglGetProcAddress func: 'wglFlush'
trace:wgl:X11DRV_wglGetProcAddress ('wglFlush'):                        (0x68f749d0) - WineGL
trace:wgl:process_attach found DisabledExtensions="GL_ARB_vertex_buffer_object"
fixme:win:EnumDisplayDevicesW ((null),0,0x195ee20,0x00000000), stub!
trace:wgl:wglGetProcAddress func: 'glAccum'

[and it goes on with more trace:wgl:wglGetProcAddress func: stuff...]

---

### Post by stephlar on 2010-08-06
As a final note... I took a screenshot of WoW running through Wine with DirectX, mostly to share.

This is on the lowest settings (and even then, 'shadowed terrain' doesn't load), in fullscreen mode, and in a starting zone (very low population).  I get about 4-6fps outside (8fps if I'm lucky) and about 12-15fps indoors.  It's definitely not an internet issue because I'm plugged into a T1 line.

Pretty funky!!



[IMG]http://i3.photobucket.com/albums/y62/ellusia/WoW.png[/IMG]

---

### Post by hikaricore on 2010-08-06
Even in DX mode it's using OpenGL via conversion, which causes really weird effects on hardware with next to no OpenGL support. ;)

---

### Post by _h_ on 2010-08-06
> **stephlar said:**
> As a final note... I took a screenshot of WoW running through Wine with DirectX, mostly to share.

This is on the lowest settings (and even then, 'shadowed terrain' doesn't load), in fullscreen mode, and in a starting zone (very low population).  I get about 4-6fps outside (8fps if I'm lucky) and about 12-15fps indoors.  It's definitely not an internet issue because I'm plugged into a T1 line.

Pretty funky!!



[IMG]http://i3.photobucket.com/albums/y62/ellusia/WoW.png[/IMG]


I think adding the OffscreenRenderingMode to backbuffer on the Direct3D registry tweak fixes this.

---

### Post by asdfoo on 2010-08-06
If you're game you can look at using ubuntu edgers which provides closer to development versions of parts involving video support.

---

### Post by frank1e on 2010-08-07
So my main question is...
Why would WoW crash in OpenGL mode and not in DirectX mode?  Any suggestions on what else to try?[/QUOTE]


I want to say I am having the same exact problem. I'm sick of booting into windows for wow. It';s the only reaosn I use win now.  I tried ruunning wow in open gl mode and it crashes on boot.  If I just run it regular it runs but only like 6 fps.  But I am not on a netbook I have a pentium 4 2.8 ghz dell dimension. Nvidia 6200 agp gfx card.  Guys lets find a solution to this! =) Im new to linux but any help appreciated.

---

### Post by thenellt on 2010-08-07
Yes, you should set offscreenrendering to fbo in regedit (look in winehq for a howto if you need it) and have you tried getting drivers from here [[COLOR="Blue"]http://intellinuxgraphics.org/download.html[/COLOR]]("http://intellinuxgraphics.org/download.html") ?

---

### Post by cwwilson721 on 2010-08-07
> > **frank1e said:**
> So my main question is...
Why would WoW crash in OpenGL mode and not in DirectX mode?  Any suggestions on what else to try?


I want to say I am having the same exact problem. I'm sick of booting into windows for wow. It';s the only reaosn I use win now.  I tried ruunning wow in open gl mode and it crashes on boot.  If I just run it regular it runs but only like 6 fps.  But I am not on a netbook I have a pentium 4 2.8 ghz dell dimension. Nvidia 6200 agp gfx card.  Guys lets find a solution to this! =) Im new to linux but any help appreciated.I don't know why you have a problem. On my kids' machine, WoW is running fine w/NV6200AGP, and a Athlon 2000+.

Did you try deleting/renaming the WTF folder, then appending '-opengl' at the end of the command to launch WoW?```
env WINEPREFIX="/home/<USER>/.wine" wine /home/<USER>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/Launcher.exe -opengl
``` And turn off Compiz? Framerates are about 20-30 in most places, but forget 25mans and Dalaran. WAY too much for this hardware

---

### Post by stephlar on 2010-08-08
> **thenellt said:**
> Yes, you should set offscreenrendering to fbo in regedit (look in winehq for a howto if you need it) and have you tried getting drivers from here [[COLOR=Blue]http://intellinuxgraphics.org/download.html[/COLOR]]("http://intellinuxgraphics.org/download.html") ?


Made the regedit change, and it's still looking like crap.

So although I could have sworn I installed drivers, the xorg.conf file STILL appears empty.

So, I went through it all again, spending nearly 3 hours trying to figure out how to compile these things.

Doing a "./configure" command while in the "xf86-video-intel-2.12.0" directory gives me a "No package 'libdrm' found" error.

I then went and found a libdrm package here:
[http://www.linuxfromscratch.org/blfs/view/cvs/general/libdrm.html](http://www.linuxfromscratch.org/blfs/view/cvs/general/libdrm.html)

And compiled that.  But I got a "libdrm already found" sort of error (that was 2 hours ago), listing a libdrm of version 2.4.0.

After some sort of finagling, I managed to get past that error...  However, trying to ./configure the xorg file still gives me a "no libdrm" error.

So I am foiled again!

---

### Post by stephlar on 2010-08-08
Ok ok, much clearer question...

I have located the old libdrm.so.2.4.0 in the /lib folder.  How would I go about removing these, or upgrading these to the newest version (somewhere in the 2.4.14 range)?  And why doesn't the xorg compile find these libraries?

---

### Post by Espionage724 on 2010-08-08
I had a similar situation with my 950GMA. I tried the stock drivers that come with Ubuntu, and the edgers drivers. Both failed to run WoW in OpenGL mode (I was able to run other games in GL mode such as Warcraft III however with little trouble)

Someone told me that it was because the Intel graphics drivers don't provide some instruction that WoW was looking for.

Idk if the edgers drivers are different then the intellinuxgraphics link drivers, but I thought they were similar/the same? Anyway, it shouldn't stop you from trying them (idk how to complile the drivers from there, so that stopped me)

Good luck!

---

### Post by zelrikriando on 2010-08-09
I am having very similar issues, here is where I am at now:

[http://i34.tinypic.com/295rgcm.jpg](http://i34.tinypic.com/295rgcm.jpg)

I cant use opengl, but I have reasonable fps without it. My main issue is the black textures on the ground. I am on ubuntu 10.04, wine 1.3.0 and an i3 330M integrated intel laptop with 4Gb or RAM.

I tried a few of the things discussed above but I kept the default intel drivers as I dont know how to upgrade them.

---

### Post by stephlar on 2010-08-09
Today's progress:
(with clear step-by-step instructions for beginners)


1. I found this extremely helpful page for beginners (which includes myself, to an extent):
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)[INDENT]1A: In Terminal, I made myself a root user by typing "sudo su" before doing all this.  Not sure if it's necessary, but I figured it couldn't hurt.
1B: I went through Step 1 on the above page.  Also, I had previously done a "sudo apt-get install git-core" and created a folder named "Git" in /home/username/ to save stuff in.
1C: I found the git repository here: [http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/](http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/).  At the bottom of the page is a git address.  I used this forum page to help out with this:
[http://ubuntuforums.org/showthread.php?t=1533694](http://ubuntuforums.org/showthread.php?t=1533694)
1D: I extracted the xf86... folder within Git, because it wouldn't let me extract to /usr/local/src as recommended by the above page.  I found out I had to do this through Terminal with a "move" command:
```
sudo mv foldername "/usr/local/src/"
```1E:  From there, I just continued with their instructions for Step 1.
[/INDENT]2. Using the Terminal, I navigated to the /usr/local/src/xf86... folder.  If you're not familiar with this, you can press Tab to auto fill once you have a few characters down, so you don't have to type it all out.
```
cd /usr/local/src/xf86-video-intel
```[INDENT]2A: Once in the directory, I tried the command "./configure" and got the usual libdrm missing error (as mentioned in a previous post).
2B: I searched for the newest libdrm file found here:
[http://dri.freedesktop.org/libdrm/](http://dri.freedesktop.org/libdrm/)
2C: Repeated most of Part 1 above (Extracted, moved to /usr/local/src/).  Ran ./configure of libdrm.  Then "sudo make install".  So that's done.  :)
2D: Repeated ./configure in xf86 directory...  Ended up with two more errors:
Missing xf86driproto and glproto.
Found these here:
[http://www.t2-project.org/packages/xf86driproto.html](http://www.t2-project.org/packages/xf86driproto.html)
And here:
[http://www.t2-project.org/packages/glproto.html](http://www.t2-project.org/packages/glproto.html)
Extracted, moved, ran ./configure, and "make" and "sudo make install" for each.
2E: Repeated ./configure for xf86 again...  Another error!
Missing glxint.
Found this using this thread:
[http://ubuntuforums.org/archive/index.php/t-203312.html](http://ubuntuforums.org/archive/index.php/t-203312.html)
And can be fixed by running:
```
sudo apt-get install --reinstall mesa-common-dev
```[/INDENT]3. Repeated ./configure in xf86 directory...  This time it was a go![INDENT]3A: In Terminal, ran "make" then "sudo checkinstall" (to create a .deb file)
3B: Double clicked on the .deb file (it creates the file in the same directory as the xf86-video-intel folder)

[/INDENT]So everything looked great, everything was working (supposedly)...

Then I checked the xorg.conf file and it was STILL blank!!

I checked out the "Synaptic Package Manager" and tried to see if I was missing any other important xorg packages.  I checked any I thought were relevant/important.  I have updated as well.

I then, recompiled the xf86 directory (./configure, make, sudo checkinstall OR sudo make install).  And still this xorg.conf file remains empty.

*sigh*

I am going to try from scratch again.

---

### Post by cwwilson721 on 2010-08-09
Erm...Newest Xorg doesn't NEED xorg.conf anymore.

---

### Post by stephlar on 2010-08-10
> **cwwilson721 said:**
> Erm...Newest Xorg doesn't NEED xorg.conf anymore.

See, this would be great, if WoW ran in OpenGL mode for me.  :)

I'm still trying to figure out what's not being recognized (hardware, software) or what it's depending on that I don't have/is broken.

---

### Post by stephlar on 2010-08-10
> **Espionage724 said:**
> Someone told me that it was because the Intel graphics drivers don't provide some instruction that WoW was looking for.

Hmmm...  I'll look into this.

---

### Post by zelrikriando on 2010-08-10
> **stephlar said:**
> See, this would be great, if WoW ran in OpenGL mode for me.  :)

I'm still trying to figure out what's not being recognized (hardware, software) or what it's depending on that I don't have/is broken.

I am not sure what xorg.conf has anything to do with it, it's an obsolete feature. I think the main issues are the crappy intel drivers, the settings in wine and the Config.WTF file. 

I am a bit scared to change the mesa packages personally as I used them to compile some other programs. I'll try to poke around with the drivers anyway.

---

### Post by Espionage724 on 2010-08-11
This may or may not help, but have you tried adding SET fixedfunction "0" to your config.wtf? This should increase performance on D3D mode, and this might help make it start on OpenGL mode.

If I remember correctly, I think I did make WoW start in OpenGL mode somehow probably using that fixed function thing, but as I remember I think there were mad graphic glitches.

Another thing to maybe try out is SET gxApi "D3D9ex"  it uses a newer D3D9 render.

---

### Post by stephlar on 2010-08-16
> **Espionage724 said:**
> This may or may not help, but have you tried adding SET fixedfunction "0" to your config.wtf? This should increase performance on D3D mode, and this might help make it start on OpenGL mode.

If I remember correctly, I think I did make WoW start in OpenGL mode somehow probably using that fixed function thing, but as I remember I think there were mad graphic glitches.

Another thing to maybe try out is SET gxApi "D3D9ex"  it uses a newer D3D9 render.

Thanks, I'll try both.

---

### Post by stephlar on 2010-08-26
> **Espionage724 said:**
> This may or may not help, but have you tried adding SET fixedfunction "0" to your config.wtf? This should increase performance on D3D mode, and this might help make it start on OpenGL mode.

If I remember correctly, I think I did make WoW start in OpenGL mode somehow probably using that fixed function thing, but as I remember I think there were mad graphic glitches.

Another thing to maybe try out is SET gxApi "D3D9ex"  it uses a newer D3D9 render.


Unfortunately, neither worked!  And using the D3D9ex mode actually froze the game at the login screen.  :P

---

### Post by mspuke on 2010-08-30
I had the same weird black block problem that you displayed in the screenie you posted and I successfully fixed it by opening up winecfg and allowing pixel shader, and turning the Vertex shader support to "hardware". 

Although, now that I look back it appears that the Vertex shader support is on none, the pixel shader is checked. If either of these are different for you, it could be the solution. 

On a side note; I'm not sure what graphics card you are running but if it's intel you're better off not using opengl mode when running the game.

---

### Post by akoskm on 2010-08-30
Hi!
stephlar, have you checked your xorg.conf?
I assume that you have installed your video driver correctly.
In this case, regarding to your 3rd [*post*]("http://ubuntuforums.org/showpost.php?p=9686839&postcount=4") in wine.log you can see that wine is loading the default mesa drivers instead of your video driver.
Could you post your */etc/X11/xorg.conf* and */var/log/Xorg.0.log*?

---

### Post by ToxicBurn on 2010-08-30
> **stephlar said:**
> As a final note... I took a screenshot of WoW running through Wine with DirectX, mostly to share.

This is on the lowest settings (and even then, 'shadowed terrain' doesn't load), in fullscreen mode, and in a starting zone (very low population).  I get about 4-6fps outside (8fps if I'm lucky) and about 12-15fps indoors.  It's definitely not an internet issue because I'm plugged into a T1 line.

Pretty funky!!



[IMG]http://i3.photobucket.com/albums/y62/ellusia/WoW.png[/IMG]


I hate to say it but the #1 problem is that your Graphics card / Onboard video is really not strong enough to run wow in windows let alone linux.

im sorry 

even if you fixed it would you want to play at 2-8FPS ?

---

### Post by zelrikriando on 2010-09-06
> **ToxicBurn said:**
> I hate to say it but the #1 problem is that your Graphics card / Onboard video is really not strong enough to run wow in windows let alone linux.

im sorry 

even if you fixed it would you want to play at 2-8FPS ?

I would like to say that I am having the same issues right now on my laptop and that I get much more than 8fps. The onboard video card should be able to handle WoW as it is able to on Windows. This is not really a hardware issue but a software issue.

Anyway, my personal fix was to build a desktop computer with a nvidia in it and then Wow runs perfectly on it (once I get the game started anyway, I still have random crashes when I log in, I blame wine for that). 

I have no luck yet on fixing this bug on my laptop.

---

### Post by hikaricore on 2010-09-07
[B]I'm so god damn tired of repeating this...

Integrated intel chipsets usually do not have adequate OpenGL support to run WoW via wine on Linux.
It does not matter if you're running the game in OpenGL or DX mode, you are still using OpenGL (via conversion).
This is not a bug with wine or Linux, but either a HARDWARE issue or an problem with the Intel drivers themselves.
Please stop lying to yourself and everyone else and saying it's not hardware related because you're wrong and you are going to confuse the noobs...

The "video hardware" is designed for very basic usage under Windows with Direct3D in mind and that's about all.[/B]

---

### Post by Jazzy_Jeff on 2010-09-08
I use an nvidia card on my desktop and World of Warcraft flies on my system. I actually get better fps then I did in Windows. On average I get around 60 fps. It slows to around 35 fps inside the big towns where everyone is hanging out. If you want to play any 3D games on a laptop with Linux then please make sure it has an nvidia card. They are better supported under Linux than all the others I have found.

---

### Post by cwwilson721 on 2010-09-08
> **Jazzy_Jeff said:**
> I use an nvidia card on my desktop and World of Warcraft flies on my system. I actually get better fps then I did in Windows. On average I get around 60 fps. It slows to around 35 fps inside the big towns where everyone is hanging out. If you want to play any 3D games on a laptop with Linux then please make sure it has an nvidia card. They are better supported under Linux than all the others I have found.That's a bit too much.

You should say:
[COLOR=Navy][SIZE=4]If you use integrated graphics for wine/WoW, make sure it's Nvidia or ATi, not Intel.[/SIZE][/COLOR]
[COLOR=Black][SIZE=2]
ATi makes a fine product, too, that actually WORKS with opengl. So does Nvidia.
INTEL DOES NOT
[/SIZE][/COLOR]

---

### Post by Jazzy_Jeff on 2010-09-08
> **cwwilson721 said:**
> That's a bit too much.

You should say:
[COLOR=Navy][SIZE=4]If you use integrated graphics for wine/WoW, make sure it's Nvidia or ATi, not Intel.[/SIZE][/COLOR]
[COLOR=Black][SIZE=2]
ATi makes a fine product, too, that actually WORKS with opengl. So does Nvidia.
INTEL DOES NOT
[/SIZE][/COLOR]

I have found that nvidia cards are better supported then the other cards. I have used ATI graphics in the past as well and have just found that nvidia seems to work better for gaming.

---

### Post by stephlar on 2010-09-15
> **hikaricore said:**
> [B]I'm so god damn tired of repeating this...
[/B]Pessimistic much?

> [B]
Integrated intel chipsets usually do not have adequate OpenGL support to run WoW via wine on Linux.
[/B]Yes, I know that.  That's why I'm here to try and fix it!> [B]
It does not matter if you're running the game in OpenGL or DX mode, you are still using OpenGL (via conversion).
[/B]This comes straight off the Wine website, so DUH.  Systematically, it would make more sense to run a game through OpenGL, if possible.  WoW has that option.  Read the title of this thread.> [B]
This is not a bug with wine or Linux, but either a HARDWARE issue or an problem with the Intel drivers themselves.
[/B]In my experience, we write software code to program the hardware... after all, the hardware is just transistors and capacitors.  :)  Wine and Linux are software, and there's of course NOTHING WRONG WITH THEM (ahem, sarcasm).  Yes, Intel cards suck because Intel doesn't provide its own 'software' (aka drivers) for their hardware to run smoothly through another software (Linux).  That's where programmers come in...  We should be intelligent enough to write a software (driver) that WILL properly communicate between Intel hardware and a Linux OS.I'm pretty sure that's what the Open Source community is all about.
> [B]
Please stop lying to yourself and everyone else and saying it's not hardware related because you're wrong and you are going to confuse the noobs...
[/B]It's not a hardware or a software issue.  It's a MISCOMMUNICATION between software AND hardware -- that's the point of a driver/firmware.  Get it right.  :)> [B]
The "video hardware" is designed for very basic usage under Windows with Direct3D in mind and that's about all.[/B]Which "video hardware" are you referring to?  Intel?  Or all of them?  Because technically, Intel and Nvidia have both made chips for Mac OS computers.  And the Mac OS is written in a form of Unix.  And Unix, as we all know, is the basis for Linux.  Your point is null.

Hikaricore - I am sick and tired of your ignorance, pessimism, and overall unhelpfulness to this community.

---

### Post by cwwilson721 on 2010-09-15
It is a combo issue, but at the heart is the HARDWARE does not support the HARDWARE acceleration of opengl.

You can software render until you are blue in the face, and it won't help. 

Let's give a fairly easy to follow analogy using automobiles:

Let's have 3 cars. All three have the same body style, weight, size, etc.

[LIST]
[*]Car 'A' is a 2 door SUV with a 400HP V8 (We'll call this vehicle '9800GTX2')
[*]Car 'B' is a 2 door SUV with a 200HP V8 (We'll call this one '6200int')
[*]Car 'C' is a 2 door SUV with a 25 HP 1 cylinder engine (This is our 'GMA')
[/LIST]
Car 'A' happily runs, climbs anything, and kills the environment (Tons of excess heat given off). But it does all that's asked of it because it has the power to do so.

Car 'B' runs OK, gets the kids to school, but it can't haul the boat you bought, but it has better mileage (less heat).  

Car 'C' runs okay, also, but only two people at a time, and it dies when it tries to go up a hill. But, what great mileage!!

Okay so far? Good. Now, for the fixes..

Car 'A' don't need no stinkin' fixes. An occasional tune-up, and all is well. And change the oil.

Car 'B' can be 'fixed' by adding a supercharger. And away it goes...

Car 'C' CAN'T BE FIXED. Add a supercharger, add better plugs, add 3000+ octane gas..IT WON'T WORK. The 'engine' is TOO SMALL.

So the Intel chips lack the 'horsepower' (the hardware component to accelerate opengl). Changing the code driving it won't increase squat. opengl is opengl, unless Intel wants a separate 'opengl' standard just for itself (which negates the 'standard' anyway)

For now, I'd give up on Intel until it gets its act together, and actually implements the hardware portion of opengl. Until that happens, it's still a 1 cylinder putt-putt, at least, as far as opengl goes.

---

### Post by saisake on 2011-05-09
> **saisake said:**
> hi, i have the same issue, i can run wow on my netbook MSI Wind under windows xp doing 6-15 fps. just yesterday i decided to install ubuntu 10.04 lts on the netbook, and trying to run wow thru wine.

it runs at 2-3 fps with opengl disabled, and crashes at launch with opengl enabled.

I have other faster hardwares that runs wow smoothly under ubuntu. its my preference that it runs on my netbook for mobility purposes, so when i go out with my netbook i can still login on wow.

i have searched some solutions, and found some infos that can be factor as to why this happens, under intel graphics, the opengl version is 1.2-1.3ish, with my nvidia cards opengl version is around 2.1ish

if we could find a workaround to have our intel drivers upgrade to this 2.1+ version. it could work for us, using intel graphics to run wow. just my opinion TS.

ill subscribe to this thread, so we can work together to have a solution for our issue.

The recent release of ubuntu 11.04 / kubuntu 11.04 have updated opengl drivers to 2.1 ish, and guess what?

Wow can now run on opengl with no problems on intel gma graphics.
attached is a screenie of kubuntu 11.04 64bit, running wow with ofcourse low framerate, anyway, what do expect for gaming on intel graphics. but still, it works now.....

regards to TS.

PS: When you disable Desktop Effects, wow runs at 30 fps.... with all option on low...

---

### Post by saisake on 2011-05-12
BUMP:

Manage to make WOW work on kubuntu 11.04 with opengl.

framerates is good ranging from 15-20fps...on fullscreen, all options low

now i encountered an issue, that when i get close with 2 other players or more. or a player gets in range with me, wine crashes....and wow included

tried using wine 1.2 and 1.3 same problem...


but when questing alone in the world, no glitches, no crashes etc...

PS: no error logs generated on wow, when it crashes, only on wine...
we are this close to make it work on wine over intel graphics...

---

### Post by samuaz on 2011-07-05
I have the same problem in OpenGL mode, if I'm doing every single quest
is perfect (20-30 fps with the graphic quality to a minimum), but when I
one city or another player I have about wine crashes: S

any solution found so far?,

macbook 4.1 intel core 2 duo 2.16 GHz, 4GB ram, intel gma x3100

---

### Post by samuaz on 2011-07-08
[SIZE="4"]I HAVE fix it!

i write a new thread about it[/SIZE]

intel core 2 duo 2,16 ghz, gpu intel gma x3100 4gb ram... runing world of warcraft cataclysm 4,2 in wine, NO MORE CRASH, fps playable!!

---

### Post by akoskm on 2011-10-27
> **samuaz said:**
> [SIZE="4"]I HAVE fix it!

i write a new thread about it[/SIZE]

intel core 2 duo 2,16 ghz, gpu intel gma x3100 4gb ram... runing world of warcraft cataclysm 4,2 in wine, NO MORE CRASH, fps playable!!

Could you gave us a link for that thread?
Thanks!

---

### Post by akoskm on 2011-10-27
> **saisake said:**
> The recent release of ubuntu 11.04 / kubuntu 11.04 have updated opengl drivers to 2.1 ish, and guess what?

Wow can now run on opengl with no problems on intel gma graphics.
attached is a screenie of kubuntu 11.04 64bit, running wow with ofcourse low framerate, anyway, what do expect for gaming on intel graphics. but still, it works now.....

regards to TS.

PS: When you disable Desktop Effects, wow runs at 30 fps.... with all option on low...

Could you explain how you managed to dismiss the corrupted shadows from the ground?
Thank you!

---

