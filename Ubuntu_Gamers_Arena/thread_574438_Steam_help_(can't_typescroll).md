---
title: "Steam help (can't type/scroll)"
date: 2007-10-12
forum: Ubuntu Gamers Arena
---

### Post by Vadi on 2007-10-12
I can't seem to be able to scroll at all in the steam window. I tried using the up down, tab, page up/down buttons, -nothing- works. Also, I can't seem to be able to type in the search bar, at all. I tried pasting into it, didn't work either.

Anything have a solution? All I want is Counter-Strike Source to work.

---

### Post by gsiliceo on 2007-10-12
Do you have, beryl/compiz/compizfusion installed?

---

### Post by Vadi on 2007-10-12
Yep.

Let me try without it.

---

### Post by Vadi on 2007-10-12
Tried, same thing.

I can't seem to be able to buy any game either, it tells me 'Attempt to write to virtual adress 36 without appropriate access rights.' More googleing...

---

### Post by cogadh on 2007-10-13
Do you have the Gecko engine installed in Wine? Steam won't really work correctly without it.

EDIT - Almost forgot, what version of Wine are you using?

---

### Post by Vadi on 2007-10-14
Well, I presume yes, because when I was following some instructions to install gecko in wine, all it did was open a wine window pointing to their site.

My wine version is wine-0.9.46.

---

### Post by cogadh on 2007-10-14
It should have come up with a Gecko install dialog, then after the install was complete, the Wine site should have displayed. If that is what happened, then Gecko is installed. You can test it to confirm by running this in the terminal:
```
wine iexplore http://www.winehq.org
```

Are you using a Wine virtual desktop window when running Steam, or is it running in "full screen"? Also, what other settings are you using on the Graphics tab in winecfg?

---

### Post by Vadi on 2007-10-14
Yeah, so I do have gecko.

I'm not using wine's desktop window, steam is displayed just like other windows.

I attached a screenshot of winecfg :)

---

### Post by Lord C on 2007-10-20
For me, Steam runs fine, I just can't see any text on any Steam window. I have to know what I'm clicking.

Just tested, I can get into CS fine, nice fps over 100. The graphics don't look very good, but I suppose that could be tweaked, maybe.

I wonder why Steam won't run with Cedega anymore, if it runs fine with default Wine.

---

### Post by Vadi on 2007-10-20
Eh, I tried buying the game via paypal but apparently there are some issues and regressions, so I gave up for now. I'm quite happy with Open Arena :D

---

### Post by cogadh on 2007-10-20
> **Lord C said:**
> For me, Steam runs fine, I just can't see any text on any Steam window. I have to know what I'm clicking.

Just tested, I can get into CS fine, nice fps over 100. The graphics don't look very good, but I suppose that could be tweaked, maybe.

I wonder why Steam won't run with Cedega anymore, if it runs fine with default Wine.
The text problem usually indicates that you don't have the Tahoma font in Wine. Copy it from a Windows machine (or search for it online, you might be able to download it) and put it in the .wine/drive_c/windows/fonts folder.

Cedega seems to have a problem with the new Steam Community features that were recently added. I don't know if anyone has found a workaround for it yet.

---

### Post by Vadi on 2007-10-20
I do remember having it, but I'll try getting steam again (didn't do it yet on gutsy).

---

