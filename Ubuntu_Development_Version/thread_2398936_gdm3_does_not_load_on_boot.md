---
title: "gdm3 does not load on boot"
date: 2018-08-19
forum: Ubuntu Development Version
---

### Post by Wise Ferret on 2018-08-19
Upgraded to cosmic recently. This is what I get on boot:
```
...
[  OK  ] Started GNOME Display Manager.
[  OK  ] Started Hold until boot process finishes up.
[   93.880436   ] generic_make_request: Trying to write to read-only block-device loop0 (partno 0)
[...repeated for devices loop1 to loop6...]
```
Gdm does not start.
When I switch to a different VT and login, gdm3 does not start. However, I am able to start gnome using startx.
Any ideas?

---

### Post by amano on 2018-08-20
I think that this is a known bug and already fixed upstream. The fix has yet to land in Ubuntu though.

Try switching to another VT with ALT+F4 and back with ALT+F1. Maybe that's a workaround for the problem.

---

### Post by Wise Ferret on 2018-08-20
Thank you. Moving between VTs does not help, unfortunately.
Do you happen to have a link to the bug report? This way I'll be able to contribute logs, if necessary.

---

### Post by dino99 on 2018-08-20
try cleaning the system (gtkorphan/bleachit as root but select carefully the settings), and possibly switch to a different session (x/wayland). And glance at "journalctl -b | grep gdm"

---

### Post by Wise Ferret on 2018-08-23
The problem was solved, either because of recent updates or because of using gtkorphan.

---

