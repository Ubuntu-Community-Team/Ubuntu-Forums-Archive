---
title: "world of warcraft"
date: 2009-05-08
forum: Wine
---

### Post by ragerty on 2009-05-08
hi,
i'm completly new to ubuntu and have just installed the jaunty version, my question is,
how do i install WOW on this OP, i have wine installed but can't seem to get anything to happen, its proberly a simple mistake on my part, but i can't figure it out.
i have xp on my internal HD, and UBUNTU JAUNTY 9.04 on my external HD.
the wine is installed and can be seen from the application tab, i also have the same problem with my rosetta stone, it's displayed on the desktop in the optical drive icon (E drive) but won't load.
i'm growing gradually displeased with windows and want to make a full transfer to ubuntu.

---

### Post by Ugluk on 2009-05-08
World of Warcraft does not require installation.

---

### Post by Torgas Prim on 2009-05-08
Follow this guide:  [http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

WoW runs great on Linux under Wine

---

### Post by Wiebelhaus on 2009-05-08
[Codeweavers]("http://www.codeweavers.com/")  For a windows like installation experience , It's not free but worth every penny and can be used for many things such as office , IE , Autocad maybe even Photoshop , I'm not sure. Either way , It's amazing software.

Cheers!

---

### Post by ragerty on 2009-06-18
Hi, still having probs with this game, if i run it from the internal hd (which was installed through xp) it crashes after about 1 minute, i still cant download from blizz, and all the advice about command lines appears to be for the game in 'cd' form not 'dvd' i cant find the 'installer.exe' file on the dvd, and when i use wine on any of the files on the dvd, it just won't do anything or says that there is no windows compatable files available.
help plzzzzzzzzzzzz

---

### Post by perceptus on 2009-06-18
I am unsure with Ubuntu, but with other distro's I have notices WoW has some serious on linux when using certain ATI cards.

---

### Post by BinaryFeast on 2009-06-18
> **ragerty said:**
> Hi, still having probs with this game, if i run it from the internal hd (which was installed through xp) it crashes after about 1 minute, i still cant download from blizz, and all the advice about command lines appears to be for the game in 'cd' form not 'dvd' i cant find the 'installer.exe' file on the dvd, and when i use wine on any of the files on the dvd, it just won't do anything or says that there is no windows compatable files available.
help plzzzzzzzzzzzz

 When you try to launch the game from your XP-partition, do you get any error messages? What commands do you use? I can play WoW just fine by typing: ```
wine /host/Users/Public/Games/"World of Warcraft"/Wow.exe -opengl
``` Modify the path according to where your wow.exe file is stored and try typing it in a terminal. See if any error messages roll by.

---

### Post by Mauler5858 on 2009-06-18
Personally id reccomend copying the whole wow direcory from its default location to:

/home/*username*/.wine/drive_c/Program Files

Then apply the tweaks to it from that location.  Also are you running it in OpenGL mode or DirectX mode?

OpenGL is much more stable for WOW on wine.

---

### Post by ragerty on 2009-06-18
Gosh! so many replies, I'll run through them one by one in the appropriate order till i get a stable game play. ty dudes/dudettes, you've made me one happy ragerty  ]:-)

---

### Post by geirha on 2009-06-18
Some more tweaks that may help here:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by ragerty on 2009-06-24
to everyone who's helped, a very big ty, the game is now up and running whoo-hoo!
i'm starting to get the hang of ubuntu, so when win7 comes out and i lose support for xp, i feel confident enough to make a full switch over to ubuntu. thanks again chaps and chapettes   ]:-)

---

