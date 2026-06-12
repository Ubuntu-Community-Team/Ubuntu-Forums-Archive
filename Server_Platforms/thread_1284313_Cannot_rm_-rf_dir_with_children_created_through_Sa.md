---
title: "Cannot rm -rf dir with children created through Samba"
date: 2009-10-06
forum: Server Platforms
---

### Post by Angel of Death on 2009-10-06
I have several folders that display with a green background (which I cannot find a definition for) that refuse to rm -rf. Every folder is empty with exception of the child folder below it. I understand that this is potentially a permissions problem but I've tried everything I can think of/Google and I'm stuck.

I've removed the share from smb.conf.
I've killed Samba
I've chmodded all folders recursively to 777
I've chowned everything to $USER:USER
I've even tried to shutdown -Fr now (which from what I've read is supposed to run a filesystem check, but cannot confirm actually did anything)

Any help would be appreciated.

I've attached a screen shot of the mysterious colored folders. Thanks!

```

mdk@ubuntu:~/srcds_l/synergy$ rm -rf orangebox
rm: cannot remove directory `orangebox/synergy': Directory not empty
rm: cannot remove directory `orangebox/episodic/sound/npc/dog': Directory not empty
rm: cannot remove directory `orangebox/episodic/sound/npc/advisor': Directory not empty
rm: cannot remove directory `orangebox/episodic/sound/commentary': Directory not empty
rm: cannot remove directory `orangebox/episodic/sound/ambient/outro': Directory not empty
rm: cannot remove directory `orangebox/episodic/sound/ambient/levels/citadel': Directory not empty
rm: cannot remove directory `orangebox/episodic/sound/ambient/levels/city': Directory not empty
rm: cannot remove directory `orangebox/episodic/sound/ambient/levels/intro': Directory not empty
rm: cannot remove directory `orangebox/episodic/sound/ambient/intro': Directory not empty
rm: cannot remove directory `orangebox/episodic/sound/vo/episode_1/c17': Directory not empty
rm: cannot remove directory `orangebox/episodic/sound/music': Directory not empty
rm: cannot remove directory `orangebox/episodic/scripts/talker': Directory not empty
rm: cannot remove directory `orangebox/episodic/models/props_interiors': Directory not empty
rm: cannot remove directory `orangebox/episodic/models/props_combine': Directory not empty
rm: cannot remove directory `orangebox/episodic/models/weapons': Directory not empty
rm: cannot remove directory `orangebox/episodic/models/props_debris': Directory not empty
rm: cannot remove directory `orangebox/episodic/models/props_lab': Directory not empty
rm: cannot remove directory `orangebox/episodic/resource': Directory not empty
rm: cannot remove directory `orangebox/episodic/materials/props': Directory not empty
rm: cannot remove directory `orangebox/episodic/materials/decals': Directory not empty
rm: cannot remove directory `orangebox/episodic/materials/models/props_interiors': Directory not empty
rm: cannot remove directory `orangebox/episodic/materials/models/props_combine': Directory not empty
rm: cannot remove directory `orangebox/episodic/materials/models/weapons/v_shotgun': Directory not empty
rm: cannot remove directory `orangebox/episodic/materials/models/props_pipes': Directory not empty
rm: cannot remove directory `orangebox/episodic/materials/models/props_lab': Directory not empty
rm: cannot remove directory `orangebox/episodic/materials/models/props_junk': Directory not empty
rm: cannot remove directory `orangebox/hl2/shaders/psh': Directory not empty
rm: cannot remove directory `orangebox/hl2/shaders/fxc': Directory not empty
rm: cannot remove directory `orangebox/hl2/shaders/vsh': Directory not empty
rm: cannot remove directory `orangebox/hl2/expressions': Directory not empty
rm: cannot remove directory `orangebox/hl2/sound/player': Directory not empty
rm: cannot remove directory `orangebox/hl2/sound/npc/metropolice/vo': Directory not empty
rm: cannot remove directory `orangebox/hl2/sound/npc/overwatch/radiovoice': Directory not empty
rm: cannot remove directory `orangebox/hl2/sound/npc/combine_soldier/vo': Directory not empty
rm: cannot remove directory `orangebox/hl2/sound/physics/wood': Directory not empty
rm: cannot remove directory `orangebox/hl2/sound/combined/trainyard': Directory not empty
rm: cannot remove directory `orangebox/hl2/sound/weapons/fx/nearmiss': Directory not empty
rm: cannot remove directory `orangebox/hl2/sound/ambient/atmosphere': Directory not empty
rm: cannot remove directory `orangebox/hl2/sound/ambient/levels/citadel': Directory not empty
rm: cannot remove directory `orangebox/hl2/sound/vehicles': Directory not empty
rm: cannot remove directory `orangebox/hl2/sound/vo/npc': Directory not empty
rm: cannot remove directory `orangebox/hl2/sound/vo/batch converters': Directory not empty
rm: cannot remove directory `orangebox/hl2/sound/music/stingers': Directory not empty
rm: cannot remove directory `orangebox/hl2/sound/common': Directory not empty
rm: cannot remove directory `orangebox/hl2/scripts': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/props_interiors': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/props_citizen_tech': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/props_doors': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/props_buildings': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/props_building_details': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/props_combine': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/props_c17': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/props_canal': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/props_wasteland': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/props_animated_breakable': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/vehicles': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/props_debris': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/props_pipes': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/props_lab': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/props_junk': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/props_trainstation': Directory not empty
rm: cannot remove directory `orangebox/hl2/models/props_rooftop': Directory not empty
rm: cannot remove directory `orangebox/hl2/cfg': Directory not empty
rm: cannot remove directory `orangebox/hl2/resource': Directory not empty
rm: cannot remove directory `orangebox/hl2/materials/particle/old': Directory not empty
rm: cannot remove directory `orangebox/hl2/materials/particle/smoke1': Directory not empty
rm: cannot remove directory `orangebox/hl2/materials/shadertest': Directory not empty
rm: cannot remove directory `orangebox/hl2/materials/skybox': Directory not empty
rm: cannot remove directory `orangebox/hl2/particles': Directory not empty
rm: cannot remove directory `orangebox/ep2/sound/npc/ministrider': Directory not empty
rm: cannot remove directory `orangebox/ep2/sound/npc/vort': Directory not empty
rm: cannot remove directory `orangebox/ep2/sound/npc/fast_zombie': Directory not empty
rm: cannot remove directory `orangebox/ep2/sound/weapons/strider_buster': Directory not empty
rm: cannot remove directory `orangebox/ep2/sound/ambient/levels/caves': Directory not empty
rm: cannot remove directory `orangebox/ep2/sound/ambient/levels/outland': Directory not empty
rm: cannot remove directory `orangebox/ep2/sound/ambient/levels/gman': Directory not empty
rm: cannot remove directory `orangebox/ep2/sound/ambient/levels/launch': Directory not empty
rm: cannot remove directory `orangebox/ep2/sound/ambient/energy': Directory not empty
rm: cannot remove directory `orangebox/ep2/sound/ambient/ambience': Directory not empty
rm: cannot remove directory `orangebox/ep2/sound/vehicles/junker': Directory not empty
rm: cannot remove directory `orangebox/ep2/sound/vo/outland_11a/silo': Directory not empty
rm: cannot remove directory `orangebox/ep2/sound/vo/outland_01/intro': Directory not empty
rm: cannot remove directory `orangebox/ep2/sound/foley': Directory not empty
rm: cannot remove directory `orangebox/ep2/sound/music': Directory not empty
rm: cannot remove directory `orangebox/ep2/scripts/talker': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/props_interiors': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/map12_building2': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/props_citizen_tech': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/map12a_hangar': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/map12_sawmill': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/props_mining': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/props_foliage': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/map1_rubble': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/props_combine': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/map10_doors': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/props_forest': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/props_c17': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/weapons': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/props_hive': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/skeleton': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/props_silo': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/map1_bridge': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/props_junk': Directory not empty
rm: cannot remove directory `orangebox/ep2/models/props_trainstation': Directory not empty
rm: cannot remove directory `orangebox/ep2/resource': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/map12_building2': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/map12a_hangar': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/antlion_grub': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/map12_sawmill': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/props_mining': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/props_foliage': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/rockslide': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/map10_doors': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/combine_strider': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/props_forest': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/props_c17': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/props_wasteland': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/antlion_guard': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/props_hive': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/ep2_out12_hut1': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/props_silo': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/rendering_regression_test/ministrider': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/vortigaunt': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/models/props_trainstation': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/particle': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/effects': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/nature': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/overlays': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/vgui/resource': Directory not empty
rm: cannot remove directory `orangebox/ep2/materials/vgui/screens': Directory not empty
rm: cannot remove directory `orangebox/ep2/particles': Directory not empty

```

---

### Post by Angel of Death on 2009-10-06
Figured it out.

Basically, I'm using the parent folder as a virtual file system and the mount was 'stuck'. 'Stuck' is the best way I can put it, it wasn't originally showing up in the mount list and only after removing it from fstab and restarting was I able to rm the directories.

---

