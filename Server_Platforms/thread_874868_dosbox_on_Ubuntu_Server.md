---
title: "dosbox on Ubuntu Server"
date: 2008-07-30
forum: Server Platforms
---

### Post by samalex on 2008-07-30
Hi Everyone ...

I'd like to run several older MS-DOS apps on my Ubuntu 8.04 Server, namely a few older BBS apps, but dosbox just isn't working for me.  Before I get too far, I did get dosemu going, but it doesn't have the virtual modem capacities that dosbox has. I need something that'll truly mimic a modem with at-commands and it's my understanding dosbox does this but dosemu doesn't -- though I could be wrong.  My goal is to port various MS-DOS apps to Telnet via COM1 in dosbox.

I installed dosbox via apt-get, but when I run it, I get this:

```

$ dosbox
DOSBox version 0.72
Copyright 2002-2007 DOSBox Team, published under GNU GPL.
---

     =======================|  DirectFB 1.0.1  |=======================
          (c) 2001-2007  The DirectFB Organization (directfb.org)
          (c) 2000-2004  Convergence (integrated media) GmbH
        ------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2008-04-08 15:15)
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
Exit to error: Can't init SDL DirectFBCreate: Initialization error!

```

I've read that to create a config file you have to run CONFIG -writeconf dosbox.conf from within dosbox, but I can't even get the thing to run.

I'm doing this all through SSH, but I wouldn't think that'd matter ...  Or is X required?  Any suggestions?

Thanks,

Alex

---

### Post by PatrikMDR on 2008-12-21
Hi, I know I'm a bit late with a solution but perhaps someone else runs into the same error.

The problem here is a compiz/sdl/driver issue. 

If you disable the Visual effects (System/Preferences/Appearance) it works. My graphics card is an Intel 945GM. The driver is not the best I've seen but it's getting better.

Good luck

---

### Post by Fisslefink on 2009-07-12
Not sure if this will help, but I was getting the same "SDL" error messages trying to run Dosbox from the terminal.  I sure felt like an idiot when I looked on Gnome's "Ubuntu menu" (i.e. the start menu), under Games, and there was an icon for "Dosbox Emulator".  Clicked that and it ran just fine.  Also, hitting Alt+F2 from Gnome and running "dosbox" worked just fine.

Running from terminal still produces the errors below, presumably because it can't access the SDL graphics frameworks:

```
username@ubuntubox-intrepid-ibex:~$ dosboxDOSBox version 0.72
Copyright 2002-2007 DOSBox Team, published under GNU GPL.
---

     =======================|  DirectFB 1.0.1  |=======================
          (c) 2001-2007  The DirectFB Organization (directfb.org)
          (c) 2000-2004  Convergence (integrated media) GmbH
        ------------------------------------------------------------

(*) DirectFB/Core: Single Application Core. (2008-09-12 19:59) 
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
    --> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment variable.
(!) DirectFB/Core: Could not initialize 'system' core!
    --> Initialization error!
Exit to error: Can't init SDL DirectFBCreate: Initialization error!

```


Hope that helps

---

