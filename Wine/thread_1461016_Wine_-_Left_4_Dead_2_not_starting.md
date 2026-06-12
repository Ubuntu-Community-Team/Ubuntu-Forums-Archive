---
title: "Wine - Left 4 Dead 2 not starting"
date: 2010-04-23
forum: Wine
---

### Post by svendbenno on 2010-04-23
Hi. I'm trying to make the steam version of Left 4 Dead 2 work, but it simply wont start. 

My launch options are: 
```

-w 1440 -h 868 -console -dxlevel 80 -novid

```

When i navigate to the directory and launch the left4dead2.exe it plays the sound from the video in a second, and then closes. 

This is what the terminal prints when i'm launching it:
```

AppFramework : Unable to create system Physics2 Interface v0.5!
fixme:win:EnumDisplayDevicesW ((null),0,0x32e030,0x00000000), stub!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:d3d:debug_d3dformat Unrecognized 1129272385 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1129272385) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1094800211 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1094800211) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1129272385 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1129272385) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1094800211 (as fourcc: SSAA) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1094800211) in the format lookup table
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x155ac8, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x32e230)
The default video config for the machine has changed, updating the current config to match.
Unable to rename c:\program files\steam\steamapps\common\left 4 dead 2\left4dead2\cfg\video.txt to c:\program files\steam\steamapps\common\left 4 dead 2\left4dead2\cfg\video.bak!
Unable to rename c:\program files\steam\steamapps\common\left 4 dead 2\left4dead2\cfg\video.txt to c:\program files\steam\steamapps\common\left 4 dead 2\left4dead2\cfg\video.bak!
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515474505 (as fourcc: INTZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515474505) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1515667794 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1515667794) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 909198916 (as fourcc: DF16) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(909198916) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 1280070990 (as fourcc: NULL) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(1280070990) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
BinkOpen( c:\program files\steam\steamapps\common\left 4 dead 2\left4dead2\media\valve.bik )
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
ALSA lib ../../../src/pcm/pcm.c:7234:(snd_pcm_recover) underrun occured
svend@svend-desktop:~/.wine/drive_c/Program Files/Steam/steamapps/common/left 4 dead 2$ 

```

I'm already running Counter Strike Source and garrysmod fine. 
i'm running Ubuntu 9.10
Have anyone had the same problem and fixed it?

---

### Post by asdfoo on 2010-04-24
just fyi, there is no dxlevel 80 for this game, it was removed for l4d.

you didn't tell us which version of Wine you are using (1.1.43 is most recent), which video card and drivers you have either.

---

### Post by svendbenno on 2010-04-24
I'm running wine-1.1.42


My graphics card is a 250GTS. I'm running the NVIDIA accelerated graphics driver(version 185)

---

### Post by DigitalStimulus on 2010-04-27
Confirmed, I have tried many versions of wine from 1.1.33 up to 1.1.42 and 1.1.43

From what I have read, it seems like this issue is related to Steam and DRM trying to access the game in a specific location (C:) and/or in a specific way (NTFS).

I've tried setting Windows 98, 2000, XP, Vista, and 7 for Steam. I have also run the SteamService with /install /uninstall /repair and /forceinstall options with various Wine configurations.

"Incomplete installation of Left 4 Dead 2 (2)" is always the error.

It seems that around the time of 1.1.35 this was fixed, but a Steam update since then possibly "broke" it again.

Left 4 Dead plays flawlessly, it is L4D2 that doesn't work.

Someone from appdb.winehq.org seems to be able to run L4D2 with Ubuntu 9.10 64 bit and 1.1.43, I have emailed him to find out how and am still awaiting a response.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=18408&iTestingId=52170](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18408&iTestingId=52170)

---

### Post by asdfoo on 2010-04-28
what? are you running this from your windows partition?

if you are, *facepalm*, the Wine FAQ says this is not supported.

---

### Post by 3vi1 on 2010-04-29
> **asdfoo said:**
> what? are you running this from your windows partition?

if you are, *facepalm*, the Wine FAQ says this is not supported.

What makes you think he's doing that?

I have the same problem on one of my systems with an ATI5870 card (latest proprietary fglrx drivers).  Neither L4D nor L4D2 will run on it, though both games run fine on my similarly configured nVidia 9800GTX+ box.

And trust me:  Both are (attempting to) run the games from EXT4.

fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
...

---

### Post by asdfoo on 2010-04-30
> **3vi1 said:**
> What makes you think he's doing that?

I have the same problem on one of my systems with an ATI5870 card (latest proprietary fglrx drivers).  Neither L4D nor L4D2 will run on it, though both games run fine on my similarly configured nVidia 9800GTX+ box.

And trust me:  Both are (attempting to) run the games from EXT4.

fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 826889281 (as fourcc: ATI1) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(826889281) in the format lookup table
...

Just that he said: From what I have read, it seems like this issue is related to Steam and DRM trying to access the game in a specific location (C:) and/or in a specific way (NTFS).

---

### Post by svendbenno on 2010-04-30
I'm not running it from a windows partition.

I installed steam through wine.

---

### Post by DrMelon on 2010-05-01
L4D and L4D2 do not have -dxlevel 80. You must run at dxlevel 90 or higher. Unfortunately, this will make it run slow and be unstable.

---

### Post by meteorbytes on 2010-11-12
Did this ever get solved? I'm having the same problem. I'm using wine 1.3.6, nvidia gtx 260 with the current nvidia driver 260.19.12. I'm getting the same console output as above.

---

