---
title: "Has anyone got LOTRO to work in Karmic?"
date: 2009-11-01
forum: Wine
---

### Post by Garyu on 2009-11-01
I've got a fresh install of Karmic, installed LOTRO according to instructions on WineHQ appdb, but all I get after updating everything when the game starts is a black screen.

LOTRO has a gold rating from previous versions. I'm just surprised it refuses to work for me now. So question is, did Karmic bork it up or is it possible I missed something during install/setup?

---

### Post by Garyu on 2009-11-03
Just FYI, I finally got it to work. 

You have to download d3dx9_36.dll and put it in
~/.wine/drive_c/windows/system32/d3dx9_36.dll

After that, it works rather well. Sound dies now and then, textures are behaving weirdly sometimes, game freezes if alt-tab or other way of switching apps, etc. But it is playable.

---

