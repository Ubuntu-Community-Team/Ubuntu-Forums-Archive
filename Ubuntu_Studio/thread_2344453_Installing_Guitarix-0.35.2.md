---
title: "Installing Guitarix-0.35.2"
date: 2016-11-25
forum: Ubuntu Studio
---

### Post by mike215 on 2016-11-25
I am trying install the latest version of Guitarix and it's been a real pain. I've had install a few things that were missing when compiling, and now I can't seem to install glibmm. I attached pics of what I get in terminal. 

Am I going about this the wrong way?

---

### Post by howefield on 2016-11-25
The images are difficult to read, you'd probably be better copying and pasting the text from the terminal back here.

---

### Post by CrocoDuck on 2016-11-25
> **howefield said:**
> The images are difficult to read, you'd probably be better copying and pasting the text from the terminal back here.

+1

If what I read is correct (not very clear pictures) you have to install libglibmm.

---

### Post by howefield on 2016-11-26
Probably libglibmm-2.4-dev is what you need, that is the package from a 16.04 install, it might be a different version depending on the version of Ubuntu you have but you can do an apt-cache search to find out.

```
apt-cache search libglibmm
libglibmm-2.4-1v5 - C++ wrapper for the GLib toolkit (shared libraries)
libglibmm-2.4-dbg - C++ wrapper for the GLib toolkit (debug symbols)
libglibmm-2.4-dev - C++ wrapper for the GLib toolkit (development files)
libglibmm-2.4-doc - C++ wrapper for the GLib toolkit (documentation)
```

---

