---
title: "Handling mouse movement with Xinput"
date: 2024-09-18
forum: Ubuntu Application Development
---

### Post by vladimir1128 on 2024-09-18
Hi everyone. I'm making a custom game engine and recently I changed keyboard and mouse handling from X to Xinput in order to be able to get raw input and mouse offsets instead of coordinates. But the problem is that XI_RawMotion is sent only when the pointer is inside the window. Which is quite logical and works well in fullscreen mode but is not acceptable in windowed mode. Using XIGrabDevice didn't change the situation, or maybe I used it in a wrong way. Are there any ideas about how to turn on an exclusive mode or something? :)

---

### Post by TheFu on 2024-09-18
First thing to ask is whether Xinput works with Wayland.  Coding for Xorg (aka X11) is a short-term idea at this point.

---

### Post by vladimir1128 on 2024-09-18
Well, typing "echo $XDG_SESSION_TYPE" in Terminal gave the result "wayland". So in general it works. But yes, I'll also try to research input handling on Wayland, just in case

---

