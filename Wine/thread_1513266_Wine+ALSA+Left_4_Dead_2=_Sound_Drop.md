---
title: "Wine+ALSA+Left 4 Dead 2= Sound Drop"
date: 2010-06-19
forum: Wine
---

### Post by Tumpster on 2010-06-19
So I've been an avid user of Left 4 Dead 1 and 2. This problem only seems to arise in L4D2, where the audio will cut out. Now, not completely, some things will drop but some stay, for instance, I can hear the noise my gun makes, the shots fired but I don't hear characters talking anymore or any special infected sounds. Another instance is I'll see my gun firing but I'll hear the effects as it's hitting the target I'm pointed at, so I'm loosing all but that and other items. It's really hit or miss what drops and what stays, but one thing is always consistent is the music and music alerts like a horde or tank is coming. I've switched audio config settings in WINECFG to try ESound and it still does it, none of the other audio drivers work for me. I have the latest edition of Wine and have always update the second a new beta drops and it's always remained a problem, even after a new format of my hard drive on another matter. Can anyone help me fix this?

---

### Post by Tumpster on 2010-06-25
Any ideas?

---

### Post by Tumpster on 2010-06-29
Help, please!

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

### Post by sumwonyuno on 2010-07-03
Hello,

I've been having the same reoccuring problem playing Left 4 Dead 2 ever since I got the game.  From my experience, the sound drop problem and the Server not able to authenticate user to Steam problem are potentially related.

The sound drop is likelier to happen when you either rescued (by incap or fall) or you rescue someone else.  You expect the rescue sound to play, but it doesn't, and then most sounds don't play.  There are other instances where this also occurs (like luck), but the rescue one is the most reliable one to reproduce.  Maps like the Passing and Dark Carnival, and game types like realism have a higher chance as well.  I have not noticed any trends on weapons (melee or guns) and items, or characters (survivors or infected).

If you turn on captions and play the game, you expect to see readable words.  When the sound problems occur, you'll see garbage appear in the captions whenever a sound event happens.  You could play with the sound drop until:
- you get kicked off the server (even your own) and get the Server not able to authenticate message
- there is a round change, then the game "breaks", and you'll have to kill left4dead2.exe
- you take the initiative, quit, and restart the game before the first two happen

You could do some of the fixes that Windows users do for crashing, -lv, validation, etc.  However, they will not get to the root of the problem, as this problem can happen every time you play.  I believe the issue is either with wine or the game itself.  There is either a bug in wine and/or in the Left 4 Dead 2 code, or something is not implemented effectively in wine.  The sound drop, disconnection, and broken game are only symptoms of some deeper problem.  Sometimes I can play an entire campaign with no problems, other times the first incap leads to doom, and most of the time is chance.

I can't really recommend any sort of wine or game fixes because virtually everything I've tried is not effective at solving the sound drop problem completely.  I guess a cynical solution is to avoid rescuing when you or your teammate is down, and only play on easy single player Dead Center.

[Edit] A non-exhaustive list of things I have tried, but make no real difference:
- wine through chroot
- v195 nvidia drivers and v256 beta
- updating wine (I'm on 1.2 rc3 right now)
- enforcing file permissions on .wine and Steam folders (e.g. 777)
- parameters such as -lv
- disabling sound in wine
- pulseaudio and alsa
- deleting files and letting Steam redownload
- validation every single time I play (maybe a placebo effect)

Anyone else is welcome to take a whack at the problem, so we can actually whack some zombies without buggy gameplay.

---

### Post by Tumpster on 2010-07-03
THis is very huge as I actually went as far as wiping my whole machine and doing a fresh install. I have had no troubles since but I fear it may be back, I'm attempting to debug right now to see how it goes. Anyone willing to help out, PLEASE feel free to do so, I'll assist in any way I can!

---

### Post by Tumpster on 2010-07-03
YUP! Back in a big way, really wish I could figure this out so I wouldn't think of wipping the hell out of my machine AGAIN.

---

### Post by sumwonyuno on 2010-07-04
If you reinstalled it once, and it still happens, I don't think reinstalling it again will do anything constructive (it would waste a lot of time).  BTW, I've been using Arch Linux, so it may not be distro-specific.  I did wipe and reinstall Arch about a month ago, but I backed up and restored my files for wine and the game.  The problem has happened before and after OS reinstallation.  I'm not keen on redownloading everything for wine, Steam and Left 4 Dead 2 if it hasn't seemed to help.

I've been running the game with -dev and -condebug options, and I haven't noticed anything that comes up when the sound drops.  Ignore the "Stopping all sounds" message, as it's related to bringing up the console and options menu (escape and ~ keys).

---

### Post by Tumpster on 2010-07-04
So far since installing 1.2RC6 of Wine the issue has not come back. SO FAR, I've played for under 2hrs with lots of drops and rescues, we'll see how this goes.

---

### Post by Tumpster on 2010-07-04
> **Tumpster said:**
> So far since installing 1.2RC6 of Wine the issue has not come back. SO FAR, I've played for under 2hrs with lots of drops and rescues, we'll see how this goes.

After 5 hours of zombie killing, team rescuing, bomb exploding fun, the glitch is BACK! I cannot express how overjoyed I am that my audio is dropping again after I rescue someone or someone rescues me. Any help is appreciated!

---

### Post by Tumpster on 2010-07-04
```
 fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x20295e88 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x202969a8 Wrong thread, returning 1.
fixme:d3d:IWineD3DOcclusionQueryImpl_GetData 0x16dcb7c0 Wrong thread, returning 1.
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
Reference Count for Material __fontpage_additive (1) != 0
Reference Count for Material __fontpage_additive (1) != 0
Reference Count for Material __fontpage_additive (1) != 0
Reference Count for Material console/background05_widescreen (1) != 0
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
Reference Count for Material vgui/left4dead2logo (1) != 0
Reference Count for Material vgui/menu_backgroud_top (1) != 0
Reference Count for Material vgui/menu_backgroud_bottom (1) != 0
Reference Count for Material vgui/menu_mode_border (1) != 0
Reference Count for Material vgui/arrow_left (1) != 0
Reference Count for Material vgui/arrow_right (1) != 0
Reference Count for Material vgui/menu_mode_campaign (1) != 0
Reference Count for Material vgui/menu_mode_mutation (1) != 0
Reference Count for Material vgui/menu_mode_realism (1) != 0
Reference Count for Material vgui/menu_mode_realismversus (1) != 0
Reference Count for Material vgui/menu_mode_singleplayer (1) != 0
Reference Count for Material cable/rope_shadowdepth (1) != 0 
```

---

### Post by Tumpster on 2010-07-05
I've opened a bug report on this through WineHQ: [http://bugs.winehq.org/show_bug.cgi?id=23516](http://bugs.winehq.org/show_bug.cgi?id=23516)

---

### Post by sumwonyuno on 2010-07-14
Did you read the new comment under your post in WineHQ on the Left 4 Dead 2 page?

Simply type snd_restart in the console whenever the sound drops, and sound is restored.  The poster is suggesting another program playing sound (e.g. Pidgin) may be contributing to the problem.  I did the command once, and I can say it worked for that time.  I'll have to do some more tests.

---

### Post by Tumpster on 2010-08-18
Still occurring after several Wine updates. Only kicks in after I rescue someone or pick them up! Any ideas?

---

### Post by wesman83 on 2010-08-25
i had this same issue. on my machine it's DEFINITELY pulseaudio causing the problem.

i did a:
killall -9 pulseaudio
then:
killall -9 indicator-sound-service 

and L4D2 works great with no sound issues running for hours and hours :-D

---

### Post by turboemu on 2010-12-02
Iv tried these commands above with no luck. But I don't get any sound ever. I get it in the intro movie but as soon as I see the main menu I never get sound from then on. Any ideas? Im using wine 1.3.8

---

### Post by Mega_Mike on 2012-08-10
I have the exact same issue.  I'm running Left 4 Dead and the intro sounds works, but sound drops in-game and I can't get it back.  Running 1.5.10, amd64.

---

### Post by vladdy on 2012-08-15
Resurrecting old threads won't help, try using the ubuntu wine ppa + pulseaudio

---

