---
title: "Team Fortress 2 - Set to directX 8 and can't set it back"
date: 2010-08-07
forum: Wine
---

### Post by Vunutus on 2010-08-07
Contrary to what the appDB says, it runs on directX 9 completely perfectly for me as far as I can tell. Max settings and everything looks great and runs smooth.

I noticed a little while back that I would seem to get some network lag in game where players would be stuttery as they walked occasionally even if it said I had very good ping. Now I know this wasn't video lag since the whole game was smooth, just not the players. I thought maybe directX had something to do with the networking so I figured I'd give directX 8 a spin like the appDB says. I added -dxlevel 85 to my launch parameters and it pretty much wrecked everything. My FPS sags pretty much all the time even with not much going on in game. I exited the game and removed -dxlevel 85 from my launch parameter area but it didn't unset it. When I go to advanced video options it shows "hardware directX level" in a greyed out box as DX8. Software directX is showing 9, though. I tried setting -dxlevel 9 too, again to no avail apparently.

How do I fix my game? I just want it playable again :X

---

### Post by JustinR on 2010-08-07
> **Vunutus said:**
> Contrary to what the appDB says, it runs on directX 9 completely perfectly for me as far as I can tell. Max settings and everything looks great and runs smooth.

I noticed a little while back that I would seem to get some network lag in game where players would be stuttery as they walked occasionally even if it said I had very good ping. Now I know this wasn't video lag since the whole game was smooth, just not the players. I thought maybe directX had something to do with the networking so I figured I'd give directX 8 a spin like the appDB says. I added -dxlevel 85 to my launch parameters and it pretty much wrecked everything. My FPS sags pretty much all the time even with not much going on in game. I exited the game and removed -dxlevel 85 from my launch parameter area but it didn't unset it. When I go to advanced video options it shows "hardware directX level" in a greyed out box as DX8. Software directX is showing 9, though. I tried setting -dxlevel 9 too, again to no avail apparently.

How do I fix my game? I just want it playable again :X

Hi,

Do you have WineTricks installed? If not search Google and install it.

I believe it offers the ability to change DirectX versions.

---

### Post by 8Kuula on 2010-08-08
-dxlevel 90 != -dxlevel 9

---

### Post by Vunutus on 2010-08-13
> **8Kuula said:**
> -dxlevel 90 != -dxlevel 9

This worked, thanks!

---

