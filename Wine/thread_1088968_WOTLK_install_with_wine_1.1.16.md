---
title: "WOTLK install with wine 1.1.16"
date: 2009-03-06
forum: Wine
---

### Post by jasonmichel on 2009-03-06
just installed the newest version of Wine..got WOW installed with all the patches etc just fine..go to run it and it crashes.  i've read every thread about it and i see alot of mention of the config.wtf file.  Well i can't even get a logon screen.


heres the crash output


World of WarCraft (build 9551)

Exe:      C:\World of Warcraft\Wow.exe
Time:     Mar  6, 2009  3:36:46.024 PM
User:     jason
Computer: jason-laptop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:005D383C

The instruction at "0x005D383C" referenced memory at "0x0079AEA4".
The memory could not be "written".


WoWBuild: 9551
Settings: 
SET readTOS "-1"
SET readEULA "-1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET gxWindow "1"
SET locale "enUS"
SET expansionMovie "0"
SET movie "0"
SET showToolsUI "1"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "54"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "777.000000"
SET specular "1"
SET particleDensity "1.000000"
SET groundEffectDensity "24"


oh and its an HP Pavillion dv7-1170us with 4gb ram nvidia 9600-


Display-
Resolution		: 1440x900 pixels
Vendor		: The X.Org Foundation
Version		: 1.5.2
-Monitors-
Monitor 0		: 1440x900 pixels
-Extensions-
BIG-REQUESTS
Composite
DAMAGE
DOUBLE-BUFFER
DPMS
Extended-Visual-Information
GLX
MIT-SCREEN-SAVER
MIT-SHM
MIT-SUNDRY-NONSTANDARD
NV-CONTROL
NV-GLX
RANDR
RECORD
RENDER
SECURITY
SHAPE
SYNC
TOG-CUP
X-Resource
XC-APPGROUP
XC-MISC
XFIXES
XFree86-DGA
XFree86-Misc
XFree86-VidModeExtension
XINERAMA
XInputExtension
XKEYBOARD
XTEST
XVideo
-OpenGL-
Vendor		: NVIDIA Corporation
Renderer		: GeForce 9600M GT/PCI/SSE2
Version		: 2.1.2 NVIDIA 173.14.12
Direct Rendering		: Yes

---

### Post by jasonmichel on 2009-03-09
bump

---

### Post by NightMKoder on 2009-03-09
[https://help.ubuntu.com/community/WorldofWarcraft#Configuration](https://help.ubuntu.com/community/WorldofWarcraft#Configuration)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

In the least add SET gxApi "opengl" in your config. Also would be nice if you gave us the wine console output.

---

### Post by jasonmichel on 2009-03-09
how can i get you the wine console output?

---

### Post by jasonmichel on 2009-03-16
ok..heres the issue...i don't have a config file...all i have is a "Runonce.wtf"  i am attaching screenshot.

SET readTOS "-1"

SET readEULA "-1"

SET readScanning "-1"

SET readContest "-1"

SET readTerminationWithoutNotice "-1"

SET checkAddonVersion "1"

SET installType "Retail"

and in the second one, this is entered

SET readTOS "-1"

SET readEULA "-1"

SET readScanning "-1"

SET readContest "-1"

SET checkAddonVersion "1"

SET locale "enUS"

SET expansionMovie "1"

SET movie "1"

SET showToolsUI "1"

---

