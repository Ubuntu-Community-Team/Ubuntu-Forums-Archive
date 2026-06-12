---
title: "Dota2 crashes before loading"
date: 2015-10-21
forum: Ubuntu/Debian BASED
---

### Post by tony97 on 2015-10-21
I'm running DeepinOS which is built ontop of Ubuntu 14.04. Been trying for awhile now to get Dota 2 and the DLC Reborn to work, but it crashes soon after the Dota2 logo. Sometimes it gets as far as to show a small toolbar thing on the bottom left of the client and changes the mouse pointer, but then it crashes to desktop. OS is fully updated, and I'm running the latest Nvidia Proprietary drivers for Nvidia Geforce GT 750m alongside Bumblebee for the optimus support.

I've searched, and am still searching, for a solution but everything i find is outdated and doesn't help. I'm hoping someone here would be able to help me resolve this issue. here is the console errors it's giving...

```
Game update: AppID 570 "Dota 2", ProcID 7718, IP 0.0.0.0:0
ERROR: ld.so: object '/home/tony/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/tony/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
pid 7721 != 7720, skipping destruction (fork without exec?)
ERROR: ld.so: object '/home/tony/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/tony/.local/share/Steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Using breakpad crash handler
Setting breakpad minidump AppID = 570
Forcing breakpad minidump interfaces to load
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Looking up breakpad interfaces from steamclient
Calling BreakpadMiniDumpSystemInit
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198065431052 [API loaded yes]
Steam_SetMinidumpSteamID:  Setting Steam ID:  76561198065431052
Setting breakpad minidump AppID = 373300
Installing breakpad exception handler for appid(gameoverlayui)/version(20151014123426)
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Fontconfig warning: "/media/tony/Linux Extras/Games/steamapps/common/dota 2 beta/game/core/panorama/fonts/conf.d/41-repl-os-win.conf", line 148: Having multiple values in <test> isn't supported and may not work as expected
Fontconfig warning: "/media/tony/Linux Extras/Games/steamapps/common/dota 2 beta/game/core/panorama/fonts/conf.d/41-repl-os-win.conf", line 160: Having multiple values in <test> isn't supported and may not work as expected
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Installing breakpad exception handler for appid(gameoverlayui)/version(1.0)
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  15 (X_QueryTree)
  Resource id in failed request:  0x600006
  Serial number of failed request:  89
  Current serial number in output stream:  89
GetHud called with NULL g_pHudGameSystem!Attempting to create OpenGL context: v3.3 (Core profile)...success.
Attempting to create OpenGL context: v3.3 (Core profile)...success.
DumpContextInfo: OpenGL vendor NVIDIA Corporation
DumpContextInfo: OpenGL renderer GeForce GT 750M/PCIe/SSE2
DumpContextInfo: Using OpenGL context version 3.3
DumpContextInfo: Context supports GLSL version 3.30 NVIDIA via Cg compiler
Game removed: AppID 570 "Dota 2", ProcID 7723 

```

I appreciate any assistance

---

### Post by howefield on 2015-10-21
Hello tony97, welcome to the forum, your thread has been moved to the "Ubuntu/Debian BASED" forum.

---

