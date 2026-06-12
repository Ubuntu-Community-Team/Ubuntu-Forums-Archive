---
title: "gnome-alsamixer segfault"
date: 2013-04-20
forum: Ubuntu Development Version
---

### Post by monkeybrain2012 on 2013-04-20
Unable to start gnome-alsamixer. Tried to start it in the terminal and get

"** (gnome-alsamixer:28457): WARNING **: gam_toggle_get_state (). No idea what to do for mixer element "Auto-Mute Mode"!
Segmentation fault (core dumped)
"


Anyone experiencing this problem? Has a bug been filed?

---

### Post by Frogs Hair on 2013-04-20
Some users had sound problems with the latest kernel and there is a thread started. The mixer seems to work here though. ```
alsamixer 
```

---

### Post by nykobing on 2013-04-25
> **Frogs Hair said:**
> Some users had sound problems with the latest kernel and there is a thread started. The mixer seems to work here though. ```
alsamixer 
```


Do you know where this thread is? I searched and can not find it. I need gnome-alsamixer to select audio in and it is crashing. I don't have those options using regular alsamixer.

---

### Post by foop09 on 2013-05-09
I'm getting the same segfault. Running 13.04 32 bit on a macbook pro 1,2. I really need to get gnome-alsamixer running on this machine.

---

### Post by bcschmerker on 2013-05-09
The ncurses-based ALSA Mixer, /usr/bin/alsamixer (package: alsamixer) should be accessible from GNOME Terminal, KDE Konsole, or equivalent; repair technicians can even access it from the serial-terminal command line when X is down.  A segfault in alsamixer can be a clue to a driver issue.

---

### Post by monkeybrain2012 on 2013-05-09
Here is the bug report
[https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/1171011](https://bugs.launchpad.net/ubuntu/+source/gnome-alsamixer/+bug/1171011)

---

### Post by viljeml on 2013-05-09
Try QasMixer its better than gnome-alsamixer

---

### Post by nykobing on 2013-05-10
> **viljeml said:**
> Try QasMixer its better than gnome-alsamixer

Thank you. That worked for me.

---

