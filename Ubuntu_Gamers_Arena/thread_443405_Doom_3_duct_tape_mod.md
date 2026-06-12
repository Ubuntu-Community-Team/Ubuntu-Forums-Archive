---
title: "Doom 3 duct tape mod"
date: 2007-05-14
forum: Ubuntu Gamers Arena
---

### Post by Nehvrook on 2007-05-14
Just wondering if anyones had any problems getting this mod to work? I've got Doom 3 installed and running fine but I want to use this mod because I'm a wuss and get scared while playing lol 

[http://doom3.filefront.com/file/Duct_Tape;29537](http://doom3.filefront.com/file/Duct_Tape;29537)

That's the mod I've put on, I'm sure I've put it on right but nothing changes in the game (Even starting a new game doesn't activate it) and it's not listed in the mods section at the main menu. Anyone have this problem/know what I'm doing wrong?

---

### Post by noerrorsfound on 2007-05-15
[http://ducttape.glenmurphy.com/](http://ducttape.glenmurphy.com/)

It works for me and all I did was follow the instructions found in the readme:
> -  INSTALLATION  --------------------------------------------



Doom 1.3 Installation Instructions:

Unpack, copy the pak008.pk4 to your /base directory, and run

Doom3. Note that if you have any save games, loading them will

make them start at the beginning of the level. If you remove

duct-tape, then they will start at whereever they were before.



Doom Resurrection of Evil Installation Instructions:

Unpack, copy pak002.pk4 to the appropriate directory (I'm not

quite sure what it is as I don't have it).
Are you sure you're putting it in the *base* folder inside of the directory where you installed Doom 3 to? It should be inside of a folder with only pk4 files and nothing other than those.

Also, make sure you are not putting it in /home/you/.doom3/base but in the actual install directory (default is */usr/local/games/doom3/base* although I install games to my home directory because there are less permission problems and I can back up my installs). Also, rename it to pak009.pk4 because pak008.pk4 is already taken by the game (perhaps it's from an update that wasn't out when he wrote the instructions).

---

### Post by Nehvrook on 2007-05-16
I've got it working now. I don't know what I did to fix it, but it's fixed lol. Only the machine gun has a flashlight though, I thought the shotgun got one too. But it's better than nothing.

---

### Post by noerrorsfound on 2007-05-17
> **Nehvrook said:**
> I've got it working now. I don't know what I did to fix it, but it's fixed lol. Only the machine gun has a flashlight though, I thought the shotgun got one too. But it's better than nothing.
The first version of the mod only added a light to the machine gun. If you downloaded it from a site other than [http://ducttape.glenmurphy.com/](http://ducttape.glenmurphy.com/) then perhaps they were hosting an older version. The changelog for version 0002 on the site says "By popular request, light added to shotgun." so if you have at least that version then it should work.

---

