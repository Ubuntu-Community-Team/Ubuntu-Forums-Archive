---
title: "Rift running low FPS in ubuntu 11.04"
date: 2011-04-29
forum: Wine
---

### Post by Zonen on 2011-04-29
I installed ubuntu 11.04 and wine 1.3 with most current nvidia drivers for my gtx 460 and then installed rift.  I configured Direct3D and opengl to get the full potential of my gaming experience yet I am seeing a significant drop in FPS on ubuntu vs Windows 7.  I am wondering if anyone else has rectified this FPS issue in Rift or any other game that might help me.  I have to drop the game graphics down to low and still am only getting around 15-18 fps and it has a reasonable amount of video lag vs windows were it runs smooth.  Thanks for the help in advance.

---

### Post by Zonen on 2011-04-29
also if you have any recommendations on another distro that will provide a better gaming experience and improved FPS please let me know.

---

### Post by Kenjitamura on 2011-04-29
The reason that Windows 7 games so much better than Ubuntu is because Rift is programmed in Directx9.  DirectX is windows exclusive, what wine is doing is it is translating all the directx commands to opengl.  Converting every call from directx to the opengl equivalent effectually halves your FPS in games.  If Rift becomes popular enough that it's ported to Mac meaning it'll use OpenGL like WoW can then my wager would be running in OpenGL mode on ubuntu you'd be getting better performance than in Windows 7.  Until then if you want to game in Rift on Ubuntu you have to take the performance hit.

Here are some registry tweaks for Wine which may improve FPS open regedit and in HKEY_CURRENT_USER\Software\Wine create a new key and call it Direct3D.

In the new directory add the following string values with the following values: String Value/value

> DirectDrawRenderer/opengl
Multisampling/disabled
OffScreenRenderingMode/pbuffer
UseGLSL/disabled
VertexShaderMode/hardware

If you type lspci -n in the terminal and scroll down to the entry 0300 in the second column you can further optimize the registry. 

My lspci -n puts out 
> 01:00.0 0300: 1002:9498
with that information I can add in the same place I put the other values 

values:String value/value
> VideoPciVendorID/0x1002
VideoPciDeviceID/0x9498

For me 0x1002 indicates the vendor is ATI and 0x9498 tells the registry my card is a Radeon HD 4650.

A 4650 is considerably weaker than a gtx 460 but in 10.10 in Meridian I get an FPS of 15 and everywhere else 30 on low settings.  I'm going to be upgrading to a 5770 which should allow me to double to triple my FPS.

---

### Post by brian70809 on 2011-04-30
The biggest jump you can get is by Turning off the Project Textures..  You will double your fps a lot of the time.

I have MED settings with Projected turned off and I'm at 20-30 fps in Meridian and roaming around.  

My system is a Quad Core Q6600, 8Gig ram, Nvidia GTX260.. on Ubuntu 11.04 64x...

---

### Post by jnthornh on 2011-05-19
> **brian70809 said:**
> The biggest jump you can get is by Turning off the Project Textures..  You will double your fps a lot of the time.

I have MED settings with Projected turned off and I'm at 20-30 fps in Meridian and roaming around.  

My system is a Quad Core Q6600, 8Gig ram, Nvidia GTX260.. on Ubuntu 11.04 64x...


Hey Brian, did you change anything else within wine? I have a system which has nearly identical specs as yours (Q6600, 8GB, GTX460) and with the settings you mention I get about 12 FPS in Meridian.

---

### Post by nixIT on 2011-05-30
are you guys running in 32bit or 64bit Ubuntu?

---

### Post by brian70809 on 2011-06-03
Well.. i have an update..  My FPS did drop on that q6600 with gt260 as Rift started to fill up with players...

I ended up building a new system for work related reasons.. and here is what I get now.

I bounce from 30-55fps in game.. Meridian jumps around a lot. from 9fps to 30+, but generally stays at 27 if I'm moving around.  I am not sure what causes this.

My system now is a i5-2500, Nvidia GTX 460, 8gigs Ram, and Ubuntu 11.04 64bit.

Settings:

Terrain Dist-4
Object Dist -125
Object Det - 50
AF - 2
Shadow Map Res - 1
Text Quality -3
Ground Cluster Density 3
Ground Clutter Radius 100
Shader Complexity - 6
Lighting Quality - 8
Particle Quantity - 250
Spell Detail - 3

In the boxes below. only one checked is Enable Detail Objects.. and shadows is Environment Only..
AA is none.

An improved CPU and GPU have almost doubled my fps average.

---

### Post by nixIT on 2011-06-07
I will give your settings a shot.  

I know on my windows partition, I can max everything out, and RIFT looks gorgeous, but in Linux (64bit), I have it set to medium with other options turned off and it's playable.

-nixIT

---

### Post by StevenWR on 2011-06-09
> **nixIT said:**
> I will give your settings a shot.  

I know on my windows partition, I can max everything out, and RIFT looks gorgeous, but in Linux (64bit), I have it set to medium with other options turned off and it's playable.

-nixIT


You guys running Nvidia card are the lucky ones ive already proven the games like the combo of Intel dual core t5700 and Nvidia450 the fps is 2 times what i can get with amd x2 3000 and radeon 6670 really dissapoints me but i have no intentions on makeing my back up machine my main one. Just mess around with the registry tweaks open terminal and here is a link for all the registry tweeks you can add in the d3d folder it does help [http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys). .... your not gonna get alot of fps but it can be improved.

---

### Post by Sunfist on 2011-06-12
I tried running Rift using Crossover Games and still took a huge fps hit, from 30-35 down to 10-12. It was still playable but barely. As I have a dual-boot system I decided to just stick to Win7 for Rift, rather than rebuild my computer. It would be nice if they added graphics support for OpenGL but I am not optimistic.

---

### Post by brian70809 on 2011-06-13
That's about right on your frame rate drop..  I can run full mode in Windows 7 with all graphics options max with a FPS of around 55-60.   I drop to around 12-15 fps in Crossover with same settings..

That's why I posted my settings for the higher FPS..  The game still looks great, but not as great as native windows..

The DirectX conversion to OpenGL in Linux is just too much of a bottleneck.

---

### Post by desktorp on 2011-06-13
I always just try to remind myself that DirectX9 has not been 100%  reverse engineered by Wine devs.  I think to describe it as a bottleneck  is a bit inaccurate, because rather than spewing out  too much work for your system to handle, there is probably just some  error(s) happening in the background, which the system can't resolve on its own.  The right fix could suddenly make  a world of difference, so be sure to rally together when you find even one person that shares your woes.  A bug report by more than one user has that much more chance of being noticed and resolved.

Has anyone tried running this game from the terminal to get some output?

---

