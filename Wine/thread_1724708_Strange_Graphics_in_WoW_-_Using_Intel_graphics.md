---
title: "Strange Graphics in WoW - Using Intel graphics"
date: 2011-04-08
forum: Wine
---

### Post by Murdoc419 on 2011-04-08
I have successfully got World of Warcraft to run and at first had very bad issues with my graphics but I followed a few guides and for the most part it's not bad. My FPS could be slightly higher, I'm getting around 10-15 fps outside of towns. Other than that I there are black sections on the ground underneath myself, mobs and other players. Also other player's character models are completely white minus a few pieces of gear. I will link the guides I used to set up my graphics, they are slightly old (From 9.04) but they seemed to be the best available. By the way I am running distro 10.10 and my graphics card is an Intel Express Chipset series 4. 

Guides used:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)  <-- Troubleshooting section

[http://forums.pcworld.com/index.php?/topic/65185-world-of-warcraft-intel-integrated-graphics-and-ubuntu-9-04/](http://forums.pcworld.com/index.php?/topic/65185-world-of-warcraft-intel-integrated-graphics-and-ubuntu-9-04/)

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)   <-- Linked in the above site. I followed Part B (Safe/Optimal)

If there are better steps to take to get WoW running smoothly with Ubuntu please let me know. I know it probably will never be perfect using an Intel card but I'm not sure if I can update the graphics card in my laptop.

---

### Post by cwwilson721 on 2011-04-08
> **Murdoc419 said:**
> I have successfully got World of Warcraft to run and at first had very bad issues with my graphics but I followed a few guides and for the most part it's not bad. My FPS could be slightly higher, I'm getting around 10-15 fps outside of towns. Other than that I there are black sections on the ground underneath myself, mobs and other players. Also other player's character models are completely white minus a few pieces of gear. I will link the guides I used to set up my graphics, they are slightly old (From 9.04) but they seemed to be the best available. By the way I am running distro 10.10 and my graphics card is an Intel Express Chipset series 4. 

Guides used:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)  <-- Troubleshooting section

[http://forums.pcworld.com/index.php?/topic/65185-world-of-warcraft-intel-integrated-graphics-and-ubuntu-9-04/](http://forums.pcworld.com/index.php?/topic/65185-world-of-warcraft-intel-integrated-graphics-and-ubuntu-9-04/)

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)   <-- Linked in the above site. I followed Part B (Safe/Optimal)

If there are better steps to take to get WoW running smoothly with Ubuntu please let me know. I know it probably will never be perfect using an Intel card but I'm not sure if I can update the graphics card in my laptop.

Can't do anything else. The chip and it's drivers are the issue. Intel's older chips cannot run opengl correctly. So WoW/wine is not really usable.

---

### Post by Murdoc419 on 2011-04-08
Well I am not actually running it in OpenGL but DirectX. It was much worse when I had it configured for OpenGL. Regardless I figured the problem was just the crappy hardware I have in this laptop lol. Looks like I won't be getting rid of my Windows partition :(

---

### Post by spoons on 2011-04-09
Your chipset supports the features necessary, but the graphics driver is poor and is not exposing the functionality needed to Wine.

---

### Post by cwwilson721 on 2011-04-09
> **spoons said:**
> Your chipset supports the features necessary, but the graphics driver is poor and is not exposing the functionality needed to Wine.
NO. The issue at the core is 'correct' implementation of opengl.

The chip AND the driver are the issues behind this on Intel graphics. That is why an application that works fine in Windows with D3D doesn't work as well, if at all, in Linux with opengl (D3D calls in wine are actually 'converted', for lack of a better word, to opengl calls on Linux hardware). Nvidia and Ati/AMD does this fine. Thus, many assume it's the driver that is at fault.

The Intel chip itself has it's own version of 'opengl', not the full implementation of the hardware spec. AND the driver, since it can't do 'real' opengl, lags also. It is a combination of both hardware, and software, in this case (older Intel graphics)

The newest (Sandy Bridge) Intel chips should do much better. Unfortunately, not many of these new CPUs have made it 'into the wild' yet.

---

### Post by Dlambert on 2011-04-09
Look up Ui rendering, i had a similar problem but opengl worked better for me. Maybe change the buffer to pbuffer?

---

