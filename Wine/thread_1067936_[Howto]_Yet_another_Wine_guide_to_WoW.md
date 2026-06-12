---
title: "[Howto] Yet another Wine guide to WoW"
date: 2009-02-12
forum: Wine
---

### Post by cb951303 on 2009-02-12
[SIZE="4"]**Who's this howto for?**[/SIZE]

This howto is not for everyone. It works on my computer, but might not work on your system.

*My system's specs are:*
[LIST]
[*]Nvidia 6600GT with 180.11 driver
[*]AMD X2 4200+
[*]3.3 GB RAM
[*]Ubuntu 8.10 32bit
[*]WoW files from a Windows installation
[/LIST]
I'm getting ~14FPS in Dalaran (Graphically the most complex place in game). ~60FPS in general.
Latency is somehow 2-3 times better than Windows.

[SIZE="4"]**What's different from other howtos?**[/SIZE]
[LIST=1]
[*]It doesn't require to add extra repos. Only official packages.
[*]ALT + Tab works without a glitch. Even faster/more stable than Windows.
[*]You can use your native language in WoW.
[/LIST]
[SIZE="4"]**Okay, what do I do?**[/SIZE]

Before starting, make sure direct rendering works. There are a lot of howtos, wiki entries, tutorials etc. about it, so I'm not going to explain it here.

[LIST=1]
[*]Install "**wine**", "**wine-gecko**", "**msttcorefonts**" and "**nvidia-glx-180**" via Synaptic Package Manager.
[*]Restart X server to make sure you are using nvidia-glx-180 and not previous version.
[*]**ALT + F2 -> winecfg**: Set Windows version to XP. Go to audio tab and make sure only ALSA is checked. Don't quit winecfg yet.
[*]Copy the content of "**/usr/share/fonts/truetype/msttcorefonts**" to "**.wine/drive_c/windows/Fonts**" in your home directory.
[*]Copy WoW directory to "**.wine/drive_c/Program Files**"
[*]Rename the "**Interface**", "**WTF**" and "**Cache**" directories in it to "**Interface.bak**", "**WTF.bak**" and "**Cache.bak**".
[*]Go to winecfg window and add "Wow.exe" to the applications list. Select it. Go to the graphics tab and check "Emulate a virtual desktop". Set dimensions to your WoW resolution. Repeat the same thing for "Launcher.exe".
**This step is crucial if you want ALT + Tab to work without losing audio. If there are no other applications open to switch with ALT + Tab, you can call the Gnome panel with ALT + CTRL + Tab.**
[*]Run "Launcher.exe" by double clicking it. See if there is any updates. Click play and then exit WoW.
[*]Open "**Config.wtf**" in the newly created WTF folder. Add the highlighted lines below. Don't worry for the extra lines.
```

SET locale "enGB"
SET portal "eu"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
**SET gxApi "opengl"**
[B]SET gxColorBits "24"
SET gxDepthBits "24"[/B]
SET gxResolution "1280x1024"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "1"
SET movie "0"
SET Gamma "0.900000"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "397"
SET specular "1"
SET particleDensity "1.000000"
SET groundEffectDensity "24"
[B]SET ffxDeath "0"
SET ffxSpecial "0"[/B]
SET mouseSpeed "1"
SET readTOS "1"
SET readEULA "1"
SET readTerminationWithoutNotice "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET realmName "Sporeggar"
SET gameTip "20"
SET VoiceActivationSensitivity "0.39999997615814"
SET gxMultisample "1"
SET gxRefresh "50"
SET gxFixLag "1"
SET movieSubtitle "1"
SET readScanning "-1"
SET readContest "-1"
SET installType "Retail"

```
Some people also adds the line **SET ffxGlow "0"** but I prefer eyecandy over performance here, so...
[*]Run "WoW.exe" by double clicking it. Go to options, Set your resolution. Disable "**Hardware cursor**" if it's not already. Adjust the brightness to your liking.
[*]Optionally you can make a desktop entry like this
```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=World of Warcraft
Type=Application
Terminal=false
Icon[en_US]=/home/cosku/Drive_C/Program Files/World of Warcraft/WoW.svg
Name[en_US]=World of Warcraft
Exec=**env LANG="tr_TR.UTF-8"** WINEPREFIX="/home/cosku/.wine" wine "C:\\Program Files\\World of Warcraft\\Wow.exe"
Icon=/home/cosku/Drive_C/Program Files/World of Warcraft/WoW.svg
Comment[en_US]=
```
Note the highlighted part. It allows me to use my native language keys such as *&#351;, &#287;, &#305;* with WoW. You can have a list of available settings with **locale -a**. If your language is not listed there, you can add it with the command **locale-gen**.
[*]Have fun.

PS: Note that you might have to wait a little too much while starting and quitting WoW.
[/LIST]

---

### Post by L.Rizla on 2009-02-12
Great post cb951303. I had no problems when installing WoW. I run ubunto 8.10 and the process seemed fairly straight forward. I noticed in similar posts regarding WoW alot of people had isues with crashing after the intro movie. I had the same problem. My solution was after some experimentation was to disable the pixel shader radio button under graphics. I have had no issues after that and a better frame rate then with vista.

---

### Post by cb951303 on 2009-02-13
Thank you. Unlike most people, running WoW has always been a very straight forward experience for me. I don't know if it's because of my system but I thought like sharing anyway. Also none of the other howtos mention "Enable Virtual Desktop". Without it ALT + Tab crashes audio. I believe a lot of WoW players use this key combination very often. At least I do :P

*Added FPS values on my system for reference.
*Modified styling.

---

### Post by Mmmbopdowedop on 2009-02-13
That alt+tabbing has been annoying me for around a year now!

Thanks for pointing it out, never really thought about playing with any settings to try and sort it. Makes life alot simpler! Saves playing in Windowed mode so that I could easily switch. :D

Much appreciated. :D

I play WoW in OpenGL mode via Wine, no problems at all installing and I have around 20 more fps than I had in Windows. 
When trying to play in D3D(?) I would have the same problem L.Rizla pointed out and the disable'ing the pixel shaders in winecfg would let me play, though not as smooth & missing textures. This bothered me at first because of the Hardware Cursor, but with the help from the other thread below this with the nifty script, i've no problems.

Anyone else notice it looks nicer in OpenGL? Seems more colorful and less pixelated.

Again, thanks! :)

---

### Post by cb951303 on 2009-02-14
I installed the latest nvidia drivers (180.29) from this PPA: [https://launchpad.net/~anders-kaseorg/+archive/ppa](https://launchpad.net/~anders-kaseorg/+archive/ppa)

so far it works without a problem but I won't change the howto for the sake of simplicity.:popcorn:

---

### Post by cb951303 on 2009-02-18
Another thing I couldn't find googling is howto set my locale properly in wine. In windows I was able to use my native language's letters in WoW but wine didn't allow me to do that. Fortunately winehq forums helped. I added what you need to do in order to support your language in wine + WoW (assuming WoW already supports it) :popcorn:

---

### Post by L.Rizla on 2009-02-20
I found a way to fix the audio crashing when pressing alt-tab. I just pressed alt-tab a whole bunch and at the same time pressing the hide all windows button. Found that out randomly.

---

