---
title: "What does this mean?"
date: 2009-10-16
forum: Wine
---

### Post by kraoZ on 2009-10-16
The game I'm trying to play just gives me this error.

```

fixme:service:QueryServiceObjectSecurity 0x1526a8 4 0x152998 0 0x32eed0 - semi-stub
fixme:service:QueryServiceObjectSecurity 0x1526a8 4 0x152998 28 0x32eed0 - semi-stub
fixme:advapi:SetEntriesInAclA 1 0x32ee60 0x1529ac 0x32eecc
fixme:service:SetServiceObjectSecurity 0x1526a8 4 0x32ee4c
fixme:win:EnumDisplayDevicesW ((null),0,0x32f414,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface

```

A little help? :3

---

### Post by mocoloco on 2009-10-16
Need more info.  Lots more.  What game?  What are your system specs?   Looks like it's an MS Windows® game you're running under wine.  Just need more info to be able to help.

---

### Post by beastrace91 on 2009-10-16
Mind filling in a few blanks for us? What game, what Wine version, what graphics card, and what driver version?

~Jeff

---

### Post by kraoZ on 2009-10-16
Card~5900 ZT/Driver~173.14.20/WINE~1.1.31

---

### Post by aoanla on 2009-10-16
Well, you still haven't told us what game it is. This makes it a little hard to debug, given that the terminal output you *have* got is common to a lot of games in Wine that do work.

---

