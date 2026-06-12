---
title: "No Sound in Starcraft 1"
date: 2010-12-14
forum: Wine
---

### Post by ender4 on 2010-12-14
I installed StarCraft 1 and the Brood Wars expansion set from a battle chest, without any hiccups.  However, when I try to play it, the graphics work fine, but there are a couple seconds of sound when I start the program, and after that no sound.  There isn't any music, no sound when I click on things in the menu.  And no music or sound effects in game play. I have tried using Windows 7, Vista, Windows XP, and Windows 98 compatibility modes, and I have tried both ALSA and OSS in winecfg.  

I am using Kubuntu 10.10, and have also tried running it using an openbox session to no avail.  I have Wine version 1.2.1. 
I have an intel  GM965/GL960 integrated graphics card (not that I think it is the culprit). and the lspci listing for my audio card is: ```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

When I run "wine StarCraft.exe" in the terminal I get output like the following:
```
fixme:advapi:SetSecurityInfo stub
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x32f178,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x19d4c8,0x19d438): stub
```

Any help would be appreciated.  It's just not the same without sound.

---

### Post by ender4 on 2010-12-15
fixed.  I used emulation instead of full for the sound driver (and used ALSA)

---

