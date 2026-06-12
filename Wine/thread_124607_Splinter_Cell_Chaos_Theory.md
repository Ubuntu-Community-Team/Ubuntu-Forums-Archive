---
title: "Splinter Cell Chaos Theory"
date: 2006-02-01
forum: Wine
---

### Post by Tichondrius on 2006-02-01
Did anyone get this game to work using cedega or wine ?  Or did anyone try and fail ? This is a great game.

---

### Post by Sutekh on 2006-02-01
Two good sites here for checking compatability;

[Wine Application Database]("http://appdb.winehq.org/")

[Transgaming (Cedega) Gaming Database]("http://transgaming.org/gamesdb/index.mhtml")


[Transgaming - Splinter Cell Chaos Theory]("http://transgaming.org/gamesdb/games/view.mhtml?game_id=3733")
The Transgaming Forums might be a good place to ask for success stories.

---

### Post by leech on 2006-02-02
This game is highly unlikely to work in linux unless a native port is made.  It uses Starforce as copy protection, which doesn't even work on some Windows sytems.

Leech

---

### Post by davidkonsumer on 2009-02-06
I got it to install and run on intrepid.

```
wineconfig
```

[LIST]
[*]emulate virtual desktop 1024x768
[*]vertex shader support: hardware
[*]allow pixel shader
[*]set up and test an audio driver
[/LIST]

```
wine regedit
```
[LIST]
[*]new key HKEY_CURRENT_USER\Software\Wine\Direct3D
[*]new string value OffscreenRenderingMode=fbo
[/LIST]

---

### Post by Jack Brear on 2009-06-07
sorry, can you translate into newbie language please...

---

### Post by Dark Aspect on 2009-06-07
I have heard of this game running on wine as well as seen it before, however in my own attempts I could not get past Starforce. Cracks were unsuccessful and as leech said, Starforce doesn't run on wine. If you can find a way to get around Starforce than it would probably work.

---

