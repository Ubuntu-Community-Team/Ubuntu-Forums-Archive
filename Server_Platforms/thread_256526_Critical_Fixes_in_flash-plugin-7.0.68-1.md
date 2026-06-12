---
title: "Critical Fixes in flash-plugin-7.0.68-1"
date: 2006-09-13
forum: Server Platforms
---

### Post by anodizer on 2006-09-13
flash-plugin-7.0.68-1 fixes multiple input validation errors that had the potential for execution of arbitrary code. These are CVE-2006-3311, CVE-2006-3587, and CVE-2006-3588.

How can we update in ubuntu?

---

### Post by PvSinNL on 2006-09-22
The manual way?

Download the installer from [www.macromedia.com](www.macromedia.com), unpack it, move the files **libflashplayer.so** and **flashplayer.xpt** to your plugins directory (e.g., /usr/lib/firefox/plugins if you're using Firefox) after renaming or backing up the originals, and finally change owner and group to root... (The latter steps preferably not while Firefox is running, obviously.)

(This circumvents the normal update system, but as it only concerns two files --- and no dependencies, AFAIK --- it doesn't seem to be too much of a problem. YMMV!)

---

