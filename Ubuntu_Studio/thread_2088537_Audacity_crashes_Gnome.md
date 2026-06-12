---
title: "Audacity crashes Gnome"
date: 2012-11-26
forum: Ubuntu Studio
---

### Post by potiphera on 2012-11-26
Sometimes when I'm using Audacity and I perform an action (it can be pretty much anything, like deleting, zooming in, etc.), Gnome immediately crashes and restarts, returning me to the login screen.

I tried installing Audacity from the PPA, but the problem persists. Sometimes I use JACK and sometimes I don't, and the crashes occur either way. Gnome never crashes on this computer otherwise. I'm using Ubuntu Studio 10.04. Has anyone experienced this problem, or does anyone know how I can diagnose the issue and solve it? If all else fails, I'll try compiling Audacity from source, but I'd rather not go that far if there's a simpler fix. Thanks!

---

### Post by potiphera on 2012-12-17
I tried compiling from source, but the problem persists. Is there a log file somewhere that would help diagnose the issue?

---

### Post by jejeman on 2012-12-17
A guess it crashes X server.
Look in
/var/log/Xorg.0.log etc.
~/.xsession-errors

---

### Post by potiphera on 2012-12-18
Thanks for the response! There doesn't seem to be anything relevant in in those Xorg log files, just lots and lots of modelines (there was some kind of segmentation fault listed after the first time I tried to make it crash, but I didn't save that one because I wanted to replicate the crash after rebooting and only running Audacity).

When I tried rebooting and using Audacity until it crashed (I tried this twice), .xsession-errors.old lists something like this at the end of the file after the crash:

```
** (update-notifier:2013): DEBUG: Skipping reboot required
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 53653 requests (53652 known processed) with 0 events remaining.
nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gtk-window-decorator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
evolution-alarm-notify: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Audacity: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
```

Is that relevant? What does it mean?

---

### Post by jejeman on 2012-12-18
Search also tail of dmesg
```
dmesg | tail
```

---

### Post by potiphera on 2012-12-19
After a crash, dmesg | tail gives me

```
[   30.457268] CPU1 attaching sched-domain:
[   30.457270]  domain 0: span 0-3 level MC
[   30.457272]   groups: 1 2 3 0
[   30.457275] CPU2 attaching sched-domain:
[   30.457276]  domain 0: span 0-3 level MC
[   30.457278]   groups: 2 3 0 1
[   30.457281] CPU3 attaching sched-domain:
[   30.457282]  domain 0: span 0-3 level MC
[   30.457283]   groups: 3 0 1 2
[   38.853024] eth0: no IPv6 routers present
```

Also, after this last time I replicated the crash, Xorg.0.log.old has these lines at the end of the file, after all the modelines:

```
Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x45fcc8]
1: /usr/bin/X (0x400000+0x5dfbd) [0x45dfbd]
2: /lib/libpthread.so.0 (0x7ff52afa6000+0xf8f0) [0x7ff52afb58f0]
3: /lib/libdrm_radeon.so.1 (0x7ff5279f4000+0x1ef6) [0x7ff5279f5ef6]
4: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7ff527bf9000+0xc3ed9) [0x7ff527cbced9]
5: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7ff527bf9000+0xcefcc) [0x7ff527cc7fcc]
6: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7ff527bf9000+0xcf13d) [0x7ff527cc813d]
7: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x7ff527bf9000+0xbbc72) [0x7ff527cb4c72]
8: /usr/lib/xorg/modules/libexa.so (0x7ff526fac000+0x9555) [0x7ff526fb5555]
9: /usr/lib/xorg/modules/libexa.so (0x7ff526fac000+0xa0ea) [0x7ff526fb60ea]
10: /usr/lib/xorg/modules/libexa.so (0x7ff526fac000+0x74fe) [0x7ff526fb34fe]
11: /usr/bin/X (0x400000+0xd9e6b) [0x4d9e6b]
12: /usr/bin/X (0x400000+0x424f4) [0x4424f4]
13: /usr/bin/X (0x400000+0x4418c) [0x44418c]
14: /usr/bin/X (0x400000+0x261aa) [0x4261aa]
15: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7ff529c9bc4d]
16: /usr/bin/X (0x400000+0x25d59) [0x425d59]
Segmentation fault at address 0x28

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Laser Mouse: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) AIGLX: Suspending AIGLX clients for VT switch
 ddxSigGiveUp: Closing log
```

---

### Post by jejeman on 2012-12-19
Yep, X is crashing (segmenting).
I don't know, try to use different desktop theme.

---

### Post by potiphera on 2012-12-21
Changing the desktop theme didn't work, but thanks for confirming that it's crashing X. If nobody has any other ideas, I'll let this thread die and post on the Audacity forum (I'll try to remember to be a responsible citizen and post my solution here if I find one).

---

