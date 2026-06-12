---
title: "Run an X window application locally"
date: 2010-08-02
forum: Server Platforms
---

### Post by wesg on 2010-08-02
I'm adding a GUI to my server for specific admin tasks (Xubuntu desktop), and the major one I have in mind is MythTV setup, which uses X server. How can I run an X session locally? Ie. I'm looking to VNC into my server, then from there start an app that displays mythtv-setup in an X environment.

---

### Post by ruffEdgz on 2010-08-03
Quick question: Why not just ssh and use X11 forwarding to accomplish what you want?

I have never been able to complete this on my local server before but it seems you might just need to follow this guide and the "X11 Server Installation" part to maybe get what you want: [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)

Having that windows manager on there (fluxbox, openbox, etc...) will allow you to get into a lightweight GUI environment when you VNC into your box.

Just a thought and I am going to try this myself on my test environment soon. Hope this helps?

---

### Post by LightningCrash on 2010-08-03
With SSH's X11 forwarding you won't need an X server on the remote box at all. You just need xauth on the remote box and that's pretty much it.

You only need VNC if you want to leave a session running.

---

### Post by wesg on 2010-08-04
I hacked together a VNC server that provides me with temporary sessions, enough to run the mythtv-setup program. That's good enough for me!

---

