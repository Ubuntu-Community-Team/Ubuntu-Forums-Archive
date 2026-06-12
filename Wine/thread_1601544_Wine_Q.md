---
title: "Wine Q"
date: 2010-10-20
forum: Wine
---

### Post by kagardner on 2010-10-20
I heard you were able to change D3D to OpenGL so that games wouldn't have extremely low FPS, I tried playing WoW and it was terrible. Thought this might help, anybody tell me how I can do this?

---

### Post by Rikev on 2010-10-20
Go into the folder holding your files for WoW and look for the folder WTF (yes it is called that! Crazy devs). Then edit the file config.wtf to include the following:

```
SET gxApi "opengl"
```

Alternatively, if you start the program from a Terminal add -opengl on the end of what you type to start it.

---

