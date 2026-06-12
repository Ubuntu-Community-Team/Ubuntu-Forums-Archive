---
title: "[SOLVED] Nexuiz on Ubuntu Server 8.04 - Doesn't work..."
date: 2008-05-12
forum: Server Platforms
---

### Post by thedevnull on 2008-05-12
I have tried to run Nexuiz SERVER on Ubuntu Server 8.04 from both the Repos and the sourceforge packages to no avail.  Tried both 2.40 and 2.42.  Either way I get the same general errors that seem to be about permission issues.


Nexuiz Linux 09:18:32 Mar 23 2008
Trying to load library... "libz.so.1" - loaded.
Added packfile /usr/share/games/nexuiz/data/data20080229.pk3 (3982 files)
Added packfile /usr/share/games/nexuiz/data/music20080229.pk3 (10 files)
Trying to load library... "libcurl.so.4" - loaded.
execing quake.rc
execing default.cfg
execing physicsQBR.cfg
execing newhook.cfg
execing weapons.cfg
execing normal.cfg
Warning: Could not expand $r_showsurfaces
Warning: Could not expand $gl_finish
Warning: Could not expand $v_kicktime
couldn't exec config.cfg
couldn't exec data/campaign.cfg
couldn't exec autoexec.cfg
Shader 'textures/Reaptxt/sun' already defined
Server using port 26000
Server listening on address 0.0.0.0:26000
Loaded maps/aggressor.ent
models/weapons/g_gl.md3: could not load texture "glaunch.tga"
models/weapons/g_gl.md3: could not load texture "glaunch.tga"
models/grenademodel.md3: could not load texture "grenademodelskin.tga"
models/weapons/v_gl.md3: could not load texture "glaunch.tga"
models/weapons/v_gl.md3: could not load texture "glaunch.tga"
models/weapons/w_gl.zym: could not load texture "glaunch"
models/weapons/g_rl.md3: could not load texture "textures/rl2.tga"
models/weapons/g_rl.md3: could not load texture "textures/rl.tga"
models/weapons/g_rl.md3: could not load texture "textures/rl2.tga"
models/flash.md3: could not load texture "f_shotgun.jpg"
models/rocket.md3: could not load texture "textures/rl2.tga"
models/rocket.md3: could not load texture "textures/rl2.tga"
models/rocket.md3: could not load texture "textures/rl2.tga"
models/rocket.md3: could not load texture "textures/rl2.tga"
models/weapons/v_rl.md3: could not load texture "textures/rl2.tga"
models/weapons/v_rl.md3: could not load texture "textures/rl.tga"
models/weapons/v_rl.md3: could not load texture "textures/rl2.tga"
models/weapons/w_rl.zym: could not load texture "rl2"
models/weapons/w_rl.zym: could not load texture "rl"
models/items/a_rockets.md3: could not load texture "rocketam.tga"
models/items/a_cells.md3: could not load texture "cellammoskin.tga"
models/items/a_shells.md3: could not load texture "shellsamm.tga"
models/weapons/g_uzi.md3: could not load texture "textures/uzi.tga"
models/weapons/g_uzi.md3: could not load texture "textures/uzi.tga"
models/tracer.mdl: could not load texture "models/bulcore.tga" (frame 0) for shader "models/bulcore"
models/tracer.mdl: could not load texture "models/bultrail.tga" (frame 0) for shader "models/bultrail"
models/uziflash.md3: could not load texture "textures/muzzle2"
models/uziflash.md3: could not load texture "textures/muzzle1"
models/weapons/v_uzi.md3: could not load texture "textures/uzi.tga"
models/weapons/v_uzi.md3: could not load texture "textures/uzi.tga"
models/weapons/w_uzi.zym: could not load texture "uzi"
models/items/g_a25.md3: could not load texture "saskin.tga"
models/items/g_a25.md3: could not load texture "laskin.tga"
models/items/g_h100.md3: could not load texture "lhskin.tga"
models/items/g_h100.md3: could not load texture "50hpskin"
models/weapons/g_hagar.md3: could not load texture "hagar.tga"
models/weapons/g_hagar.md3: could not load texture "hagar.tga"
models/weapons/v_hagar.md3: could not load texture "hagar.tga"
models/weapons/v_hagar.md3: could not load texture "hagar.tga"
models/weapons/w_hagar.zym: could not load texture "hagar"
models/items/g_h25.md3: could not load texture "mhskin.tga"
models/weapons/g_nex.md3: could not load texture "nexgun.tga"
models/nexflash.md3: could not load texture "nexflash.tga"
models/weapons/v_nex.md3: could not load texture "nexgun.tga"
models/weapons/w_nex.zym: could not load texture "nexgun"
models/weapons/g_electro.md3: could not load texture "electroskin.tga"
models/weapons/g_electro.md3: could not load texture "electroskin.tga"
models/ebomb.mdl: could not load texture "models/eleccore.tga" (frame 0) for shader "models/eleccore"
models/ebomb.mdl: could not load texture "models/eleccore2.tga" (frame 1) for shader "models/eleccore"
models/ebomb.mdl: could not load texture "models/eleccore3.tga" (frame 2) for shader "models/eleccore"
models/ebomb.mdl: could not load texture "models/eleccore4.tga" (frame 3) for shader "models/eleccore"
models/ebomb.mdl: could not load texture "models/eleccore5.tga" (frame 4) for shader "models/eleccore"
models/ebomb.mdl: could not load texture "models/eleccore6.tga" (frame 5) for shader "models/eleccore"
models/ebomb.mdl: could not load texture "models/eleccore7.tga" (frame 6) for shader "models/eleccore"
models/ebomb.mdl: could not load texture "models/eleccore8.tga" (frame 7) for shader "models/eleccore"
models/ebomb.mdl: could not load texture "models/elecbeam.tga" (frame 0) for shader "models/elecbeam"
models/ebomb.mdl: could not load texture "models/elecglass.tga" (frame 0) for shader "models/elecglass"
models/weapons/v_electro.md3: could not load texture "electroskin.tga"
models/weapons/v_electro.md3: could not load texture "electroskin.tga"
models/weapons/w_electro.zym: could not load texture "electroskin"
models/domination/dom_unclaimed.md3: could not load texture "models/domination/dom_neutral.tga"
models/domination/dom_blue.md3: could not load texture "models/domination/dom_symbol2.tga"
models/domination/dom_red.md3: could not load texture "models/domination/dom_symbol.tga"
models/items/g_a1.md3: could not load texture "shard"
models/items/g_h1.md3: could not load texture "shskin.tga"
NOTE: crashed before even initializing the world, not saving persistent data
Shader 'textures/Reaptxt/sun' already defined
Loaded maps/runningman_1on1remix.ent
"fraglimit" changed to "30"
"timelimit" changed to "20"
models/laser.mdl: could not load texture "models/ltrail.tga" (frame 0) for shader "models/lasertrail"
models/laser.mdl: could not load texture "models/lcore.tga" (frame 0) for shader "models/lasercore"
models/weapons/v_laser.md3: could not load texture "laser.tga"
models/weapons/w_laser.zym: could not load texture "laser"
models/weapons/g_shotgun.md3: could not load texture "textures/shotgun.tga"
models/weapons/v_shotgun.md3: could not load texture "textures/shotgun.tga"
models/weapons/w_shotgun.zym: could not load texture "shotgun"
models/player/carni.zym: could not load texture "carni"
models/player/carni.zym: could not load texture "carniarmor"
models/player/crash.zym: could not load texture "quark"
models/player/grunt.zym: could not load texture "grunt"
models/player/headhunter.zym: could not load texture "headhunter"
models/player/insurrectionist.zym: could not load texture "insurrectionist"
models/player/jeandarc.zym: could not load texture "heroine"
models/player/lurk.zym: could not load texture "lurk"
models/player/lurk.zym: could not load texture "reptile"
models/player/lycanthrope.zym: could not load texture "lycanthrope"
models/player/marine.zym: could not load texture "marine"
models/player/nexus.zym: could not load texture "nexus"
models/player/nexus.zym: could not load texture "mulder"
models/player/nexus.zym: could not load texture "xolar"
models/player/nexus.zym: could not load texture "fbgreen"
models/player/nexus.zym: could not load texture "fbred"
models/player/nexus.zym: could not load texture "fborange"
models/player/nexus.zym: could not load texture "fbcolored"
models/player/pyria.zym: could not load texture "pyria"
models/player/shock.zym: could not load texture "shock"
models/player/skadi.zym: could not load texture "skadi"
models/player/specop.zym: could not load texture "specop"
models/player/visitant.zym: could not load texture "fricka"
models/gibs/bloodyskull.md3: could not load texture "bloodyskull.tga"
models/gibs/eye.md3: could not load texture "eye.tga"
models/gibs/eye.md3: could not load texture "eyeblood.tga"
models/gibs/gib1.md3: could not load texture "gib1.tga"
models/gibs/gib2.md3: could not load texture "textures/gib2.tga"
models/gibs/gib3.md3: could not load texture "textures/gib3.tga"
models/gibs/gib4.md3: could not load texture "textures/gib4.tga"
models/gibs/gib5.md3: could not load texture "flesh1.tga"
models/gibs/gib6.md3: could not load texture "flesh1.tga"
models/gibs/smallchest.md3: could not load texture "textures/meat.tga"
models/gibs/smallchest.md3: could not load texture "textures/meat.tga"
models/gibs/smallchest.md3: could not load texture "textures/meat.tga"
models/gibs/smallchest.md3: could not load texture "textures/meat.tga"
models/gibs/smallchest.md3: could not load texture "textures/meat.tga"
models/gibs/chest.md3: could not load texture "textures/meat.tga"
models/gibs/chest.md3: could not load texture "textures/meat.tga"
models/gibs/chest.md3: could not load texture "textures/meat.tga"
models/gibs/arm.md3: could not load texture "textures/meat.tga"
models/gibs/arm.md3: could not load texture "textures/meat.tga"
models/gibs/arm.md3: could not load texture "textures/meat.tga"
models/gibs/leg1.md3: could not load texture "textures/meat.tga"
models/gibs/leg2.md3: could not load texture "textures/meat.tga"
models/gibs/leg2.md3: could not load texture "textures/meat.tga"
models/hook.md3: could not load texture "textures/hook"
models/weapons/g_crylink.md3: could not load texture "crylink.tga"
models/plasmatrail.mdl: could not load texture "models/pcore.tga" (frame 0) for shader "models/plascore"
models/plasmatrail.mdl: could not load texture "models/ptrail.tga" (frame 0) for shader "models/plastrail"
models/weapons/v_crylink.md3: could not load texture "crylink.tga"
models/weapons/w_crylink.zym: could not load texture "crylink"
Saving persistent data...
======server ERROR in db_save:
Can't write DB to server.db

server EDICT 0:
modelindex 1.0000
absmin '-1376.0000 -1424.0000 -576.0000'
absmax ' 1664.0000 1152.0000 2440.0000'
movetype 7.0000
solid 4.0000
classname worldspawn
model maps/runningman_1on1remix.bsp
mins '-1376.0000 -1424.0000 -576.0000'
maxs ' 1664.0000 1152.0000 2440.0000'
message Running Man (1on1)
Host_Error: server: Program error in function db_save:
Can't write DB to server.db
Tip: read above for entity information

QuakeC crash report for server:
s386: STORE_F GLOBAL1, fh
s387: LT fh (= -1.0000), FALSE (= 0.0000), GLOBAL988
s388: IFNOT GLOBAL988, s394
s389: STORE_F IMMEDIATE (=Can't write DB to ), GLOBAL4
s390: STORE_F pFilename (=server.db), GLOBAL7
s391: CALL2 strcat (=strcat())
s392: STORE_F GLOBAL1, GLOBAL4
s393: CALL1 error (=error())
../common/util.qc : db_save : statement 10
g_world.qc : SV_Shutdown : statement 8
Quake Error: Host_Error: server: Program error in function db_save:
Can't write DB to server.db
Tip: read above for entity information




Anyone else seeing this?  :confused:

---

### Post by ahaslam on 2008-06-27
Have you forwarded UDP port 26000 to the correct device & allowed through iptables?

---

### Post by thedevnull on 2008-06-27
Hey Ahaslam,

Thanks for your response!  :)  This issue has been resolved.  I don't know what changed since I initially saw patches or kernel or whatever but I am not about to argue with success.  

BTW.  I did have UFW setup but its got those ports open. 

Thankfully I can go back to playing my favorite and arguably the best FOSS FPS, Nexuiz.

Have an amazing weekend!

:guitar:

---

