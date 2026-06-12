---
title: "screen size"
date: 2008-06-05
forum: Virtualisation
---

### Post by milanvora2 on 2008-06-05
Running Ubuntu 8.04 
Installed virtualbox
Installed XP guest
Installed Guest additions to change screen size:

in xorg.conf:1 have specified only 1 resolution: 1280 X 1024
Max size available in virtualbox under winodws is 1180 X1024
any idea why i can't get 1280 X 1024

---

### Post by peakshysteria on 2008-06-05
```
sudo displayconfig-gtk
```

Adjust to the right resolution and restart X (Ctrl+Alt+Backspace).

---

### Post by milanvora2 on 2008-06-05
you didn't understand the problem:
my ubuntu host is showing 1280 X 1024.
it's my windows guest that can't go beyond 1180

---

### Post by peakshysteria on 2008-06-05
Ops, was a bit fast there. Sorry man.

---

