---
title: "Steam Team Fortress 2"
date: 2011-01-06
forum: Wine
---

### Post by Azumor on 2011-01-06
Hi, does anyone know how you can get Team fortress 2 to work when I try to start it the box comes up and says "preparing for start of Team Fortress 2" and just keep loading it's the only game in steam I can't start all other that i got like CS, Left for dead 2 and half-life works anyone know how to fix it ?

on my w7 team fortress 2 wont find any servers when all other games does, so any help is appreciated.

---

### Post by ronnielsen1 on 2011-01-06
Try this and the rest of the directions on the link and see if it helps

> 
[LIST]
[*][SIZE=2]Make sure sound is configured and working (test in winecfg).                    
[/SIZE]
[*][SIZE=2]Add "-dxlevel 81" to the TF2's launch options. **This option is needed for the first run!** If not removed it will reset all TF2's video settings to DX81 defaults.                    
[/SIZE]
[*][SIZE=2]Add "-nointro" option to skip valve video. Some users report this helps to avoid initial crash.  [/SIZE]
[*][SIZE=2]Run TF2 within a Virtual Desktop if you want  consistent alt-tabbing.  This is done via winecfg -> Graphics ->  "Emulate a Virtual Desktop".  This size should be the same as your  screen resolution.                    
[/SIZE]
[*][SIZE=2]If you are using a multi-screen setup and a  Virtual Desktop you may need to enable the "Allow DirectX apps to stop  the mouse leaving their window" if the mouse is escaping in your Wine  version.                    
[/SIZE]
[*][SIZE=2]Virtual Desktops can be defined on a per-application basis.  
[/SIZE]
[/LIST]

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9901](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9901)

---

