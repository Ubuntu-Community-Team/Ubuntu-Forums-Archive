---
title: "I took the USP off my taskbar but now i can't put it back on..."
date: 2006-09-27
forum: Ubuntu System Panel
---

### Post by jason.b.c on 2006-09-27
I removed the USP from the taskbar ( don't ask me why i did that ) but now i can't get it to put itself back on there..

Here is the error message i recieve:

> The panel encountered a problem while loading "OAFIID:GNOME_USP".

What does that mean..??

I right click the taskbar and choose "add to panel" , when the window pop's up i scroll down to "Ubuntu System Panel" and i drag it to the taskbar where i want it , That's when i get the error...


How do i completely remove ( uninstall ) the USP..???

---

### Post by bulldog on 2006-09-27
Try not to drag,but simply click it and hit apply at the botom and close the window.

---

### Post by jason.b.c on 2006-09-28
> **bulldog said:**
> Try not to drag,but simply click it and hit apply at the botom and close the window.

That was a good suggestion bulldog but unfortunatly it still dosen't work...

> The panel encountered a problem while loading "OAFIID:GNOME_USP".

Same error message again..:mad:

---

### Post by hanzomon4 on 2006-09-28
Me too just updated to edgy 

```
The panel encountered a problem while loading "OAFIID:GNOME_USP".
```

---

### Post by jason.b.c on 2006-09-28
I don't understand this , I even completely removed the USP through synaptic and then downloaded the latest version and installed it..

And it still won't reapply itself back to my taskbar...](*,) 

Man i wish i could get it back on , I can't stand these stock menu's..

---

### Post by hanzomon4 on 2006-09-28
Got it try this >  sudo apt-get install  python-dbus python-gnome2 python-gst0.10


---

### Post by cumic on 2006-10-27
I have the same problem, I debugged usp and I have found the "problem" :)

The problem is that edgy installs python2.5, but "python" is linked to python2.4

An eventual solution is to execute this:

```
$ python2.5 usp
```

Another solution is to remove python2.4 packages...

---

