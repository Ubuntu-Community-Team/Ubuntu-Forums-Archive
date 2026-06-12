---
title: "WoW crashes in D3D mode"
date: 2009-01-15
forum: Wine
---

### Post by ramboza on 2009-01-15
Hello,

When i had 8.04 everything was ok and WoW was playable both opengl and d3d modes.

Now i've installed 8.10 and wow crashes with "memory could not be read" if launching wow.exe without "-opengl" key.

Well, frankly, it's not a problem for me, because opengl mode is still playable, so i'm just curious why this happends.

Can't bring exact wine output right now, but it look like smth:

...error...render glsl shader...must be version 120


I'll update the output when i'm back home from work.

---

### Post by ramboza on 2009-01-15
Found some info at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

Vertex shaders work fine on NVidia hardware, just not in D3D. ;)
This is probably due to the fact that the DX9c conversion calls aren't yet complete. And since OpenGL can already run the vertex shaders fine, there's no real hurry to implement the same functionality in D3D.

Open winecfg -> Graphics -> Direct3D -> Vertex Shader Support.
Change from Hardware to None. Now you can run Wow in D3D mode.


So, solved :p

---

### Post by Juggercat on 2009-01-29
Its a problem with the compiz...

Go to system -> Preferences -> Apearance -> Visual Effects 

Select None.

That solves it :D

cheers!

---

