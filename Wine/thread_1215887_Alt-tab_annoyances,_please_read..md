---
title: "Alt-tab annoyances, please read."
date: 2009-07-17
forum: Wine
---

### Post by shyce on 2009-07-17
Is there something that I can hack to make full-screen Wine (when alt-tab/minimized) change back to my desktop resolution?

Let me explain.

I'm playing Diablo II (1.12a) stock-install with Wine 1.1.25 (latest version afaik) on an Intel x3100 GM965 graphics chipset. 

Using ```
xrandr --output LVDS --set PANEL_FITTING full
```, I can get the game to stretch it's old 800x600 graphics across my 1280x800 laptop screen. I'd like to be able to alt-tab out of the game and have the resolution switch back to 1280x800 instead of staying @ 800x600.

Glide3 wrappers are not an options because 3d acceleration is broken on this chipset with ubuntu/intel drivers right now.

Also, is there any way I can add "Desktop" to one of the applications I can alt-tab into? I hate having two hotkeys for desktop-view and switch-application. 

Why can't ubuntu add a logic string that says "if only one application is open, then show desktop instead"? One of the few things I like about windows.

---

