---
title: "WINE questions"
date: 2009-11-06
forum: Wine
---

### Post by JaxDragon on 2009-11-06
I just wubi'd a 30GB ubuntu installation, and installed wine via apt-get. I would like to play team fortress 2, and I was told running windows programs from your physical C drive could cause problems. So I'm wondering if I could just copy over my team fortress 2 files, and run them directly from ubuntu. I know there are extra steps to running orange box games etc., I just want to know if I can copy the game files so I don't have to redownload them.

---

### Post by madverb on 2009-11-06
There are steps on the steam wiki on how to move across steam files to another computer. You can also make backup of steam games and copy them across.

Team Fortress 2 doesn't work very well with Wine.
Here's hoping that Valve make a linux port!

---

### Post by JaxDragon on 2009-11-06
Alright thanks! Shame TF2 has issues with wine. Hopefully it's at least playable.

---

### Post by beastrace91 on 2009-11-06
> **madverb said:**
> Team Fortress 2 doesn't work very well with Wine.
Here's hoping that Valve make a linux port!

What are you talking about? TF2 is almost always ranked at Gold or Plat level on the Wine appdb. It runs quiet flawlessly with little-to no extra configuration. The only thing is you are best off setting it to run with -dxlevel 81 at the launch options as this gives a much better FPS.

Still a native Linux port would be best - but I have a feeling we will see Bill Gates running Ubuntu before this happens >.<

EDIT: @OP regarding your comment about running applications off your Window's partition, for some applications with Wine this works fine how ever Steam/Steam games are not among these (has to do with an issue involving the way ntfs is mounted on Linux & Wine conflicting.)

Regards,
~Jeff

---

### Post by madverb on 2009-11-08
Yes, TF2 does get high ranking on winehq but I find the problems that come with this gold/platinum experience sort of take away from it actually been rated that.
The problems I have had with it in wine are the same as most people but for some reason they can get past these problems and call it a Gold experience.

Flawless, to me, means that the game runs the same using Wine as in Windows. It is not flawless.

---

### Post by pataphysician on 2009-11-08
I just installed TF2 and it was very easy. There's a package manager for Wine called wine-doors that has steam in its repository (or whatever it uses). You can install wine-doors through synaptic, then run it and chose which Windows software you want. For TF2 you need to install Steam, the Tahoma font, and DX9.

Once that's installed, I'm *pretty sure* you can just copy your game files over into the relevant directory in the virtual "c:\" drive in your home directory. Something like /home/YOUR_NAME/.wine/dosdevices/c:/Program Files/Steam/steamapps/YOUR_STEAM_NAME

Your Windows partition where steam is installed should also have a folder within the Steam directory that's "your steam name," or whatever, and I'd guess you can copy that whole thing over into /steamapps

---

### Post by beastrace91 on 2009-11-08
> **madverb said:**
> Flawless, to me, means that the game runs the same using Wine as in Windows. It is not flawless.

What is your hardware/configuration? Other than TF2 running at a slightly slower frame rate (which is easily corrected as I stated by running in dxlevel 81 mode) I had 0 extra configuration in Wine.

I understand just because it worked for me does not mean it will work for you. But in that same respect just because it was a bit bumpy for you doesn't mean it be that bumpy for someone else.

And just as a heads up a gold rating means the application runs 100% fine AFTER configuration tweaks and changes... So if you have to play with it to get it working & after the tweaks it works fine then it is indeed gold rating.

~Jeff

---

### Post by pataphysician on 2009-11-08
> **beastrace91 said:**
> What is your hardware/configuration? Other than TF2 running at a slightly slower frame rate (which is easily corrected as I stated by running in dxlevel 81 mode) I had 0 extra configuration in Wine.

I understand just because it worked for me does not mean it will work for you. But in that same respect just because it was a bit bumpy for you doesn't mean it be that bumpy for someone else.

And just as a heads up a gold rating means the application runs 100% fine AFTER configuration tweaks and changes... So if you have to play with it to get it working & after the tweaks it works fine then it is indeed gold rating.

~Jeff

I'm not the guy you were replying to so I hope it's ok if I jump in here, and ask what tweaks were necessary and what hardware you're running TF2 on? I installed as above, using wine-doors and then installing the game via Steam. Even with DX8.1 and all graphical settings turned down, I'm seeing 10-15FPS. My hardware isn't that great (Athlon 64 X2 4400, 2GB RAM, GeForce 7950 GT [190.42 drivers]). I only see ~50fps average in Windows, so I'm wondering if I'm just running into a hardware limitation. However, in another thread ([http://ubuntuforums.org/showpost.php?p=8271836&postcount=24](http://ubuntuforums.org/showpost.php?p=8271836&postcount=24)), this guy's specs look about the same as mine, and he's claiming he can play L4D.

---

### Post by beastrace91 on 2009-11-08
I have the following dropped into my TF2 autoexec.cfg to optimize FPS further - ```
//Chucker's FPS config
 
//Netcode Settings (change to your preference)
rate 25000
cl_cmdrate 101
cl_interp_ratio 1
cl_updaterate 101
cl_interpolate 1

//Actual Video Settings
mat_antialias 0
mat_forceaniso 0
mat_hdr_enabled 0
mat_hdr_level 0
mat_picmip 2
mat_trilinear 0 
mat_vsync 0
r_rootlod 2
mat_dxlevel 81     //Changes DX level to 8.1, remove this if you'd rather have your default
mat_monitorgamma "1.6"  //Ingame Gamma Settings

//FPS Settings
fps_max 0  //Setting to 0 sets no max limit
cl_detaildist "0"
cl_detailfade "0"
cl_drawmonitors "0"
cl_ejectbrass "0"
cl_forcepreload "1"
cl_lagcomp_errorcheck "1"
cl_lagcompensation "1"
cl_downloadfilter "nosounds"
cl_ejectbrass "0"
cl_forcepreload 1
cl_phys_props_enable "0"
cl_phys_props_max "0"
cl_show_splashes "0"
cl_smoothtime "0.01"
cl_smooth 1
commentary 0
mat_aaquality "0"
mat_autoexposure_max "0"
mat_autoexposure_min "0"
mat_bloomscale "0"
mat_bufferprimitives "0"
mat_bumpmap "0"
mat_clipz "1" 
mat_compressedtextures "1"
mat_diffuse "1" 
mat_disable_bloom "1"
mat_disable_fancy_blending "1"
mat_disable_lightwarp "1"
mat_disable_ps_patch "1"
mat_envmapsize "0"
mat_excludetextures "1"
mat_envmaptgasize "0"
mat_fastspecular "1"
mat_filterlightmaps "1"
mat_filtertextures "1"
mat_forceaniso "0"
mat_forcehardwaresync "0"
mat_forcemanagedtextureintohardware "0"
mat_framebuffercopyoverlaysize "0"
mat_hdr_enabled "0"
mat_hdr_level "0"
mat_hdr_manual_tonemap_rate "0"
mat_mipmaptextures "0"
mat_lightmap_pfms "0"
mat_maxframelatency "0"
mat_max_worldmesh_vertices "0"
mat_parallaxmap "0"
mat_picmip "2"
mat_queue_mode "2"
mat_reducefillrate "1"
mat_shadowstate "0"
mat_show_ab_hdr "0"
mat_showlightmappage "-1"
mat_specular "0"
mat_texture_limit "-1"
mat_trilinear "0"
mat_use_compressed_hdr_textures "1"
mat_showenvmapmask "0"
mat_showlowresimage "0"
mat_showmaterials "0"
mat_showmaterialsverbose "0"
mat_supportflashlight "0"
mat_wateroverlaysize "0"
mat_motion_blur_enabled "0"
mat_motion_blur_percent_of_screen_max "0"
mat_softwarelighting "0"
mp_decals "0"
muzzleflash_light "0"
net_maxfragments "1280"
net_maxfragments "1280"
net_showevents "0"
npc_height_adjust "1"
props_break_max_pieces "0"
props_break_max_pieces_perframe "0"
r_3dnow "1"
r_3dsky "0"
r_PhysPropStaticLighting "0"
r_WaterDrawReflection "0"
r_WaterDrawRefraction "0"
r_ambientboost "0"
r_cheapwaterend "1"
r_cheapwaterstart "1"
r_decal_cullsize "0"
r_decals "0"
r_dopixelvisibility "0"
r_drawbatchdecals "0"
r_drawflecks "0"
r_drawmodeldecals "0"
r_drawmodelstatsoverlaymax "1.5"
r_drawmodelstatsoverlaymin "0.01"
r_drawspecificstaticprop "0"
r_dynamic "0"
r_eyeglintlodpixels "0"
r_eyemove "0"
r_eyes "0"
r_eyeshift_x "0"
r_eyeshift_y "0"
r_eyeshift_z "0"
r_eyesize "0"
r_fastzreject "0"
r_flashlightrendermodels "0"
r_unloadlightmaps "1"
r_flashlightrenderworld "0"
r_flex "0"
r_forcewaterleaf "0"
r_lightaverage "0"
r_lod "2"
r_staticprop_lod "4"
r_maxdlights "0"
r_maxmodeldecal "0"
r_maxnewsamples "0"
r_maxsampledist "0"
r_minnewsamples "0"
r_mmx "1"
r_norefresh "0"
r_occlusion "0"
r_renderoverlayfragment "0"
r_queued_decals "1"
r_rootlod "2"
r_ropetranslucent "0"
r_shadowmaxrendered "32"
r_shadowrendertotexture "1"
r_shadows "0"
r_spray_lifetime "0.1"
r_sse "1"
r_sse2 "1"
r_teeth "0"
r_staticpropinfo "0"
r_updaterefracttexture "0"
r_updaterefracttexture "0"
r_visualizeproplightcaching "1"
r_waterdrawreflection "0"
r_waterforceexpensive "0"
r_waterforcereflectentities"0"
rope_averagelight "0"
rope_collide "0"
rope_shake "0"
rope_smooth "0"
rope_smooth_enlarge "0"
rope_smooth_maxalpha "0"
rope_smooth_maxalphawidth "0"
rope_smooth_minalpha "0"
rope_smooth_minwidth "0"
rope_subdiv "0"
rope_wind_dist "0"
 
//Blood settings
violence_ablood 1
violence_agibs 1
violence_hblood 1
violence_hgibs 1
 
echo FPS Config Loaded!
```

Also please note that it is still not as good as it will be on Windows but it still runs just fine.

As to running Left 4 Dead - this is one of those games that if you want to play it on Ubuntu I *strongly* recommend Cedega. My L4D gets nearly 3 times the FPS using Cedega than I get on Wine (25ish vs 75ish).

Regards,
~Jeff

---

### Post by pataphysician on 2009-11-08
Thanks for the reply. Looks like I still can't break the 20fps mark, though, even in a tiny little window.

[http://i34.tinypic.com/1zmoz2f.png](http://i34.tinypic.com/1zmoz2f.png)

I guess I'll just have to chalk it up to out-dated hardware.

---

### Post by beastrace91 on 2009-11-08
Yep. As an FYI running it Windowed also hurts your FPS.

~Jeff

---

