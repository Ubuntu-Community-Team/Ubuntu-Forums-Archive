---
title: "Missing Models in Source Games"
date: 2010-10-02
forum: Wine
---

### Post by SuperNapalm on 2010-10-02
My PC
Pentium D 945
2gb ram
Radeon x1650 Pro
Ubuntu Lucid 10.4
Wine 1.3.3

I'm trying to run various source games like HL2 and Goldeneye Source. I can get the games to start and load into the game with working sound but all I can see is the background. All NPCs and various background objects are totally invisible (example in attachment). When I pick up objects they turn invisible and so do objects that interact with NPCs.

HL2 Console Log:
```
maxplayers set to 1
Error: Material "___wireframe_dx9_5" uses unknown shader "Wireframe_DX9"
Steam config directory: Z:\media\New Volume\Steam\steamapps\supernapalm\half-life 2\platform\config
Unknown command "cl_thirdperson"
Can't use cheat cvar cam_snapto in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar cam_ideallag in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar cam_idealdelta in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar cam_idealyaw in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar cam_idealpitch in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar cam_idealdist in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar cam_idealdistright in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar cam_idealdistup in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar cam_collision in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar c_maxpitch in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar c_minpitch in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar c_maxyaw in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar c_minyaw in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar c_maxdistance in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar c_mindistance in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar c_orthowidth in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar c_orthoheight in multiplayer, unless the server has sv_cheats set to 1.
Unknown command "sv_backspeed"
FS:  Tried to Size NULL filename!
Can't use cheat cvar fog_start in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar fog_end in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar fog_color in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar fog_colorskybox in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar fog_color in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar fog_colorskybox in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar fog_color in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar fog_colorskybox in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar fog_startskybox in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar fog_endskybox in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar fog_color in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar fog_colorskybox in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar fog_color in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar fog_colorskybox in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar fog_color in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar fog_colorskybox in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar r_farz in multiplayer, unless the server has sv_cheats set to 1.
Can't use cheat cvar r_farz in multiplayer, unless the server has sv_cheats set to 1.
Warning: using WorldTwoTextureBlend on a non-displacement surface.
Support for this will go away soon.
   - Material       : nature/red_grass
   - Surface center : -904 -1438 0
Warning: WorldTwoTextureBlend found on a non-displacement surface (material: nature/red_grass). This wastes perf for no benefit.
Redownloading all lightmaps
Dropped Super Napalm from server (Disconnect by user.)
info_hint (HammerID: 0, position (-5596.00, -904.00, 147.69)) with no hint type.
info_hint (HammerID: 0, position (-5608.00, -1176.00, 111.69)) with no hint type.
info_hint (HammerID: 0, position (-5608.00, -1280.00, 155.69)) with no hint type.
Attempting to precache model, but model name is NULL
Dead end link: pod_player24
Dead end link: pod_track_R_07
Dead end link: pod_track_L_08
Warning: using WorldTwoTextureBlend on a non-displacement surface.
Support for this will go away soon.
   - Material       : nature/red_grass_thin
   - Surface center : -8204 -883 320
Failed to load sound "ambience\wind1.wav", file probably missing from disk/repository
Redownloading all lightmaps
```

I have a feeling it might be the gfx drivers (on Edge Open Source atm) but I'm not sure which ones would work better and I heard official ATI ones won't work on Lucid.

If anyone can help me I'd be really grateful :)

---

### Post by Fracta on 2010-11-20
sigh. No replies. I have the same problem. Portal and Painkiller work fine, except that I cant see my gun, npcs are invisible (I can even see the dust kicked up where they walk), and various environment objects are missing (but sometimes still have shadows).

---

### Post by Nowaker on 2012-01-02
Confirming.

---

