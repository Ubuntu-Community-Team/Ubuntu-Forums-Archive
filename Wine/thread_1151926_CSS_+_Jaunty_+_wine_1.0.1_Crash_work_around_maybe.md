---
title: "CSS + Jaunty + wine 1.0.1 Crash work around maybe ?"
date: 2009-05-07
forum: Wine
---

### Post by Bad Boy Bubby on 2009-05-07
I have been having trouble with source in crashing randomly but I have just played 30 mins no problem  it could be coincidence but before joining the online map I created my own game and had a run around I was testing some new FPS settings.  Anyway before now the longest I have managed to play online has been less than 5 mins so maybe if you first create a local game and then disconnect and join a net game things run better.

I have also been running TF2 and HL2 no problem, neither has crashed on me yet.  The only problem I have found is if you have the in game screen res set different than your desktop when you exit it sometimes logs you straight out of ubuntu and you have to log back in,  I think this is to reset the screen resolution.

Jaunty 9.04
wine 1.0.1
Nvidia Driver 1.80

---

### Post by Bad Boy Bubby on 2009-05-07
Ignore what I said above think it was something I added to my config to help boost FPS below is everything I have added no crashes so far been playin for about 2 hours :P

// Rates and server reg
cl_cmdrate "101"
cl_updaterate "101"
rate "25000"
cl_interp "0.01"
cl_interpolate "1"
cl_lagcomp_errorcheck "0" // Disables lag compensation error checking.
cl_lagcompensation "1" // Compensate for lag.
 
// In game physics and props etc
mp_decals "50" // How many player sprays will be shown.
r_decals "50" // How many items are shown.
cl_drawmonitors "0" // Disables the rendering of in game "monitors" which contain 3d rendered images.
cl_ejectbrass "0" // Disables brass ejection.
cl_forcepreload "1" // Forces the game to load all texture and model information on map load.
cl_phys_props_max "30" // Maximum amount of physics props allowed.
cl_ragdoll_physics_enable "1" // Enables rag-dolls, 0 makes dead bodies disappear.
cl_show_splashes "0" // Disables water splashes.
 
// Engine rendering
r_3dsky "0" // Disables the rendering of 3d sky boxes.
r_decal_cullsize "9999" // Any decals under this size are not rendered.
r_drawbatchdecals "1" // Enables the rendering of decals in batch.
r_drawflecks "0" // Disables the sparks and dirt from bullet impacts.
r_drawmodeldecals "1" // Enables models decals (i.e. blood).
r_eyes "0" // Disables eyes in models.
r_lod "-1" // Level of details on models. -1 = Variable at distance, 0 = None, 1 = Minor, 2 = Less minor.
r_occlusion "1" // Enables the model occlusion system.
r_rootlod "2" // Base lod of the model in the memory.
r_shadowmaxrendered "32" // Max shadows the game will render.
r_shadowrendertotexture "1" // Rendered the shadow texture causing it to match the player model.
r_shadows "1" // Enables shadows.
r_teeth "0" // Disables teeth in models.
r_waterdrawreflection "0" // Disables the rendering of water reflections.
r_waterforceexpensive "0" // Forces cheap water.
props_break_max_pieces "5" // Reduce prop fragmenting.
 
// Materials
mat_antialias "0" // Disables the use of multi-sampling to smooth out edges.
mat_bumpmap "0" // Disables bump mapping.
mat_clipz "0" // Disables optimized Z-Buffer rendering.
mat_compressedtextures "1" // Disables texture compression.
mat_disable_bloom "1" // Disables bloom effects.
mat_hdr_enabled "0" // Disables HDR.
mat_hdr_level "0" // Double Disables HDR.
mat_monitorgamma "1.6" // Lower the number the brighter the screen. Only works in full-screen.
mat_picmip "2" // Changes the resolutions of textures when they're loaded into memory.
mat_reducefillrate "1" // Reduces the fill-rate when the game is run in DXLevel 8.
mat_specular "0" // Disables Specularity on objects.
mat_trilinear "0" // Disables the use of Tri-linear mipmapping.
mat_wateroverlaysize "8" // Sets the resolution of water distortion. Must be multiple of 8.
 
// Hud
hud_centerid "1" // Centers player IDs.
net_graph "0" // Enables net_graph (Required in SS round) 0 is off.
net_graphpos "3" // Adjusts net_graph position-set between 1 and 3.
hud_fastswitch "1" // Allows Fast-switch.
hud_showtargetid "1"// Shows target ID at cursor.
cl_c4progressbar "1" // Draws progress bar when defusing the C4.
cl_righthand "1" // Use right-handed view models.
cl_showfps "2" // Draws fps meter at top of screen (1 = fps, 2 = smooth fps).
cl_crosshairusealpha "1" //Solid Cross-hair.
cl_crosshaircolor "0" // Green Cross-hair.
cl_radartype "1" // 0=Transparent Radar, 1=Solid radar with options to change alpha.
cl_radaralpha "255" // Use to change radar alpha, must have cl_radartype set to "1".
 
// Violence
violence_ablood "1"
violence_agibs "1"
violence_hblood "1"
violence_hgibs "1"
 
// Misc settings
cl_downloadfilter "nosounds" // Disables annoying pub sound downloads.
fps_max "300" // Caps frame-rate. Set to max monitor refresh rate + 1.
jpeg_quality "100" // High quality screen-shots.
 

And compiz is switched on

launch options for game are -dxlevel 81 -heapsize 256000 and -w -h my screen res hl2.exe set to run as win98 in wine config.

Hope this helps

---

