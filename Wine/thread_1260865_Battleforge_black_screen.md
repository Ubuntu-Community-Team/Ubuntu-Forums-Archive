---
title: "Battleforge black screen"
date: 2009-09-08
forum: Wine
---

### Post by Ixonal on 2009-09-08
Ok, first things first, runnin Ubuntu 9.04 with Wine 1.1.26

installed battle forge fine, updated with the bash script, blah blah blah. So I run the game, log in, everything comes up as updated, then I can tell that the game wants to play some video files, but I just hear sounds and see big blurs of color, then the mouse cursor changes to what it would be in game, but the screen is black even though I can apparently click on things (click sounds when I click on certain areas)

now, here is my log file
> 
[INFO][Direct3D 9]: Start Scan
[INFO][Direct3D 9]: Found Adapter: NVIDIA GeForce 9800 GT
[INFO][Direct3D 9]: Support SM 3.0
[INFO][Direct3D 9]: End Scan
[INFO][app]: BattleForge Final Build: 269450 (Retail branch)
[INFO][app]: CPU GenuineIntel family 6 (P2, P3, Pentium-M, Athlon) detected.
[INFO][app]: CPU clock speed is ~4159 MHz.
[INFO][app]: CPU has 2 cores.
[INFO][app]: CPU rating is 24 points.
[INFO][app]: GFX rating is 24 points.
[INFO][Create Device]: Switch to display parameters: 1650 × 1050 @ 0 Hz, windowed.
[INFO][Display]: Use Direct3D 9
[INFO][GPU]: Vendor ID = 0x10de
[INFO][GPU]: Device ID = 0x614
[INFO][GPU]: Subsystem ID = 0x0
[INFO][GPU]: Device name = \\.\DISPLAY1
[INFO][GPU]: Device description = NVIDIA GeForce 9800 GT
[INFO][GPU]: Driver version = 7.15.11.8618
[INFO][GPU]: Driver description = Display
[INFO][Create Device]: Vertex shader = 0x300; Pixel shader = 0x300.
[INFO][PssSoundPipeline]: Loading soundpipeline:

 Version: 1
Number of Files:8753
[INFO][PssSoundPipeline]: Loading soundpipeline bf1/sound/SoundPipeline_en.bin finished, 36263.14 seconds of music material in pipe.
[INFO][CPssPhysicalRenderer]: Got Stereo speakers!
[INFO][VisManager]: Loaded 4 different playercolors.
[INFO][VisManager]: Loaded 5 Flame Locator mappings
[INFO][VisManager]: Loaded 3 Generator and 3 Monument descriptions
[WARN][UI]: Failed to load key mapping layout 'Default' from 'C:\users\ixonal\My Documents\BattleForge\keyBindings.xml'. Reason: Could not open file for read (C:\users\ixonal\My Documents\BattleForge\keyBindings.xml)
[WARN][UI]: Failed to load key mapping layout 'Default' from 'C:\users\ixonal\My Documents\BattleForge\keyBindings.xml'. Reason: Could not open file for read (C:\users\ixonal\My Documents\BattleForge\keyBindings.xml)


and the tail end of my wine console output is this
> 
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
ixonal@Reinverka-II:~$ err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on C-Media USB Headphone Set  , disabling mixer
fixme:thread:SetThreadIdealProcessor (0x70): stub
fixme:system:SetProcessDPIAware stub!
fixme:win:DisableProcessWindowsGhosting : stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f264,0x00000000), stub!
fixme:thread:SetThreadIdealProcessor (0x88): stub
fixme:thread:SetThreadIdealProcessor (0x8c): stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33ef44,0x00000000), stub!
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x33fca4, uiNumDevices=2, cbSize=12) stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1c7e60) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1e7f40) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1ec020) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1ec900) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1ecae0) : pBox=(nil) stub
fixme:d3d_surface:IWineD3DVolumeImpl_LockBox (0x1ecbe0) : pBox=(nil) stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1ed820,0x1ed720): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1ed870,0x1ed770): stub
fixme:thread:SetThreadIdealProcessor (0x16a4): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0xcf72708,0xcf72608): stub
fixme:thread:SetThreadIdealProcessor (0x16e4): stub
fixme:thread:SetThreadIdealProcessor (0x16e8): stub
fixme:d3d:state_lastpixel Last Pixel Drawing Disabled, not handled yet
fixme:thread:SetThreadIdealProcessor (0x16e4): stub
fixme:thread:SetThreadIdealProcessor (0x16e4): stub
fixme:thread:SetThreadIdealProcessor (0x16e4): stub


I've tried altering some of the settings in config.xml, but nothing has changed it (except putting it in windowed mode, that helped)

---

### Post by hikaricore on 2009-09-08
Have you read through the appdb page?
Someone might have provided instructions for configuration but i cba to look.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=9288](http://appdb.winehq.org/objectManager.php?sClass=application&iId=9288)

---

### Post by Ixonal on 2009-09-08
yeah, looked through the entries in the wine app database, there was a comment about the same problem, but no replies to it, so that was a dead end (gogo comma splice). I've also tried to google the problem with no luck. seems like it's very uncommon... was hopin something would look fishy in the data I came up with.

---

### Post by Ixonal on 2009-09-10
bump
any ideas? nothing has worked so far...

---

