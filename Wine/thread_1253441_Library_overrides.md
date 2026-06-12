---
title: "Library overrides"
date: 2009-08-30
forum: Wine
---

### Post by risingsun on 2009-08-30
Hi I've consulted the wine FAQ on this but I was just looking for a little clarification.

If a library override is setup in winecfg, where does it check for native libraries copied from a windows installation? (I think it's the system32 directory of a wine configuration but I'm not sure.) 

Also, if you then remove the override or the native library I presume it goes back to checking for builtin libraries. If the builtin library in the system32 folder was overwritten by a native version of the library, is it still able to find a builtin version of the library somewhere?

Many thanks.

---

### Post by ackanao on 2009-08-30
In most cases built-in libraries will not be overritten so you don't have to worry about that - just copy the libraries to system32 folder and apply needed overrides.

Some applications (like IE) will overwrite Wine implementation of Windows API - it's never a good idea to install such applications in default wineprefix because it will render Wine useless for any other application you may want to use. For such applications it's better to create new wineprefix - that way you can do whatever you want with that wineprefix and when it's completely messed up, simply delete it, create new one, and try again.

Take a look at this thread for an explanation on how to create new wineprefixes and how to use them.

[http://ubuntuforums.org/showthread.php?t=1252512]("http://ubuntuforums.org/showthread.php?t=1252512")

---

