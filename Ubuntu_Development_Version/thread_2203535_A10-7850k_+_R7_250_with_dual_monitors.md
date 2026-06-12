---
title: "A10-7850k + R7 250 with dual monitors?"
date: 2014-02-03
forum: Ubuntu Development Version
---

### Post by eks on 2014-02-03
This is a shot in the dark but... Has anyone got any change with this setup?

I can't seem to launch Ubuntu Live CD, either Trusty (14.04) or Saucy (13.10). Whenever I click Try Ubuntu it hangs and the screen flickers. The only way I could manage to do it was DISABLING the internal GPU, thus using only R7 discreet card, then the live cd would boot up completely and finish install.

But then, I switched driver to fglrx, enabled the internal GPU on the bios again, got the second monitor sort of working (it wasn't the wide desktop thing). When I rebooted after turning on Xinerama the system freezes after login. I can't neither open another terminal on CTRL+ALT+F1.

On recovery mode tried uninstalling, reconfiguring xserver, and installing fglrx 13.30 that I had downloaded previously, next boot it didn't reach the login window.

I think I'll try another round of installs tomorrow, and try to figure out how to activate  the second monitor without Xinerama.

---

### Post by Bucky Ball on 2014-02-03
Good luck. Be aware that* this sub-forum is for 14.04 reports only*. If you need help with any other release please post in the regular forum areas. 14.04 is still testing, not released until April, and if you don't want to be a tester, don't install it. Stick with a released version.

---

### Post by eks on 2014-02-04
Yes, I know this sub-forum is for 14.04, *that's the reason* I'm posting here. :)

I don't mind being a tester, I've done it in previous versions. And with this hardware it seems I don't actually have an option. :P

This is probably a video driver issue, but I could help test anything and/or provide logs if necessary.

---

