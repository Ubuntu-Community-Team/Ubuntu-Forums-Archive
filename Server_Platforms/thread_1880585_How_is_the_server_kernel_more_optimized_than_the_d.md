---
title: "How is the server kernel more optimized than the desktop kernel?"
date: 2011-11-14
forum: Server Platforms
---

### Post by olegsomphane on 2011-11-14
Just wondering, how is the server kernel more optimized than the desktop kernel? I was wondering if it would be better to start with a server install and add a window manager on it, or would that be worse than just starting with a desktop install. This is for a regular use workstation with a Phenom X6 and a AMD 6970...

---

### Post by aeiah on 2011-11-14
from that i gather, the main difference is the server kernel will try and consume more ram to make services more efficient.

---

### Post by lolium on 2011-11-14
From what i remember, the desktop kernel is preemptive, which means it can give a background program runtime on the cpu before its timeslice is over. Whereas a server kernel is not preemptive and is built to run things in the background.

So deciding which would be best all depends on your usage for the computer

---

