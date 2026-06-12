---
title: "Should automatic codec-install work in Ubuntu 13.04?"
date: 2013-02-24
forum: Ubuntu Development Version
---

### Post by moma on 2013-02-24
Hello,
**Gnome-codec-install crashes:**
I want to use gnome-codec-install in my application to automatically search and add missing audio-codecs. But the program crashes when ran on Ubuntu 13.04.
See [bug #1126610]("https://bugs.launchpad.net/ubuntu/+source/gnome-codec-install/+bug/1126610").
 
I tested these commands:
$ gnome-codec-install 'gstreamer|0.10|manual|amr audio|encoder-audio/AMR'
and
$ gnome-codec-install 'gstreamer|0.10|totem|DivX MPEG-4 decoder|decoder-video/x-divx, divxversion=(int)4'

These examples are from the program's website.
 
Both commands fail with:
File "/usr/lib/python2.7/dist-packages/aptdaemon/client.py", line 55, in <module>

class AptTransaction(GObject.Object):
AttributeError: 'module' object has no attribute 'Object'
---

Should gnome-codec-install function in Raring or is it to be replaced by something else?

---

### Post by dino99 on 2013-02-24
gnome-codec-install has been updated on dec-2011 for the last time  ;)  and by the way its not the actual default ubuntu (raring) choice, which use sessioninstaller instead.

---

### Post by moma on 2013-02-25
Hello,
Thank you.
Session-installer does exactly what I was looking for.
[https://launchpad.net/sessioninstaller](https://launchpad.net/sessioninstaller)

---

### Post by mörgæs on 2013-02-25
If this solves your problem, please mark the thread so.

Also, please close the bug report if it is no longer relevant.

---

### Post by moma on 2013-03-12
I need more time to experiment with sessioninstaller.
I will mark this issue solved if everything goes well.

---

### Post by dino99 on 2013-03-12
As you can see, no one care now about that outdated package (since sessioninstaller replace it)

(actuaally 24 bugs are opened since ages, and none have been answered or assigned)

So thats it

---

