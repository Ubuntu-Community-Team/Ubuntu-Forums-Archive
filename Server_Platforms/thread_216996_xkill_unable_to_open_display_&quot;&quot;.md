---
title: "xkill: unable to open display &quot;&quot;"
date: 2006-07-16
forum: Server Platforms
---

### Post by dustparticle on 2006-07-16
I'm trying to run ```
xkill
``` but I get the following error:

*xkill: unable to open display ""*

Previously I've used RH/Fedora and there typing xkill was enough. Do I need to enter a display in Ubuntu? I tried setting the display variable:

```
DISPLAY=ubuntu-srv01:0; export DISPLAY
```

Then i get the following:

*xkill:  unable to open display "ubuntu-srv01:0"*

(I also tried using the -display switch: xkill -display ubuntu-srv01:0)
(Also tried 0.0 instead of 0)

The displayname is supposed to have the following format: *hostname:displaynumber.screennumber*

I got the hostname by using the hostname command, so i know that it's correct, but what about the displaynumber.screennumber? Should that by any chanse be something other than 0 or 0.0 (I only have one monitor)? Any Ideas?

Thanks.

Edit: This only happens when logged in as root.

System:
-------------------------------
Ubuntu 6.06 Server
Ubuntu-desktop
Automatix
VMware server
Kernel: 2.6.15-26-server #1 SMP
--------------------------------

---

