---
title: "Quake 4 just stopped working on Neon"
date: 2019-03-08
forum: Ubuntu/Debian BASED
---

### Post by TechnoJunky on 2019-03-08
I have KDE Neon, up to date. I started playing Quake 4 (installed using the old ID supplied .run file) again last week and played up to 3 or 4 days ago. Yesterday evening when I went to play it wouldn't start. So I ran it from the terminal so I could see the output. It showed "./quake4.x86: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory.". I looked up this error and someone suggested this "apt-get install libpulse0:i386". I did and now I get this output:

```
Quake4 V1.4.2 linux-x86 Jun 15 2007
found interface lo - loopback
found interface wlp3s0 - 192.168.1.203/255.255.255.0
found interface tun0 - 10.200.0.38/255.255.255.255
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
enabled Flush-To-Zero mode
--------- Initializing File System ----------
Loaded pk4 /home/Games/quake4/q4base/game000.pk4 with checksum 0xb3abe28c
Loaded pk4 /home/Games/quake4/q4base/game100.pk4 with checksum 0x74b379d9
Loaded pk4 /home/Games/quake4/q4base/game200.pk4 with checksum 0xa3c810d9
Loaded pk4 /home/Games/quake4/q4base/pak001.pk4 with checksum 0xf2cbc998
Loaded pk4 /home/Games/quake4/q4base/pak002.pk4 with checksum 0x7f8d80d1
Loaded pk4 /home/Games/quake4/q4base/pak003.pk4 with checksum 0x1b57b207
Loaded pk4 /home/Games/quake4/q4base/pak004.pk4 with checksum 0x385aa578
Loaded pk4 /home/Games/quake4/q4base/pak005.pk4 with checksum 0x60d50a1d
Loaded pk4 /home/Games/quake4/q4base/pak006.pk4 with checksum 0x9099ed11
Loaded pk4 /home/Games/quake4/q4base/pak007.pk4 with checksum 0xaf301fff
Loaded pk4 /home/Games/quake4/q4base/pak008.pk4 with checksum 0x4ac6f6d9
Loaded pk4 /home/Games/quake4/q4base/pak009.pk4 with checksum 0x36030c7d
Loaded pk4 /home/Games/quake4/q4base/pak010.pk4 with checksum 0x4b80fbda
Loaded pk4 /home/Games/quake4/q4base/pak011.pk4 with checksum 0x8acf4cfa
Loaded pk4 /home/Games/quake4/q4base/pak012.pk4 with checksum 0xbe4120b0
Loaded pk4 /home/Games/quake4/q4base/pak013.pk4 with checksum 0x6ad67f40
Loaded pk4 /home/Games/quake4/q4base/pak014.pk4 with checksum 0xee51cd59
Loaded pk4 /home/Games/quake4/q4base/pak015.pk4 with checksum 0xf5bf4e0c
Loaded pk4 /home/Games/quake4/q4base/pak016.pk4 with checksum 0x2196f58c
Loaded pk4 /home/Games/quake4/q4base/pak017.pk4 with checksum 0x91118a35
Loaded pk4 /home/Games/quake4/q4base/pak018.pk4 with checksum 0x98a14f03
Loaded pk4 /home/Games/quake4/q4base/pak019.pk4 with checksum 0xbc82ac79
Loaded pk4 /home/Games/quake4/q4base/pak020.pk4 with checksum 0xce74cda5
Loaded pk4 /home/Games/quake4/q4base/pak021.pk4 with checksum 0x2ba6e70c
Loaded pk4 /home/Games/quake4/q4base/pak022.pk4 with checksum 0x4e390eec
Loaded pk4 /home/Games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943
Loaded pk4 /home/Games/quake4/q4base/zpak_english.pk4 with checksum 0x5868f530
Loaded pk4 /home/Games/quake4/q4base/zpak_english_01.pk4 with checksum 0xd9f04b8b
Loaded pk4 /home/Games/quake4/q4base/zpak_english_02.pk4 with checksum 0x9dbd91fd
Loaded pk4 /home/Games/quake4/q4base/zpak_english_03.pk4 with checksum 0x2eb6ad8
Loaded pk4 /home/Games/quake4/q4base/zpak_english_04.pk4 with checksum 0xd3fefaa1
Loaded pk4 /home/Games/quake4/q4base/zpak_french.pk4 with checksum 0xbec7cb4
Loaded pk4 /home/Games/quake4/q4base/zpak_italian.pk4 with checksum 0x1e3aa0f
Loaded pk4 /home/Games/quake4/q4base/zpak_spanish.pk4 with checksum 0xb706e2b8
Addon pk4 /home/Games/quake4/q4base/q4cmp_pak001.pk4 with checksum 0xd0813943 is on addon list
Current search path:
/home/carl/.quake4/q4base
/home/Games/quake4/q4base
/home/Games/quake4/q4base/zpak_spanish.pk4 (3542 files)
/home/Games/quake4/q4base/zpak_italian.pk4 (3500 files)
/home/Games/quake4/q4base/zpak_french.pk4 (3462 files)
/home/Games/quake4/q4base/zpak_english_04.pk4 (3 files)
/home/Games/quake4/q4base/zpak_english_03.pk4 (4 files)
/home/Games/quake4/q4base/zpak_english_02.pk4 (21 files)
/home/Games/quake4/q4base/zpak_english_01.pk4 (1 files)
/home/Games/quake4/q4base/zpak_english.pk4 (3457 files)
/home/Games/quake4/q4base/pak022.pk4 (14 files)
/home/Games/quake4/q4base/pak021.pk4 (89 files)
/home/Games/quake4/q4base/pak020.pk4 (11 files)
/home/Games/quake4/q4base/pak019.pk4 (1206 files)
/home/Games/quake4/q4base/pak018.pk4 (3 files)
/home/Games/quake4/q4base/pak017.pk4 (3 files)
/home/Games/quake4/q4base/pak016.pk4 (193 files)
/home/Games/quake4/q4base/pak015.pk4 (34 files)
/home/Games/quake4/q4base/pak014.pk4 (552 files)
/home/Games/quake4/q4base/pak013.pk4 (239 files)
/home/Games/quake4/q4base/pak012.pk4 (1081 files)
/home/Games/quake4/q4base/pak011.pk4 (5620 files)
/home/Games/quake4/q4base/pak010.pk4 (5539 files)
/home/Games/quake4/q4base/pak009.pk4 (1284 files)
/home/Games/quake4/q4base/pak008.pk4 (1289 files)
/home/Games/quake4/q4base/pak007.pk4 (1330 files)
/home/Games/quake4/q4base/pak006.pk4 (1343 files)
/home/Games/quake4/q4base/pak005.pk4 (1395 files)
/home/Games/quake4/q4base/pak004.pk4 (2249 files)
/home/Games/quake4/q4base/pak003.pk4 (1281 files)
/home/Games/quake4/q4base/pak002.pk4 (313 files)
/home/Games/quake4/q4base/pak001.pk4 (5837 files)
/home/Games/quake4/q4base/game200.pk4 (9 files)
/home/Games/quake4/q4base/game100.pk4 (2 files)
/home/Games/quake4/q4base/game000.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
/home/Games/quake4/q4base/q4cmp_pak001.pk4 (119 files)
file system initialized.
---------------------------------------------
------------ Initializing Decls -------------
Loading guides.... 64 loaded
87ms to load 1125k of material
20ms to load 43k of skin
56ms to load 723k of sound
2ms to load 1k of materialType
136ms to load 2889k of lipSync
11ms to load 105k of playback
266ms to load 1690k of effect
---------------------------------------------
-------- Initializing renderSystem ----------
using ARB renderSystem
renderSystem initialized.
---------------------------------------------
Found default language English with VO
.... found additional language 'french' with VO
.... found additional language 'italian' with VO
.... found additional language 'spanish' with VO
696 strings read from strings/english_code.lang
1794 strings read from strings/english_guis.lang
5756 strings read from strings/english_lips.lang
5759 strings read from strings/english_mappack.lang
6235 strings read from strings/english_maps.lang
632 strings read from strings/french_code.lang
1654 strings read from strings/french_guis.lang
5616 strings read from strings/french_lips.lang
5619 strings read from strings/french_mappack.lang
6088 strings read from strings/french_maps.lang
632 strings read from strings/italian_code.lang
1654 strings read from strings/italian_guis.lang
5616 strings read from strings/italian_lips.lang
5619 strings read from strings/italian_mappack.lang
6088 strings read from strings/italian_maps.lang
632 strings read from strings/spanish_code.lang
1654 strings read from strings/spanish_guis.lang
5616 strings read from strings/spanish_lips.lang
5619 strings read from strings/spanish_mappack.lang
6088 strings read from strings/spanish_maps.lang
Couldn't open journal files
execing default.cfg
"ALT" isn't a valid key
"CTRL" isn't a valid key
couldn't exec editor.cfg
execing Quake4Config.cfg
couldn't exec autoexec.cfg
-------- Initializing Sound System ----------
sound system initialized.
---------------------------------------------
--------------- R_InitOpenGL ----------------
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
SDL_ListModes:
1920x1080 1680x1050 1440x900 1280x1024 1280x960 1280x720 1024x768 832x624 800x600 720x576 720x480
720x400 640x480
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
libGL error: unable to load driver: i965_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: i965
libGL error: unable to load driver: i965_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: i965
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
X Error of failed request: BadValue (integer parameter out of range for operation)
Major opcode of failed request: 155 (GLX)
Minor opcode of failed request: 3 (X_GLXCreateContext)
Value in failed request: 0x0
Serial number of failed request: 42
Current serial number in output stream: 43
pure virtual method called
terminate called without an active exception
signal caught: Aborted
si_code -6
Trying to exit gracefully..
pure virtual method called
terminate called recursively
double fault Aborted, bailing out
```

I also play Doom3 on Steam, using Steam Play. Last night I tried that as well and couldn't play anymore. The game loads but the screen is completely gray, unable to see what to choose on the screen. I'm assuming it's related. Any ideas would be greatly appreciated.

---

### Post by QIII on 2019-03-08
Moved to Ubuntu/Debian BASED.

---

### Post by TechnoJunky on 2019-03-10
And now it just starts working, if by magic.  During my troubleshooting I rebooted several times.  It did no good.  The other day I decided to shrink my root partition and add another so that I could install Kubuntu.  The Quake 4 and Steam are both installed on my /home partition which stayed intact.  Quake and Doom3 ran just fine in Kubuntu.  Today I booted back into Neon and the games run just fine.  With the exception of shrinking the root partition, I made no changes to Neon.

---

