---
title: "[Problem] WoW, Ubuntu 8.10, Intel 950GMA"
date: 2008-12-26
forum: Wine
---

### Post by Espionage724 on 2008-12-26
Direct3D
- Barely any texture glitches
- Low FPS
- Low color mode (even though color is set 24)

Attempted (Direct3D)
- Adding -swtnl switch
- SET M2UseShaders "0"
- SET fixedfunction "1"
- Fullscreen and Windowed
- Toggling PixelShaders and VertexShaders in Winecfg

OpenGL
- Higher FPS
- Very glitched login screen

Attempted (OpenGL)
- Adding -swtnl switch
- SET M2UseShaders "0"
- SET fixedfunction "1"
- Fullscreen and Windowed

My question is, how can I fix OpenGL?

Screenshot (left) is OpenGL
Screenshot (right) is Direct3D

---

### Post by wimpie on 2008-12-26
I don't know if this will help you but I think you always can try:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

There are so comments below with the same problem as you .. they got as well solutions only don't know which one will work.

I can remember that I had this as well with mine BC wow but don't know how I fixed it. :S

Greetings Wimpie

---

### Post by Espionage724 on 2008-12-26
I didn't see a specific comment about my issue and I tried the solutions for problems that were close to mine and still no luck :(

---

### Post by Espionage724 on 2009-12-21
Whatever I seem to try, nothing gets this game running well. I'm even using the latest experimental intel drivers and Ubuntu 10.04 beta and there is no boost in performance.

I did the vertex object buffer fix also that is mentioned to help WoW but that leads to no avail either.

I have to run WoW with SET fixedfunction "1" in the config.wtf file which makes me suspect that there is an issue with Wine and my GL extensions, most likely the ones dealing with vertex and pixel shaders.

Any ideas?

---

### Post by hikaricore on 2009-12-21
Don't make duplicate posts: [http://ubuntuforums.org/showthread.php?p=6439904](http://ubuntuforums.org/showthread.php?p=6439904)
I'm sorry no one can help you with your terrible intel chipset, but keep wine posts in the wine forum and don't crosspost.

---

### Post by LinuxGamer on 2009-12-21
So why not bite the bullet and spend a few bucks to get a real video card? Not to be rude or anything else, just saying, if you are playing WoW, you would be better off using an Nvidia or ATI card that is meant to handle OpenGL.

---

### Post by bapoumba on 2009-12-21
Threads merged.

---

### Post by jasonditz on 2009-12-21
> **LinuxGamer said:**
> So why not bite the bullet and spend a few bucks to get a real video card? Not to be rude or anything else, just saying, if you are playing WoW, you would be better off using an Nvidia or ATI card that is meant to handle OpenGL.

It might not be an upgradable system, most of the 950's I've seen are in laptops or Micro-cases (like the MacMini). But yeah, the sad truth is the early intel GMAs don't perform very well at all in wine 3D apps.

---

### Post by LinuxGamer on 2009-12-21
You are right.. Looking at his profile it is an Acer Travelmate.. Which I can not imagine trying to play WoW on anyways.. Laptops in general do not do well for gaming.. A 1.6 Celeron with an Intel Chip set is even less likely to do well. Then when you run it in Wine on Linux to boot.. I think he is just expecting to much out of to little of a machine..

---

