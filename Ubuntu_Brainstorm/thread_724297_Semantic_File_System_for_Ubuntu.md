---
title: "Semantic File System for Ubuntu"
date: 2008-03-14
forum: Ubuntu Brainstorm
---

### Post by technomaniac on 2008-03-14
I want to resurrect GLSCUBE ([www.glscube.com](www.glscube.com)). Its aim was to develop a semantic file system for GNU/Linux. However, the developers do not have enough time now. A semantic file system for GNU/Linux is essential because even MS is working on WinFS. GLScube looked promising but the developers are of the view that the code has become hard to manage and a complete re-write would be necessary. Also another project that had similar intentions was GNOME Storage but absolutely no work has been done on it. I want to mix ideas from GLSCube, GNOME Storage ans Microsoft WinFS and create a semantic file system for GNU/Linux.I am planning to start it this vacation. Any suggestions and ideas are welcome.

---

### Post by reidbold on 2008-03-19
WinFS is dead. I think everyone(especially those who start working on it) have realized that semantics should occur at the application layer. Reiser5 or 6 would have been the best shot at a real, useable SFS, but they're dead too!

---

### Post by 23meg on 2008-03-19
[QUOTE=technomaniac]Any suggestions and ideas are welcome.[/QUOTE]

[QUOTE=reidbold]I think everyone(especially those who start working on it) have realized that semantics should occur at the application layer. [/QUOTE]

Indeed; why not work on XESAM integration in virtual filesystems and file managers instead? You'll have a hard time convicing major distributions to switch to your new filesystem, especially if it doesn't go upstream (and it probably won't).

---

