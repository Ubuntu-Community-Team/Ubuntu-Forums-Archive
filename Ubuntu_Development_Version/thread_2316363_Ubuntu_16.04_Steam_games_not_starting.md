---
title: "Ubuntu 16.04 Steam games not starting"
date: 2016-03-07
forum: Ubuntu Development Version
---

### Post by stefano-incontri on 2016-03-07
I thought it was a problem related to the single games, but almost all will not start, crashing at the splash screen.

If i run them via console in the SteamLibrary they do work, running them via Steam gives segmentation fault.
Already opened an issue in the steam forum, but maybe useful to open it here too.

Tell me if you need more info or logs.

Thanks

---

### Post by QIII on 2016-03-07
Please use standard color and font.

Moved to Ubuntu Development Version.

---

### Post by stefano-incontri on 2016-03-08
Yep sorry it was a cut and paste, thought it would have reset font and color.

These are the last lines from .steam/error.log, there's even the crash log dump but it's too big to embed, please tell me where to send it if needed.

```

rm: cannot remove '/home/stefano/.steam/steam': Is a directory
rm: cannot remove '/home/stefano/.steam/bin': Is a directory
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
Installing breakpad exception handler for appid(steam)/version(1454620878)
Installing breakpad exception handler for appid(steam)/version(1454620878)
Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steam)/version(1454620878)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
[0308/084433:ERROR:main_delegate.cc(777)] Could not load cef_extensions.pak
[0308/084433:ERROR:browser_main_loop.cc(203)] Running without the SUID sandbox! See https://code.google.com/p/chromium/wiki/LinuxSUIDSandboxDevelopment for more information on developing with the sandbox on.
Installing breakpad exception handler for appid(steamwebhelper)/version(20160204122139)
Installing breakpad exception handler for appid(steamwebhelper)/version(1454588499)
[0308/084433:ERROR:main_delegate.cc(777)] Could not load cef_extensions.pak
Installing breakpad exception handler for appid(steamwebhelper)/version(20160204122139)
Installing breakpad exception handler for appid(steamwebhelper)/version(1454620878)
Installing breakpad exception handler for appid(steamwebhelper)/version(1454620878)
Installing breakpad exception handler for appid(steam)/version(1454620878)
Installing breakpad exception handler for appid(steam)/version(1454620878)
Installing breakpad exception handler for appid(steam)/version(1454620878)
Installing breakpad exception handler for appid(steam)/version(1454620878)
Installing breakpad exception handler for appid(steam)/version(1454620878)
Installing breakpad exception handler for appid(steam)/version(1454620878)
Created shared memory when not owner SteamController_Shared_mem
Installing breakpad exception handler for appid(steam)/version(1454620878)
Installing breakpad exception handler for appid(steam)/version(1454620878)


** (steam:8173): WARNING **: Unknown device type 14


** (steam:8173): WARNING **: Could not create object for /org/freedesktop/NetworkManager/Devices/1: unknown object type
Installing breakpad exception handler for appid(steam)/version(1454620878)


** (steam:8173): WARNING **: Ignoring invalid property 'secondaries'


** (steam:8173): WARNING **: Ignoring invalid property 'route-data'


** (steam:8173): WARNING **: Ignoring invalid property 'address-data'


** (steam:8173): WARNING **: Ignoring invalid property 'route-data'


** (steam:8173): WARNING **: Ignoring invalid property 'address-data'


** (steam:8173): WARNING **: Ignoring invalid property 'secondaries'


** (steam:8173): WARNING **: Ignoring invalid property 'route-data'


** (steam:8173): WARNING **: Ignoring invalid property 'address-data'


** (steam:8173): WARNING **: Ignoring invalid property 'route-data'


** (steam:8173): WARNING **: Ignoring invalid property 'address-data'


** (steam:8173): WARNING **: Ignoring invalid property 'secondaries'


** (steam:8173): WARNING **: Ignoring invalid property 'route-data'


** (steam:8173): WARNING **: Ignoring invalid property 'address-data'


** (steam:8173): WARNING **: Ignoring invalid property 'route-data'


** (steam:8173): WARNING **: Ignoring invalid property 'address-data'


** (steam:8173): WARNING **: Ignoring invalid property 'secondaries'


** (steam:8173): WARNING **: Ignoring invalid property 'route-data'


** (steam:8173): WARNING **: Ignoring invalid property 'address-data'


** (steam:8173): WARNING **: Ignoring invalid property 'route-data'


** (steam:8173): WARNING **: Ignoring invalid property 'address-data'
Generating new string page texture 2: 48x256, total string texture memory is 49,15 KB
Generating new string page texture 3: 256x256, total string texture memory is 311,30 KB
Installing breakpad exception handler for appid(steam)/version(1454620878)
Installing breakpad exception handler for appid(steam)/version(1454620878)
roaming config store loaded successfully - 558 bytes.
migrating temporary roaming config store
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Installing breakpad exception handler for appid(steam)/version(1454620878)
Failed to init SteamVR because it isn't installed
ExecCommandLine: ""/home/stefano/.steam/ubuntu12_32/steam" "
Installing breakpad exception handler for appid(steam)/version(1454620878)
System startup time: 3,87 seconds
Generating new string page texture 72: 128x256, total string texture memory is 442,37 KB
Generating new string page texture 73: 128x256, total string texture memory is 131,07 KB
Generating new string page texture 74: 64x256, total string texture memory is 507,90 KB
Generating new string page texture 75: 32x256, total string texture memory is 540,67 KB
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
rm: cannot remove '/home/stefano/.steam/bin': Is a directory
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
/usr/bin/ldd: line 119: printf: write error: Broken pipe
ExecCommandLine: "/home/stefano/.steam/root/ubuntu12_32/steam steam://open/driverhelperready"
ExecSteamURL: "steam://open/driverhelperready"
Generating new string page texture 82: 8x256, total string texture memory is 548,86 KB
Generating new string page texture 90: 128x256, total string texture memory is 679,94 KB
Generating new string page texture 114: 128x256, total string texture memory is 811,01 KB
Generating new string page texture 115: 4096x256, total string texture memory is 5,01 MB
Generating new string page texture 116: 2048x256, total string texture memory is 7,10 MB
Generating new string page texture 117: 1024x256, total string texture memory is 8,15 MB
Generating new string page texture 118: 512x256, total string texture memory is 8,68 MB
Game update: AppID 339280 "Strife", ProcID 8320, IP 0.0.0.0:0
ERROR: ld.so: object '/home/stefano/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
ERROR: ld.so: object '/home/stefano/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Setting breakpad minidump AppID = 339280
Steam_SetMinidumpSteamID:  Caching Steam ID:  76561198093677968 [API loaded no]
ERROR: ld.so: object '/home/stefano/.steam/ubuntu12_32/gameoverlayrenderer.so' from LD_PRELOAD cannot be preloaded (wrong ELF class: ELFCLASS32): ignored.
Crash log saved as '/home/stefano/.config/strife/game/crash_1.0.9.1_32.log'
Segmentation fault


Game removed: AppID 339280 "Strife", ProcID 8322 
Generating new string page texture 124: 24x256, total string texture memory is 8,70 MB
Installing breakpad exception handler for appid(steam)/version(1454620878)
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
rm: cannot remove '/home/stefano/.steam/bin': Is a directory
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
grep: symbol lookup error: grep: undefined symbol: pcre_jit_stack_alloc
/usr/bin/ldd: line 119: printf: write error: Broken pipe
ExecCommandLine: "/home/stefano/.steam/root/ubuntu12_32/steam steam://open/driverhelperready"
ExecSteamURL: "steam://open/driverhelperready"
Generating new string page texture 125: 384x256, total string texture memory is 9,09 MB
Installing breakpad exception handler for appid(steam)/version(1454620878)



```

---

### Post by stefano-incontri on 2016-03-09
The last Steam update solved the problem, now everything works flawlessy, it looks like it was just a Steam libraries problem.

---

