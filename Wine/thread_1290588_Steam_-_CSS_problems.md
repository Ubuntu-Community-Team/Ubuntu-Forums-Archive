---
title: "Steam - CSS problems"
date: 2009-10-13
forum: Wine
---

### Post by ashatron on 2009-10-13
Hi all.

Im trying to install Counter Strike Source (another step in making the switch to ubuntu fully!)

Ive installed steam through wine, no probs.
But when i run css, it opens, allows me to choose a server then when i join a server to play it either
Plays very badly approx 40 fps (i got 200 in xp), but sometimes goes up to 100 - but still looks very jerky! - dont know why though.
Or
Crashes instantly

I also cannot change my screen resolution and my mouse cursor disappears if i am not over a clickable menu button.

HELP PLEASE!! :grin:

Ive yet to try PlayOnLinux.

---

### Post by beastrace91 on 2009-10-13
Did you read the rest of the response I posted [here](http://ubuntuforums.org/showthread.php?t=1290236)? Can you provide the information I asked for there?

~Jeff

---

### Post by ashatron on 2009-10-14
> **beastrace91 said:**
> Did you read the rest of the response I posted [here]("http://ubuntuforums.org/showthread.php?t=1290236")? Can you provide the information I asked for there?

~Jeff
I did read, thanks a lot mate!

I tried dxlevel 81 - but it had no effect.

Im using Wine version 1.1.15 - it appeared to be the more successful wine version for 8.10 ubuntu.

[B]Set up - Core Duo t2700 @ 2.33Ghz (32bit) - 3gigs DDR2
gfx card - NVIDIA GeForce Go 7900 GTX 
Intrepid 8.10

GFX driver - Nvidia accelerated graphics driver (version 180)[/B]

Hope that helps. 
Thanks jeff :)

---

### Post by beastrace91 on 2009-10-14
I haven't used Ibex for awhile but I know on Jaunty my CSS run 100% "right out of the box" on Wine version .27-.29 (I have yet to try .30 and .31 as I heard they contained regressions and I don't have time/effort to deal with that atm hehe) To get better performance I would also recommend the following:

Upgrade your Wine version to one of the ones I listed above - typically new versions have better support and regressions, while they happen, aren't terribly common and you can always revert back to a previous version if a new one works poorly.

Upgrade your driver version - on Linux if you want to game it is important to keep up with the latest nVidia driver release - each one typically improve performance by a bit (I use the 190.xx beta drivers currently with out issue but the latest "stable" drivers are 185.xx.xx - upgrade to at least these)

Search the net for a "CSS fps optimization" there are a number of .cfg files out there with tweaks that will increase your performance. (I am at work currently but when I get home late tonight I can post the one I use if you would like)

Regards,
~Jeff

---

### Post by Sticky_Bit on 2009-10-14
I just installed Ubuntu 9.04, Wine, Steam and CSS and it worked out of the box. First installed all Ubuntu updates, installed the native Nvidia driver 1.80 (7900 GT), installed Wine from Ubuntu's add/rem application. Its an earlier verison than 1.1.15.

 I had to fuss with my sound a little. I installed steam from an .exe on my XP drive (dual booting) and it installed no problem with Wine, then installed CSS and good to go.

---

### Post by beastrace91 on 2009-10-14
I'd still recommend upgrading to a newer nVidia driver, you will see an FPS increase. Check the link in my sig for other performance tip increases for games.

~Jeff

---

### Post by ashatron on 2009-10-15
Thanks all :D
> **beastrace91 said:**
> I haven't used Ibex for awhile but I know on Jaunty my CSS run 100% "right out of the box" on Wine version .27-.29 (I have yet to try .30 and .31 as I heard they contained regressions and I don't have time/effort to deal with that atm hehe) To get better performance I would also recommend the following:

Upgrade your Wine version to one of the ones I listed above - typically new versions have better support and regressions, while they happen, aren't terribly common and you can always revert back to a previous version if a new one works poorly.

Upgrade your driver version - on Linux if you want to game it is important to keep up with the latest nVidia driver release - each one typically improve performance by a bit (I use the 190.xx beta drivers currently with out issue but the latest "stable" drivers are 185.xx.xx - upgrade to at least these)

Search the net for a "CSS fps optimization" there are a number of .cfg files out there with tweaks that will increase your performance. (I am at work currently but when I get home late tonight I can post the one I use if you would like)

Regards,
~Jeff
Wiked mate, will give them pointers a shot.

Yeah posting your cfg would be great!
Cheers :)

---

### Post by ashatron on 2009-10-15
ive downloaded the latest nvidia drivers i could find 
which were version 185. 

Its a .Run file though. How do i install this?

Also where did you get version 190 beta?

---

### Post by beastrace91 on 2009-10-15
You can always find an archive of all the nVidia drivers that are up for download at their [ftp site](ftp://download.nvidia.com/XFree86/)

As for installing from the .run package always remember help.ubuntu.com is one of your best friends :)

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

And drat! I forgot to post my .cfg file when I got home last night - will try to remember to do so this evening.

~Jeff

---

### Post by beastrace91 on 2009-10-17
Sorry about the long delay - it kept slipping my mind - here is the custom .cfg file I use to get extra FPS in CSS (I also add the -dxlevel 81 command to the launcher options)

```
r_decals 0
mp_decals 0

net_graph 0
cl_showfps 1
cl_interp 0.01

cl_radartype 1
cl_show_bloodspray 0
cl_ejectbrass 0
cl_scalecrosshair 1
cl_ejectbrass 0
cl_show_splashes 0
cl_show_bloodspray 0

r_3dsky 0
r_shadows 0
r_eyes 0
r_teeth 0
r_drawrain 0
r_dynamic 0
r_modellodscale 0.1
r_drawlights 0
r_DispUseStaticMeshes 0

fog_enable 0
muzzleflash_light 0

```

Hopefully that helps some.

~Jeff

---

