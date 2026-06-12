---
title: "Netbook-Launcher is gone"
date: 2010-01-19
forum: Ubuntu Moblin Remix
---

### Post by mexlinux on 2010-01-19
Suddenly my netbook-launcher is gone:

If I run it from console, this is what I get:
(netbook-launcher:2362): GLib-WARNING **: g_set_prgname() called multiple times

(netbook-launcher:2362): GLib-WARNING **: g_set_prgname() called multiple times
(netbook-launcher:2362): libnetbook-launcher-DEBUG: CONFIG: Low graphics mode: False
(netbook-launcher:2362): libnetbook-launcher-DEBUG: CONFIG: Font dpi: 96.000000
(netbook-launcher:2362): libnetbook-launcher-DEBUG: CONFIG: Font changed: Sans 10

(netbook-launcher:2362): libnetbook-launcher-DEBUG: CONFIG: Connecting to ConsoleKit for suspend/resume restarting
(netbook-launcher:2362): liblauncher-DEBUG: launcher-menu.c:361
ORPHAN: Centro de software de Ubuntu
(netbook-launcher:2362): liblauncher-DEBUG: Workarea: (0, 25) (0, 0)
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
Fallo de segmentación



Any Ideas

---

### Post by loneowais on 2010-01-31
Same happens to me. I'm on normal Karmic Desktop. Installed the Ubuntu-Netbook-Remix package.

---

### Post by mexlinux on 2010-02-04
I found my problem.
I added gnome-shell PPA repo and some packages were updated.
I simply removed gnome-shell, downgrade all the packages from that repo, and ready, I have it back

---

### Post by rubyji on 2011-10-22
I am having this problem, too. Can anyone epxplain more simply how to fix it?

The only extra repositories I have are Dropbox, Google, and Spotify.

---

