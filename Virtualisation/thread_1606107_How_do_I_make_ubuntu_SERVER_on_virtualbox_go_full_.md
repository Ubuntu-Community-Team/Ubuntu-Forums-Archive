---
title: "How do I make ubuntu SERVER on virtualbox go full screen?"
date: 2010-10-26
forum: Virtualisation
---

### Post by guest_user on 2010-10-26
I've tried installing guest additions after installing linux-source but when installing I encountered a problem which says that xorg or xfree86 not found or something like that and the install failed, what should I do?

---

### Post by mr chip on 2010-10-28
The guest additions you mentioned are specifically for Xorg (the GUI), and a server running in text mode won't be using Xorg. 

If you want to have more text on screen, you need to look at changing the console framebuffer resolution.  Google threw up this thread: [http://ubuntuforums.org/showthread.php?t=1467946](http://ubuntuforums.org/showthread.php?t=1467946) which may be useful.

---

