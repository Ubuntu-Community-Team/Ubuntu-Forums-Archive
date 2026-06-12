---
title: "WoW WotLK Not working, crashing after startup"
date: 2008-12-31
forum: Wine
---

### Post by takumidesh on 2008-12-31
I just formatted my computer with Ibex and did a fresh install, I downloaded Wine and then went to the WoW site and did the game file recovery to install the game and both expansion packs. The installation went fine and the launcher works fine as well but when i hit play my screen freaks out. i hear the beginning video but the sound is really choppy, then everything stops and i get two errors one saying wow has crashed and another coming from Ubuntu sating the app has experianced a fatal error.
I tried running wine in windowed mode and that let's me watch the intro video with normal sounds but very choppy video and once the video is done or if i hit Esc i get the same crash

i'll post a screenshot

[IMG]http://i10.photobucket.com/albums/a121/adron999/Screenshot-2.png[/IMG]

---

### Post by takumidesh on 2008-12-31
update:

I have another screenshot of when i try to run the game

also i tried running wine in windowed mode and setting the resolution to 1440x900 the game worked fine except it only appeared in the corner of the screen, the rest of the screen was blue. I tried running the game itself in windowed mode wich worked but when i maximized the window this happened,


[IMG]http://i10.photobucket.com/albums/a121/adron999/Screenshot-4.png[/IMG]


all the controls in the game worked and i was able to hit exit game and such wihout having to kill the process, but i obviously can't play like that.

here is another screenshot in fullscreen none windowed mode

[IMG]http://i10.photobucket.com/albums/a121/adron999/sscreenie.png[/IMG]

---

### Post by Darkdelusions on 2008-12-31
Are you running wow in OpenGL or D3D mode? I seem to have the best luck running it in OpenGL

---

### Post by takumidesh on 2009-01-01
i don't know wich i'm running, i'm not at my computer right so i can't check, from the tuts i read switching to openGL only helped with framerate issues after you got the game working. As soon as i get back to my computer i will see wich one i'm using then try switching.

EDIT: I am pretty sure that I'm using D3D.

---

### Post by takumidesh on 2009-01-01
Upddate:

I changed my config.wtf to make wow run using OpenGL but that changed nothing, if i run the game in windowed mode it works but the sound is really choppy and the framerate is incredibly low.

---

### Post by takumidesh on 2009-01-02
bump ;)

---

### Post by huadiph on 2009-01-02
I had the same problem with my recent install.  Ubuntu 8.10 x64.  I fixed the sound issue by checking the Driver Emulation box under the Audio tab in Wine Config.  This article also helped me with getting logged in and playing: [https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting).

I still have a similar crash every once in awhile, especially when I'm flying around (memory access violation), but for the most part I can play ok.

---

### Post by kennster on 2009-01-02
i had a simular problem i turned down the effects but i still awalys run it in a wiwndow for some reasion wow runs best in a window for me but work in full screen good also. maby you have the frame rate to high or glow effects on..

---

### Post by EnderEcho on 2009-01-02
Post your config.wtf file so we can see your settings

What kind of graphics card do you have. Installing proprietary drivers seems to solve that second problem you have.

Thats where I'm stuck because I have an intel card and i dont know where to get the right drivers.

---

