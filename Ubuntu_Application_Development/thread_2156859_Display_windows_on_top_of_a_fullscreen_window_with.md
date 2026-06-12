---
title: "Display windows on top of a fullscreen window without the Unity panel also popping up"
date: 2013-06-23
forum: Ubuntu Application Development
---

### Post by brezhoneg2013 on 2013-06-23
Hi,

   I'm writing a C ++ application directly programming Xlib. This application has to be run whatever the Window Manager.

   This application has a window that has to be displayed in fullscreen mode. This window is set to _NET_WM_WINDOW_TYPE_NORMAL and issues a _NET_WM_STATE_FULLSCREEN to toggle fullscreen. It works very fine with Unity.
   
   On top of this fullscreen window, I wish to pop up another window (top-level window) on a key press. This also works fine except that the Unity panel also shows up as long as this additional window is on screen.

   My question is : What should I do to prevent the Unity left panel from showing up in that case ? What properties (hints, EWMH, ...) should I set to tell Unity to keep hidden ?

  Thanks for any suggestions.

---

### Post by JAGroch on 2013-06-25
If it's a popup, maybe try (in your XLib code) passing the flag CWOverrideRedirect in XCreateWindow() when you create the window/popup. But it'll take control away from the window manager.  (So you'll probably lose window decorations like minimize and close.)

---

