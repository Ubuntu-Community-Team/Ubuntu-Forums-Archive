---
title: "Mouse Track Pad not working in yesterday's Nightly Build!"
date: 2011-12-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kevpan815 on 2011-12-18
On my Dell Inspiron 1012 Mini Net Book PC I have a problem where my Mouse Track Pad is not working with Yesterday's Nightly Build Of Ubuntu 12.04. Sorry, but I don't know if it is Made by Dell or a Third Party.

---

### Post by kevpan815 on 2011-12-18
Nevermind, the problem straightened itself out on Second Bootup. It looks like there are some problems that occurred only on first boot, since the error message about the swap file NOT being ready yet only occurs on first boot only.

---

### Post by effenberg0x0 on 2011-12-18
Try to open a terminal and have a look at the log. Searching for mouse, touchpad, alps, synaptics, are good choices. There must be some lead.

egrep -iHn "mouse|touchpad|alps|synaptics" /var/log/dmesg

---

