---
title: "Holy dang WoW in directx?"
date: 2010-05-23
forum: Wine
---

### Post by dardack on 2010-05-23
So, I had always set:


SET gxApi "OpenGL"

but recently a bunch of my .ini/config files got corrupted somehow (wow's Config.wtf being one of them).  I useed a backup, or so I thought.

It's been a few months, 10/25 raids/LK kills, and I didn't have:


SET gxApi "OpenGL" 

I found out looking for it for an answer to another thread.  I haven't had much issue, except if I went to different workspaces alot, wow would crash.  Last time i tried WoW and directx in wine, it would crash all the time.  This is impressive in my mind.

---

### Post by hikaricore on 2010-05-24
Wine converts DirectX to OpenGL, dx support has also improved a lot in the last few years.
That said, not setting the option just makes your system work a little harder.
The flipside of this is that OpenGL mode in Wow imho is slightly less precise than dx mode.
This is the only explaination in cases of better framerates etc without the OpenGL flag.

---

