---
title: "WoW, Wine, ATI mobility and opengl = argh!"
date: 2006-04-07
forum: Wine
---

### Post by Andrew-buntu on 2006-04-07
Hello!  I've been trying to get World of Warcraft working on my laptop for about a month now.  I'm currently running wine 0.9.11 with the patch from [winehq]("http://appdb.winehq.org/appview.php?versionId=4031").  I've got WoW patched to the latest version, too. I can usually get WoW running in d3d mode at a lousy framerate.  It's not great but it's pretty reliable and I can change my graphical settings without crashing.  But whenever I try to run in opengl mode, it's a crap shoot.  Sometimes it works fantastic for about twenty minutes.  But most of the time when I use opengl, the game freezes immediately after the world loads and all the characters are drawn after I log in. :???:  When the freeze happens, there's no crash so I never get any debug messages or anything else that could help me out.
My big question is: **Anyone else running WoW under wine on an ATI mobility Radeon X300**?  I have a Dell Inspiron 9300.  I've got fglrxgears running with direct hardware rendering.  I've tried ATI's driver versions 8.23.7 (current), 8.22.5 and 8.21.7.  I use ATI's drivers to build the breezy package and install from there.  I've tried every version of wine since 0.9.6 and I've always had the same problem. ](*,) 
I'm about to give up and just say, oh well, ATI's drivers won't cut it with this particular setup.  I've run Gentoo/fluxbox on the same laptop and had similar results so I don't think I can blame it on Ubuntu or Gnome.  But before I give up, I've got to know if anyone else is running this card.
Thanks for reading!

---

### Post by Toxicity999 on 2006-04-11
try adding:
tmpfs           /dev/shm        tmpfs           defaults        0 0

To your fstab... I was having a problem like that too but the ATI site recommends this and for me its working =D

sudo gedit /etc/fstab to open it.

Then restart and enter:
mount | grep "shm"

It should return something saying it's mounted... try again and all should be well!

---

### Post by Andrew-buntu on 2006-04-12
[QUOTE=Toxicity999]try adding:
tmpfs           /dev/shm        tmpfs           defaults        0 0

To your fstab... I was having a problem like that too but the ATI site recommends this and for me its working =D

sudo gedit /etc/fstab to open it.

Then restart and enter:
mount | grep "shm"

It should return something saying it's mounted... try again and all should be well![/QUOTE]

Seems to be working so far.  I don't believe I missed that in the release notes.  WoW looks good with the 8.23.7 drivers in OpenGL.  I'm running WoW with all the settings at the lowest level but the framerate is nice and smooth.

Thanks for your help, Toxicity!

---

### Post by Andrew-buntu on 2006-04-13
Oops, looks as if it was just another one of those instances where it worked great for a while.  I booted up today and everything froze again right after logging in with OpenGL mode.
Ah well, I'm buying a new laptop with an nVidia card anyway.

---

### Post by rylz on 2006-04-21
I'm having the same problem on both Ubuntu and Gentoo, which has shm mounted by default, so I don't think that's the cause.  Does anybody else have an idea as to what could be causing this?  I have messed with virtually every xorg.conf and Config.wtf option that commonly cause problems and have yet to solve this problem... :confused: 

I really have little faith in ATI after my week long (and counting) debacle trying to get WoW to work...

-rylz

---

### Post by Dr_Dooom33 on 2006-04-24
Use Cedega it should work I have same setup

---

### Post by Delvien on 2006-04-25
I have inspiron 6000 with x300 128 , and 1gig of system memory, I have found that if i play WoW under linux it sucks... I have to boot to windows...


The way you get around the freeze on bootup is one 1) look for a utility called RovClock, its a overclocker for the x300 under linux, simple command to run. 2) dont move or do anything on login, if you do it freezes, i was able to run around in Orgrimmar just fine, not alot of lag, but more then windows gets, ( in windows WoW is flawless, hardly a laggy spot anywhere ) and i hate windows.. so thats saying alot..

---

### Post by myname on 2006-10-11
I had the same problem you did, no matter what I tried or installed.  WoW loads, I select my character, enter a world and BAMMMM locks up tighter than a young lady on prom night.

After about a month of trying everything under the sun, I was about to give up, and install TinyXP or some other flavor of small windows, maybe parellels then windows.  Though I didn't want to have to deal with the evil "Billyware(tm)" again.  

Today, while at work while my boss was away, I started my quest again, this time for very low XP, as I've been working on it for a month.  But, at lunchtime, I think I finished the quest, and got WoW working with my ATI Radeon x1600 512 megs and AMD64 CPU.  I am using the latest ATI drivers as of 10/10/2006.

So, what I am saying, in this longer than needed email, I can finally play WoW under Ubuntu 6.06!!!  I found the help I needed.




And unlike most people who say they found the answer to their own question, I am going to post mine, even though I don't understand it, I know I was able to play WoW 150 times longer than I could before.

Open up Xorg.conf and change the following to this:


[INDENT]Section "Device"
   Identifier  "aticonfig-Device[0]"
   Driver      "fglrx"
   Option       "Capabilities" "0x00000800"
   Option       "UseFastTLS" "off"
   Option       "KernelModuleParm" "locked-userpages=0"
EndSection[/INDENT]

Actually, I just added the 3 option lines to mine, restarted X and viola, it worked.

AGain, I have no clue why it works, just know it does.  And I'm also wondering why my Driver line has "fglrx" when I installed the drivers from ATI's site.

BTW, I found the answer to this on Transgaming's forums, even though I'm running Wine and not Cedega, it worked.

---

### Post by Wolfgang Richter on 2006-12-03
Wow, your fix worked wonders for me.  Every time I ran WoW it would freeze after about 10 seconds of being in the game.  I am going to try and investigate this stuff more in-depth to try to find better fixes, but for now this is amazing.

For a FPS speed up, which I will post here as well:

[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)
> Corrupt or Missing Text in 0.9.25 and 0.9.26 - here's the fix for ATI cards 

Open a terminal window, (konsole/terminal/x terminal etc..) and type regedit. This will start the wine server
and the wine equivalent of the windows registry editor will be displayed. If your familiar with using the registry
editor under windows then this is pretty much the same.

Find HKEY_CURRENT_USER\Software\Wine\

Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder

Click right on the wine folder and select [NEW] then [KEY]

Replace the text "New Key #1" with OpenGL

Click right in the right hand pane and select [NEW] then [String Value]

Replace "New Value #1" with "DisabledExtensions"
(Notice it's case sensitive)

Then double click anywhere on the line, a dialog box will open.
In the value field type "GL_ARB_vertex_buffer_object" (without the quotes).

My final task is to get the minimap working perfectly.  My minimap goes white whenever I go into a building.  Oh well, can't have everything I guess.  I have heard this might require a patch to Wine though.  

I am running Wine 0.9.26 - a binary, I didn't build.

---

### Post by Jaxilian on 2007-04-27
It crashes for me too. I have a laptop with ATi x600
Sometimes I can play for a long time, but sometimes it just crashes on every attempt.

here is my xorg.conf

```


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "se"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc M24 1P [Radeon Mobility X600]"
	Driver      "fglrx"
	Option	    "UseFastTLS" "off"
	Option 	    "Capabilities" "0x00000800"
	Option 	    "KernelModuleParm" "locked-userpages=0"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc M24 1P [Radeon Mobility X600]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

and here is my Config.wtf

```

SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x1024"
SET gxRefresh "60"
SET hwDetect "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "32"
SET farclip "477"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET realmList "eu.logon.worldofwarcraft.com"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET locale "enGB"
SET mouseSpeed "1"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "1"
SET realmName "Draenor"
SET mouseInvertPitch "1"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET gameTip "66"
SET AmbienceVolume "0.60000002384186"
SET ShowTargetCastbar "1"
SET expansionMovie "0"
SET minimapZoom "0"
SET Gamma "1.000000"
SET minimapInsideZoom "0"
SET uiScale "1"
SET gxApi "OpenGL"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "160"
SET timingTestError "3"

```

any tips on why it crashes?

---

### Post by Jaxilian on 2007-04-27
Just now it hanged. I played for 2 hours and suddenly freeze

---

### Post by Jaxilian on 2007-04-28
and now I cant get back in again. Game freezes when world is creating. No settings touched or anything....just don't run anymore.

weird!!

---

### Post by Jaxilian on 2007-04-28
GAAAAAAAAAAAAAAAAAAH!!!!!!!! I tested 50 times now and all fail. I am gonna switch back to Windows.

---

### Post by Jaxilian on 2007-04-28
This is what I get from the terminal when I get to WoW login:
```

~$ wine "C:\Program Files\World of Warcraft\WoW.exe"
err:secur32:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:reg:GetNativeSystemInfo (0x37400b20) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x71c6a4b8) stub!

```

---

### Post by Ferrat on 2007-04-28
Prolly your MPQ file is corrupted, you need to reinstall WoW

---

### Post by Jaxilian on 2007-05-02
Find it hard to believe that since I used the same installation now when I run Windows. It's the same files and now I get around 50-60fps and no errors whatsoever.

---

### Post by cyqotiq on 2007-05-26
I'm having this exact problem, but my hardware is slightly different.  Just to cover the basics and let everyone know what I've done up to this point, here is the current status of my machine:

After installing Ubuntu (Feisty) I tried to get WoW up and going as per the Gentoo ([http://gentoo-wiki.com](http://gentoo-wiki.com)) and Ubuntu ([http://help.ubuntu.com](http://help.ubuntu.com)) How-To pages.  This resulted in a functional WoW that allowed me to accept all of the TOS pages from the patches.  When I logged in, my computer froze up, as mentioned previously in this thread.  After applying a few patches here and there (wine's RegEdit patch, WTF/Config.wtf, and winecfg to test both OSS and ALSA - both to no avail) I began noticing that the audio wasn't frozen.  It was obvious that there was still data making it through... very slowly.  This would happen for about 10 seconds or so before it would just stop.

I have, so far, configured wine to:
   Emulate Windows XP (Applications)
   Use the OSS Driver (Audio) - I've also tried this with the ALSA driver, but the system just freezes much quicker.
   Allow DirectX to stop mouse from leaving window [pointless since I'm not using DX] (Video)
   Allow the Window Manager to control the windows (Video)
   Allow pixel shader (Video)
   Use Hardware accelleration (Video)

The reason I've listed each of the above lines is because I've toyed with each of them and continued to get the same results.  As of right now, each of the above settings for winecfg is set as shown above, which is the default winecfg setting on my installation.

My WTF/Config.wtf currently has the following lines added to it:
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"

Both of the ffx* lines were added later and had no obvious affect on the game.  Adding the SoundBufferSize line and setting it to anything at all will cause the system to lock up much sooner than it would if this line were missing.  SoundOutputSystem doesn't seem to have any affect on the game either.


I added the three Option lines from above to my Xorg.config file, but that also made no difference.
	Option "Capabilities" "0x00000800"
	Option "UseFastTLS" "off"
	Option "KernelModuleParm" "locked-userpages=0"


This problem is about to drive me nuts.  Today, alone, I've had to perform a hard reset on my box 9 times because of this problem.  I have never had to abuse Linux like this before.  I feel so dirty.  I scrub and I scrub, but dammit, they don't make water hot enough!

Anyway, if anyone has a possible solution, please let me know.  I also tried using Crossover, but it does the same thing.


Edit:
I meant to do this originally but it slipped my mind after my rant.
I've got the following setup on my machine:

ATi Radeon X300 (Installed ATi's proprietary driver from their website after the proprietary driver from Synaptic didn't fix this problem)

The full specs for this machine an be found at [Gateway's Support site]("http://support.gateway.com/s/PC/R/4190/4190sp3.shtml").  The only change is that I have 1GB of RAM instead of 512MB.

---

### Post by ShadowFlar3 on 2007-05-27
Well I've had this very same problem with my ATI (surprise!) card. I have radeon 9600 pro but I think it's the same bug/error anyway.

Still haven't found any solutions but here's what I've found out so far:

1) It doesn't crash on d3d. If you're desperate to play, get Cedega and run wow under d3d. You can do this on wine, too, but you can't get rid of the "double cursor" bug. Frame rates (for me) were much lower on d3d and about equal on wine and cedega, the only difference being Cedega fixes the double cursor bug. I think you could fix it on wine by toying with the registry keys as well but no one has reported anything so far.

The only thing that keeps me from playing on d3d is that every time I take a new target the game hangs for 0.5-1 sec while loading the player icon. D'oh!

You can switch to d3d by changing SET gxAPI "OpenGL" to "d3d" in your wow config.wtf. If you have no crashes on d3d at least its safe to assume the problem is not sound, corrupted install files, addons, rather opengl.

(By the way, the game crashes on Cedega in opengl mode the same way it does on wine, in case you wondered)

2) After the crash if you examine your WoW/Errors/ directory you can probably find error report matching the date and time the crash occurred. If so, you probably see it's the infamous error 132 that mainly bugs windows users, you can read about it all over the blizz forums. Blizzard's "solution" include everything from deleting cache, addon and account settings data, running repair.exe, getting latest drivers but I think, since it doesn't crash in d3d mode, that it's not about the files at least.

3) I've tried both the newest and ubuntu-way (older) ATI drivers but no luck so far. I've applied the registry tweak, xorg fix and tried multiple wine windows versions without any real improvement. One thing I noticed is lowering the graphical settings keeps wow going longer, so I've come to think the problem might be overheating-problem. Could it be possible the opengl mode (since it outputs more frames per second anyway) uses some GL extension or some ATI card feature that d3d does not and makes it overheat resulting in a complete graphical hardlock? One thing I'm almost certain of, this is ATI related at least when running the game on wine, I've never heard nvidia users having this problem. Guess which of the 2 cards I'm going to choose for my next comp?

4) If and when you get a hardlock, if you have another computer or cellphone with 3rd party software support, use PuTTY or some other SSH client to remotely log on to your computer and kill WoW.exe. Works for me at least, allthough ctrl+alt+F1 or ctrl+alt+backspace has no effect.

Good luck with this problem, I'll keep on looking into it, can't take it without WoW for much longer.

---

### Post by ripperzane on 2008-04-03
No one prolly reads this anymore
But anyhow, meh here goes.
If you have a crash that dosent seem to let you back in but you were just playing, goto your .wine/drive_c/Program Files/World of Warcraft/Cache 
and delete the contents of the Cache folder, or rename the Cache folder if you are not wanting to delete it.

Sometimes this resolves my issue.
RZ

:guitar:

---

