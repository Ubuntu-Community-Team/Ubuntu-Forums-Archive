---
title: "How does Beryl work?"
date: 2007-02-11
forum: The Cafe
---

### Post by FuturePilot on 2007-02-11
Ok, so ever since I started using Beryl I've been curious to how exactly it works. How can you go from something that can't support transparent textures to something that can support them along with so much more. Can someone explain?:popcorn:

---

### Post by ~LoKe on 2007-02-11
Xorg.

---

### Post by shareMenaPeace on 2007-02-11
> **FuturePilot said:**
> Ok, so ever since I started using Beryl I've been curious to how exactly it works. How can you go from something that can't support transparent textures to something that can support them along with so much more. Can someone explain?:popcorn:
> 
Structuring all rendering on top of OpenGL could potentially simplify video driver development. It removes the artificial separation of 2D and 3D acceleration. This is advantageous as 2D operations are frequently unaccelerated (which is counterintuitive, since 3D would imply 2D).

It also removes all driver-dependent code from the X server itself, and allows for accelerated Compose and Render operations independent of the graphics driver.

Additionally, composite managers can use the OpenGL API for rendering, allowing for quite amazing effects. It has been reported that affiliates from NVIDIA and ATI are willing to release binary-only drivers for an OpenGL-based X server once a defined API has been established, though on the Xorg Developers Conference 2006 NVIDIA indicated that they are quite happy with the existing driver interface as well. The idea of extending this is being worked on in the AIGLX project by the Fedora Project. [9]

History

Xgl was originally developed on public mailing lists, but for a long time, until January 2, 2006 most [1] development of Xgl was done behind closed doors. On that day the source to Xgl was re-opened to the public [2] [3], and included in freedesktop.org, along with major restructuring to allow a wider range of supported display drivers. X server backends used by Xgl include Xglx and Xegl. In February 2006 the server gained wide publicity after a public display where the Novell desktop team demonstrated a desktop using Xgl with several visual effects such as translucent windows and a rotating 3D desktop. [4] [5] [6] The effects had first been implemented in a composite manager called glxcompmgr (not to be confused with xcompmgr), now deprecated because several effects could not be adequately implemented without tighter interaction between the window manager and the composite manager. As a solution David Reveman developed Compiz, the first proper OpenGL compositing window manager for the X Window System[7]. Later, in September 2006, the Beryl compositing window manager was released as an alternative to the original Compiz.
[http://en.wikipedia.org/wiki/Xgl](http://en.wikipedia.org/wiki/Xgl)

Novell made a video
[http://youtube.com/results?search_query=novel+xgl&search=Search](http://youtube.com/results?search_query=novel+xgl&search=Search)

---

### Post by FuturePilot on 2007-02-11
Good link thanks.:)

---

