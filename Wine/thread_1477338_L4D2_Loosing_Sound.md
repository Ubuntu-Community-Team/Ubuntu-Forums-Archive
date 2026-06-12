---
title: "L4D2 Loosing Sound"
date: 2010-05-08
forum: Wine
---

### Post by Tumpster on 2010-05-08
Hey there, I seem to be loosing sound while playing the game. It goes away very suddenly or will loose certain parts. For instance I will be playing a map, get hit with a swarm and will loose all sound except for gun sounds, or sounds the bullets make when hitting something. I can't hear any voices or music anymore until I restart the game. Getting to a new level does nothing to help at all. Any ideas on how to fix this? I am running the Alsa audio through wine.

---

### Post by beastrace91 on 2010-05-08
I'm sure this thread will get moved shortly - but in the future please post Wine questions in the [Wine Forum](http://ubuntuforums.org/forumdisplay.php?f=313)

That being said - what Wine version what Ubuntu version?

~Jeff

---

### Post by Bölvaður on 2010-05-08
> **Tumpster said:**
> ........through wine.
> [COLOR=Red]Wine and Windows related games on linux, please post them [in our wine forum]("http://ubuntuforums.org/forumdisplay.php?f=313").
If not they will be deleted or closed.[/COLOR]


L4D works fine, have no idea about 2.
I would think winehq.org would be a better place to ask this type of questions if the wine subforum here on the ubuntuforums is unable to

---

### Post by Tumpster on 2010-05-08
> **Bölvaður said:**
> L4D works fine, have no idea about 2.
I would think winehq.org would be a better place to ask this type of questions if the wine subforum here on the ubuntuforums is unable to

I'm running 1.043 of Wine and Karmic Koala 64bit.

---

### Post by Tumpster on 2010-05-10
Bump, is anyone else having this problem?

---

### Post by cogadh on 2010-05-10
Run the game from the terminal and post Wine's error output here, it might help identify what is going on.

---

### Post by Tumpster on 2010-05-10
Well I don't get any error, the sound just drops off, theres no rhyme or reason to it. I can keep playing just fine I just loose parts of the sound.

---

### Post by cogadh on 2010-05-10
There are absolutely no error messages in the terminal when the sound quits? That doesn't seem possible, especially since you can't run anything in Wine without it producing some kind of error output.

---

### Post by Tumpster on 2010-06-19
The log file I get in Wine through the terminal is too long to try to copy to anything to read it all. It's completely at random. Suggestions?

---

### Post by Tumpster on 2010-06-25
Any help appreciated!

---

### Post by Tumpster on 2010-06-29
HElp~

---

### Post by Tumpster on 2010-06-29
fixme:dwmapi: DwmSetWindowAttribute (0x100aa, 3, 0x32d838, 4) stub
fixme:dwmapi: DwmSetWindowAttribute (0x100aa, 4, 0x32d834, 4) stub
fixme:dwmapi: DwmSetWindowAttribute (0x100b4, 2, 0x32d304, 4) stub
fixme:dwmapi: DwmSetWindowAttribute (0x100b4, 3, 0x32d300, 4) stub
fixme:dwmapi: DwmSetWindowAttribute (0x100b4, 4, 0x32d2fc, 4) stub
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUse r returning no proxy used
fixme:dwmapi: DwmSetWindowAttribute (0x100d0, 2, 0x32d96c, 4) stub
fixme:dwmapi: DwmSetWindowAttribute (0x100d0, 3, 0x32d968, 4) stub
fixme:dwmapi: DwmSetWindowAttribute (0x100d0, 4, 0x32d964, 4) stub
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:winhttp:WinHttpGetIEProxyConfigForCurrentUse r returning no proxy used
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:threadpool:RtlQueueWorkItem Flags 0x4 not supported

---

### Post by Tumpster on 2010-06-29
> **cogadh said:**
> Run the game from the terminal and post Wine's error output here, it might help identify what is going on.

Here's a log I get or a chunk of it at least:

fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x2911b3b8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18d55a78 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18d55918 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x292bd808 Wrong thread, returning 1.
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x16ea58: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x18e808: Downloading rgb texture to reload it as srgb
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18e1c518 Wrong thread, returning 1.
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x16ea58: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x18e808: Downloading rgb texture to reload it as srgb
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x28d8be58 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x166ddbc8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x2911b5c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x2911b468 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x166dd9d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18d559c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x28a84f18 Wrong thread, returning 1.
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x16ea58: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x18e808: Downloading rgb texture to reload it as srgb
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1a2094d8 Wrong thread, returning 1.
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x16ea58: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x18e808: Downloading rgb texture to reload it as srgb
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x28d8bf08 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x28d8bda8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x2911b518 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x2911b3b8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18d55a78 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18d55918 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x163ab5e0 Wrong thread, returning 1.
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x16ea58: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x18e808: Downloading rgb texture to reload it as srgb
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x28d8bf60 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x28d8be00 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x2911b570 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x2911b410 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x166dd998 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18d55970 Wrong thread, returning 1.
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x16ea58: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x18e808: Downloading rgb texture to reload it as srgb
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x28d8be58 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x166ddbc8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x2911b5c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x2911b468 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x166dd9d8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18d559c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x294bd4c0 Wrong thread, returning 1.
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x16ea58: Downloading rgb texture to reload it as srgb
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x18e808: Downloading rgb texture to reload it as srgb
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x16381980 Wrong thread, returning 1.
fixme:d3d_surface:IWineD3DSurfaceImpl_LoadLocation 0x16ea58: Downloading rgb texture to reload it as srgb
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x15a1d618 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x193c8b28 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x293bc360 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x293bc3b8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x28208298 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x15c4c448 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x15c4c4a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x28c407b0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x162b7960 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x162b79b8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29434348 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x15c2a980 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19780148 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29dfc078 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1677b288 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1677b2e0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29d53ca0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29d53ce0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18d55020 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x27cf37c0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1a052668 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1a0526c0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1a052718 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x162d0760 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x162d07b8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x162d0810 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x162d0480 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x162d05e0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x195f67e8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29de2f38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29e844f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x2958e3b8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x2958e410 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29aefa60 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x195f66e0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x195f6738 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29d34278 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29e84400 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29e5ab40 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29e5ac98 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29e5acd8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29e5ae88 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29e5aec8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29e5af20 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29c74410 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x163aae08 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29666700 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x27277800 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29bc1108 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29bc1160 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29b074a8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29b07500 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29ee3908 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x163c02a8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x163c0300 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x163c0358 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x163c0408 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x163c0460 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29ee36a0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29ee36f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29ee3800 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29ee3858 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29f9f7b8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29f9f810 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29f9f918 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29f9f970 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x28d8bda8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x28d8bf08 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18d55918 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18d55a78 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19fcb618 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19fcb6c8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x19fcb720 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29612d38 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x29612de8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x27337030 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1a203ba8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18ba4738 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18ba4790 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1b33f8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x15d5b5f0 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x285ce6b8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x285ce710 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x285ce768 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1a203af8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1a203b50 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x18baee68 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1988b230 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1988b288 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x1a4a2bf8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x2911b3b8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x2911b518 Wrong thread, returning 1.
Unable to remove z:\home\craig\.playonlinux\wineprefix\steam\drive_c\program files\steam\steamapps\common\left 4 dead 2\left4dead2\textwindow_temp.html!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_END_BROWSER_SESSION: STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB
fixme:avifile:AVIFileExit (): stub!
Reference Count for Material ___error (1) != 0
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x2911eb00 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x16381b10 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x2985d170 Wrong thread, returning 1.
Reference Count for Material vgui_white (1) != 0
Reference Count for Material __background (1) != 0
Reference Count for Material __loading (1) != 0
Reference Count for Material __particlesdepthwrite (1) != 0
Reference Count for Material __particlesdepthwrite (1) != 0
Reference Count for Material __fontpage (1) != 0
Reference Count for Material __fontpage (1) != 0
Reference Count for Material __fontpage (1) != 0
Reference Count for Material __fontpage (1) != 0
Reference Count for Material __fontpage (1) != 0
Reference Count for Material __fontpage (1) != 0
Reference Count for Material __fontpage (1) != 0
Reference Count for Material __fontpage (1) != 0
Reference Count for Material __fontpage (1) != 0
Reference Count for Material __fontpage (1) != 0
Reference Count for Material __fontpage (1) != 0
Reference Count for Material __fontpage (1) != 0
Reference Count for Material __fontpage (1) != 0
Reference Count for Material __fontpage_additive (1) != 0
Reference Count for Material __vgui_texture_0 (1) != 0
Reference Count for Material debug/particleerror (1) != 0
Reference Count for Material particle/spray1/spray1 (38) != 0
Reference Count for Material particle/pebble1/particle_pebble_1 (10) != 0
Reference Count for Material particle/smoke1/smoke1 (24) != 0
Reference Count for Material particle/vistasmokev1_min_depth_nearcull (17) != 0
Reference Count for Material particle/warp_ripple2 (2) != 0
Reference Count for Material particle/blood_splatter/blood_splatter (7) != 0
Reference Count for Material particle/droplets/droplets_minsize_nodepth (3) != 0
Reference Count for Material particle/particle_glow_04_additive_nodepth (1) != 0
Reference Count for Material particle/spray1/spray1_nodepth (1) != 0
Reference Count for Material particle/particle_glow_04_additive (4) != 0
Reference Count for Material particle/fire_burning_character/fire_screen_crop (1) != 0
Reference Count for Material particle/warp_ripple3 (2) != 0
Reference Count for Material particle/particle_modulate_01_noz (1) != 0
Reference Count for Material particle/particle_flares/particle_flare_001_nodepth_noz (4) != 0
Reference Count for Material particle/smoker_tongue_beam (3) != 0
Reference Count for Material particle/smoker_tongue_joint (1) != 0
Reference Count for Material particle/spray1/spray1_streak (3) != 0
Reference Count for Material particle/particle_spore/particle_spore (3) != 0
Reference Count for Material particle/vistasmokev1/vistasmokev4_nearcull (7) != 0
Reference Count for Material particle/vistasmokev1/vistasmokev1 (9) != 0
Reference Count for Material particle/vistasmokev1/vistasmokev4_nocull (2) != 0
Reference Count for Material particle/droplets/droplets (2) != 0
Reference Count for Material particle/vistasmokev1_fog_add (1) != 0
Reference Count for Material particle/particle_glow_03_streak (1) != 0
Reference Count for Material particle/particle_glow_01_streak (1) != 0
Reference Count for Material particle/blood_core_streak (1) != 0
Reference Count for Material particle/water_splash/water_splash (14) != 0
Reference Count for Material particle/beam_smoke_01_alpha (3) != 0
Reference Count for Material particle/headshot/headshot (8) != 0
Reference Count for Material particle/particle_debris_burst/particle_debris_burst_002 (10) != 0
Reference Count for Material particle/particle_flares/particle_flare_004 (3) != 0
Reference Count for Material particle/blood_mist/blood_mist (12) != 0
Reference Count for Material particle/fire_particle_4/fire_particle_4 (49) != 0
Reference Count for Material particle/particle_flares/particle_flare_004_nodepth (1) != 0
Reference Count for Material particle/vistasmokev1_add_nearcull (2) != 0
Reference Count for Material particle/screenspaceboomervomit (2) != 0
Reference Count for Material particle/particle_gauze (2) != 0
Reference Count for Material particle/particle_ring_wave_12 (6) != 0
Reference Count for Material particle/particle_ring_wave_10_add (3) != 0
Reference Count for Material particle/water_splash/water_splash_nodepth (40) != 0
Reference Count for Material particle/smoke1/smoke1_additive (2) != 0
Reference Count for Material particle/particle_glow_01 (1) != 0
Reference Count for Material particle/impact/fleks (67) != 0
Reference Count for Material particle/crackedpavementdecal (1) != 0
Reference Count for Material particle/vistasmokev1/vistasmokev1_nearcull (25) != 0
Reference Count for Material particle/particle_glow_03 (3) != 0
Reference Count for Material particle/blood_core (11) != 0
Reference Count for Material particle/blood_drop (1) != 0
Reference Count for Material particle/blood_mist/blood_mist_nodepthblend (4) != 0
Reference Count for Material particle/beam_blood_01 (8) != 0
Reference Count for Material particle/bleedout_01 (3) != 0
Reference Count for Material particle/goo/goo2 (4) != 0
Reference Count for Material particle/smoke1/smoke1_nearcull (9) != 0
Reference Count for Material particle/vistasmokev1/vistasmokev4_addself_nearcull (5) != 0
Reference Count for Material particle/intestines_beam (3) != 0
Reference Count for Material particle/water_splash/water_splash_streak (14) != 0
Reference Count for Material particle/sparks/sparks_alpha (1) != 0
Reference Count for Material particle/water_splash/water_splash_nodepth_maxsize (4) != 0
Reference Count for Material particle/particle_ring_wave_8_add_nearcull (1) != 0
Reference Count for Material particle/particle_glow_01_additive (3) != 0
Reference Count for Material particle/particle_glow_03_additive (2) != 0
Reference Count for Material particle/particle_ring_wave_9_add (1) != 0
Reference Count for Material particle/particle_modulate_01_nearcull (2) != 0
Reference Count for Material particle/particle_flares/particle_flare_001_nodepth_noz_minsize (2) != 0
Reference Count for Material particle/particle_flares/particle_flare_007b_nodepth (1) != 0
Reference Count for Material particle/particle_flares/particle_flare_009_nodepth_noz_minmax (1) != 0
Reference Count for Material particle/flashlight_glow (3) != 0
Reference Count for Material particle/particle_flares/particle_flare_003_nodepth (1) != 0
Reference Count for Material particle/beam_smoke_01 (13) != 0
Reference Count for Material particle/beam_flashlight (1) != 0
Reference Count for Material particle/particle_muzzleflash4 (3) != 0
Reference Count for Material particle/particle_spark (22) != 0
Reference Count for Material vgui/white (2) != 0
Reference Count for Material particle/particle_muzzleflash2 (3) != 0
Reference Count for Material particle/particle_muzzleflashx (4) != 0
Reference Count for Material particle/particle_modulate_01 (1) != 0
Reference Count for Material particle/particle_glow_04 (1) != 0
Reference Count for Material particle/fire_burning_character/fire_burning_character_nodepth (8) != 0
Reference Count for Material particle/muzzleflashcloud (4) != 0
Reference Count for Material particle/particle_glow_05_additive (1) != 0
Reference Count for Material particle/fire_burning_character/fire_burning_character (5) != 0
Reference Count for Material particle/impact/fleks2 (10) != 0
Reference Count for Material particle/fire_particle_4/fire_particle_4_ob (1) != 0
Reference Count for Material particle/sparks/sparks (11) != 0
Reference Count for Material particle/vistasmokev1/vistasmokev1_fire5_noz (1) != 0
Reference Count for Material particle/vistasmokev1/vistasmokev1_fire (4) != 0
Reference Count for Material particle/particle_flares/particle_flare_004b_mod_ob (4) != 0
Reference Count for Material particle/particle_ring_wave_2 (2) != 0
Reference Count for Material particle/spray1/spray1_addself (4) != 0
Reference Count for Material particle/particle_debris_burst/particle_debris_burst_001 (6) != 0
Reference Count for Material particle/particle_glow_02_add_15ob_trail (2) != 0
Reference Count for Material particle/particle_glow_07_15ob (1) != 0
Reference Count for Material particle/particle_glow_05_add_15ob_minsize (1) != 0
Reference Count for Material particle/particle_glow_05_add_5ob (1) != 0
Reference Count for Material particle/vistasmokev1_add_nearcull_nodepth (1) != 0
Reference Count for Material particle/particle_debris_02 (2) != 0
Reference Count for Material particle/particle_glow_05_add_15ob_noz (3) != 0
Reference Count for Material particle/fire_burning_character/fire_molotov_crop (1) != 0
Reference Count for Material particle/fire_burning_character/fire_burning_character_noz (1) != 0
Reference Count for Material particle/particle_flares/particle_flare_001_nodepth_noz_nearfade (1) != 0
Reference Count for Material particle/particle_muzzleflash2_noz (2) != 0
Reference Count for Material particle/particle_glow_05_additive_noz_minsize (2) != 0
Reference Count for Material particle/particle_glow_05_additive_noz_minmaxsize (1) != 0
Reference Count for Material particle/particle_flares/particle_flare_007b_noz (1) != 0
Reference Count for Material particle/shells/particle_shells (12) != 0
Reference Count for Material particle/beam_smoke_01_addself (2) != 0
Reference Count for Material particle/fire_particle_2/fire_particle_2 (1) != 0
Reference Count for Material particle/smoke1/smoke1_nearcull3 (1) != 0
Reference Count for Material particle/fire_particle_2/fire_particle_2_ob (2) != 0
Reference Count for Material particle/particle_flares/particle_flare_001_nodepth_noz_ob (1) != 0
Reference Count for Material particle/vistasmokev1/vistasmokev4_addself_nearcull_ob (1) != 0
Reference Count for Material particle/particle_meleeblur_noz (10) != 0
Reference Count for Material particle/water/water_beam_01_warp_alpha (1) != 0
Reference Count for Material particle/particle_smokegrenade_sc (19) != 0
Reference Count for Material particle/star_ob_noz (1) != 0
Reference Count for Material particle/smoke1/smoke1_fade (3) != 0
Reference Count for Material particle/leaf/leafdead (2) != 0
Reference Count for Material particle/warp_ripple (1) != 0
Reference Count for Material particle/star_noz (2) != 0
Reference Count for Material particle/warp_ripple3_noz (1) != 0
Reference Count for Material particle/star_ob (1) != 0
Reference Count for Material engine/writez (1) != 0
Reference Count for Material vgui/hud/800corner1 (1) != 0
Reference Count for Material vgui/hud/800corner2 (1) != 0
Reference Count for Material vgui/hud/800corner3 (1) != 0
Reference Count for Material vgui/hud/800corner4 (1) != 0
Reference Count for Material vgui/../vgui/hud/splatter1 (1) != 0
Reference Count for Material vgui/../vgui/hud/splatter2 (1) != 0
Reference Count for Material vgui/../vgui/hud/splatter3 (1) != 0
Reference Count for Material vgui/../vgui/hud/splatter_corner_upper_right (1) != 0
Reference Count for Material vgui/../vgui/hud/splatter_horizontal_bottom (1) != 0
Reference Count for Material vgui/campaignframe (1) != 0
Reference Count for Material vgui/healthbar_white (1) != 0
Reference Count for Material vgui/healthbar_grey (1) != 0
Reference Count for Material vgui/hud/iconsheet (1) != 0
Reference Count for Material vgui/hud/iconsheet2 (1) != 0
Reference Count for Material models/infected/common/l4d2/ci_shadowbuild (1) != 0
Reference Count for Material vgui/hud/pz_charge_meter (1) != 0
Reference Count for Material vgui/hud/infected_healthbar_bg_1 (1) != 0
Reference Count for Material vgui/hud/zombieteamimage_hunter (1) != 0
Reference Count for Material vgui/hud/healthbar_bg_1 (1) != 0
Reference Count for Material vgui/hud/healthbar_bg_2 (1) != 0
Reference Count for Material vgui/hud/healthbar_bg_3 (1) != 0
Reference Count for Material vgui/hud/survivaltimerbackground (1) != 0
Reference Count for Material vgui/hud/survivaltimerclockface (1) != 0
Reference Count for Material vgui/hud/survivaltimerclock (1) != 0
Reference Count for Material vgui/../vgui/menu_mode_versus (1) != 0
Reference Count for Material vgui/menu_mode_versus (1) != 0
Reference Count for Material vgui/../vgui/menu_mode_scavenge (1) != 0
Reference Count for Material vgui/menu_mode_scavenge (1) != 0
Reference Count for Material vgui/left4dead2logo (1) != 0
Reference Count for Material vgui/menu_backgroud_top (1) != 0
Reference Count for Material vgui/menu_backgroud_bottom (1) != 0
Reference Count for Material vgui/menu_mode_border (1) != 0
Reference Count for Material vgui/arrow_left (1) != 0
Reference Count for Material vgui/arrow_right (1) != 0
Reference Count for Material vgui/menu_mode_mutation (1) != 0
Reference Count for Material vgui/menu_mode_realism (1) != 0
Reference Count for Material vgui/menu_mode_realismversus (1) != 0
Reference Count for Material vgui/menu_mode_survival (1) != 0
Reference Count for Material cable/rope_shadowdepth (1) != 0
Reference Count for Material engine/preloadtexture (1) != 0

---

### Post by cogadh on 2010-06-29
Use the forum "CODE" tags (they work just like "QUOTE" tags), it will allow the error output to stay formatted correctly (no smileys) and it will become a scrollable text box within your post, instead of a long multi-screen post like it is now. Also, we only need the section of it from the moment you lost sound, not the entire thing. From what I can see, none of that has anything to do with sound issues and nearly all of the messages are "fixme" errors related to graphics rendering, which only really matter to Wine developers ("fixme" errors are developers notes about things they still need to work on in Wine). If there are no sound-related errors at the time you lose sound,then the problem is likely not a problem with Wine, but rather with ALSA.

---

### Post by Tumpster on 2010-06-30
Well, I removed pulseaudio and tried running ALSA soley and it still had problems. I then uninstalled L4D2 and reinstalled and still no luck, I've now wiped my machine and upgraded to 10.04 LTS and will be trying it out shortly.

---

