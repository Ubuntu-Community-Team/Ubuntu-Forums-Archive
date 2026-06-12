---
title: "Mouse going opposite direction in a game (mystery of the mummy)"
date: 2010-05-11
forum: Wine
---

### Post by tombom62 on 2010-05-11
Honestly, I am using debian here, but this is a wine issue, not a debian issue, and I am posting here before I try the debian mailing list because I have had good experience with getting help around here.

ok so here it goes.  I am using debian sid, with squeeze and lenny repos in there as well.  I have the latest version of wine installed.  I am trying to play this game:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9055](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9055)
[http://www.frogwares.com/sherlock/index2.htm](http://www.frogwares.com/sherlock/index2.htm)
as you can see, they say it works.  I tried installing DX with winetricks like that guy.  nothing changed.


[SIZE="5"][B]
The problem:[/B][/SIZE]

everything installed fine, when I try to run it, it opens up, still fine, but there is one (big) problem -- THe mouse control is backwards!  so when I try to make it go left, it goes right, up, it goes down... another thing, it seems to squirl around the screen.  Like... it will go back to the point where it was in the middle of the screen after a few seconds of violently trying to force it to a certain side.  Sometimes, its center will change and it will be stuck somewhere else.  it is crazy.

So... has this ever happened to anyone?  in any game or program?  I don't even know what to search for.....

---

### Post by tombom62 on 2010-05-12
bump

---

### Post by Toffeeapple on 2010-05-12
Have you tried setting MouseWarpOverride to force or even disable maybe in the [registry]("http://wiki.winehq.org/UsefulRegistryKeys")?

(For some reason the title of this thread makes me giggle)
:)

---

### Post by tombom62 on 2010-05-12
> **Toffeeapple said:**
> Have you tried setting MouseWarpOverride to force or even disable maybe in the [registry]("http://wiki.winehq.org/UsefulRegistryKeys")?


have not.  gonna try that now and update when I'm done.
> (For some reason the title of this thread makes me giggle)
:)
hahaha you're right.  it is the mummy causing the mouse to mess up!
edit: mousewarpoverride isn't there in the registry.
another edit:
this is ONLY in the game.  other wine apps work just fine.

---

### Post by Toffeeapple on 2010-05-13
Just add it,

```
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\DirectInput]
"MouseWarpOverride"="Force"
```

Though who knows if it's going to maybe cause some other app to start misbehaving : )

This is why I generally put things in their own [prefix]("http://wiki.jswindle.com/index.php/WINEPREFIX") as descibed there.

Good luck with the mystery of the mummy mwahahahah ha ha ha ha ha (evil laughter fading into the background)

---

