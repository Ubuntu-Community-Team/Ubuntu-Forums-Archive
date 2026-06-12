---
title: "wow access violation"
date: 2009-11-22
forum: Wine
---

### Post by petrocles on 2009-11-22
Bakground:
Ubuntu 9.10 karmic
kernel linux 2.6.31-14-generic
gnome 2.28.1
memry 1.2g
intel pentium dual core 3.4ghz
ati graphics card
Latest version of wine


Probem:
installed world of warcraft following the ubuntu howto install wine guie. crashes when i click on wow.exe. it mentions access violation

i have edited config.wtf and done the regedit weak

---

### Post by id10twork on 2009-11-22
This helped me [http://ubuntuforums.org/showthread.php?t=1282443;](http://ubuntuforums.org/showthread.php?t=1282443;) for me, I have to give myself permission every time. This may help you also [http://ubuntuforums.org/showthread.php?t=1330927](http://ubuntuforums.org/showthread.php?t=1330927) (read the "Permission Denied" solution)... I guess it just matters what your computer likes better.

---

### Post by petrocles on 2009-11-22
Thank you for reply but the permissions tip has not resolved the issue

the error reads:

this application has encountered a critical error

error 132 (0x85100084) fatal exception
program  c/program files/world of warcraft/wow.exe
exception  0xc0000005(access violation) at 0073:b787897725

the instruction at 0xb7897725 referenced memory at b7897725
the memory could not be read

press ok to terminate

WoWBuild: 10192
Settings: 
SET locale "enGB"
SET hwDetect "0"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET farclip "550.000000"
SET specular "1"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET expansionMovie "0"
SET ffxDeath "0"
SET ffxGlow "0"
SET gxApi "opengl"
SET M2UseShaders "0"
SET realmList "94.23.32.135"
SET coresDetected "2"
SET videoOptionsVersion "2"
SET Gamma "1.000000"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET projectedTextures "1"

(not sure if any other details are required)

---

### Post by petrocles on 2009-11-23
well i appreciate this must  a common problem and hence low response

I will try to uninstall and re-install tonight again tonght

---

### Post by alex.rayu on 2009-11-23
People so much love Linux that they say "Wow access violation"!

---

### Post by petrocles on 2009-11-23
sorry i dont understand. Are you suggesting that you dont like the name of this thread?

When i type in the terminal
wine "C:\Program Files\World of Warcraft\Launcher.exe"
i get a popup saying 

launcher requires write permission to the c/program files/world of warcraft directory to succssfully patch the game. please enabe write accessto the directory using an administrator account


mmm and yet the folder does not have the lock and according to properties i hve enabled rad and write etc!

---

### Post by ebooa on 2009-12-20
i have been experiencing the same problem although i dont have the message about permissions.
how did you attributed the permissions to the launcher, did you run a chmod to the launcher to give it the permissions to run?

---

