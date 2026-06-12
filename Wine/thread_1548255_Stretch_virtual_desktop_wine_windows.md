---
title: "Stretch virtual desktop wine windows?"
date: 2010-08-08
forum: Wine
---

### Post by elitenoobboy on 2010-08-08
Is there a way to stretch virtual desktop wine windows? So if I want to play something like starcraft, but not have the game screw with my desktop resolution or in a tiny tiny window, and just have the window double sized?

---

### Post by rizzeh on 2010-08-08
```
winecfg
```

Click graphics options tab, tick emulate desktop and select resolution you want

---

### Post by elitenoobboy on 2010-08-08
> **rizzeh said:**
> ```
winecfg
```

Click graphics options tab, tick emulate desktop and select resolution you want

That doesn't help. The game will still just play in the same size and resolution.

---

### Post by themusicalduck on 2010-08-08
If the desktop is the right size but the game isn't then you probably need to change the video settings in the game options somewhere to the right resolution.

---

### Post by elitenoobboy on 2010-08-08
> **themusicalduck said:**
> If the desktop is the right size but the game isn't then you probably need to change the video settings in the game options somewhere to the right resolution.

You can't change starcrafts resolution though.

---

### Post by themusicalduck on 2010-08-08
That's a bit annoying. As a workaround you could use Compiz zoom. If you have the desktop effects enabled, hold the windows key and then right click and drag a box over the game.

Annoying when I use this it disables mouse and keyboard input unless I hold down the windows key again and move the zoom slightly with the mousewheel, but I have two monitors and do it on the other monitor. It might only happen because I have two monitors though so you'll have to experiment a bit.

---

### Post by elitenoobboy on 2010-08-15
> **themusicalduck said:**
> That's a bit annoying. As a workaround you could use Compiz zoom. If you have the desktop effects enabled, hold the windows key and then right click and drag a box over the game.

Annoying when I use this it disables mouse and keyboard input unless I hold down the windows key again and move the zoom slightly with the mousewheel, but I have two monitors and do it on the other monitor. It might only happen because I have two monitors though so you'll have to experiment a bit.


Currently the best setup that I have found is binding a keyboard shortcut to tell compiz's enhanced desktop zoom to zoom onto the current active window, then another keypress to temporarily halt the zoom following the mouse. This still leaves the problem of scrolling within starcraft unresolved though, as I have found compiz's method of locking the mouse so that it doesn't escape the zoomed area buggy and it will still fail to bind it to just the starcraft window itself. I have found a script that uses xdotool to be able to set a custom area to bind the mouse to, but that is also imperfect.

I would like to avoid changing the monitor's resolution because it makes it a pain when trying to multitask. The ideal situation would be to have compiz be able to stretch the virtual window to match the monitor resolution, which would allow starcraft scrolling to work without a hitch.

---

