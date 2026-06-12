---
title: "Announcing: Xinput-UI: GUI front-end for Multi-Pointer X (MPX.)"
date: 2013-03-07
forum: The Cafe
---

### Post by MaxIBoy on 2013-03-07
Multi-Pointer X has been in X.Org for a while now. If you don't know what it is, here's a video:
[video=youtube;b2iYNfl-2Es]https://www.youtube.com/watch?v=b2iYNfl-2Es[/video] 
As far as I know there's never been a GUI utility for configuring it. By default, all mice and keyboards are attached to a single pointer, and if you want another, you use the "xinput" utility to set it up. I'm fine with using the command line, but I'm planning to incorporate MPX support into a separate project soon, and decided that end-users should have a way to configure multiple mouse pointers graphically. Plus, I've been waiting for an excuse to learn wxPython, so I figured I might as well write one myself.

Here it is:
[https://github.com/Max-E/xinput-ui](https://github.com/Max-E/xinput-ui)

[img]http://img201.imageshack.us/img201/6342/screenshotsso.png[/img]

It currently consists of a single Python file, which you run without any arguments. It requires Python 2.7 and the Python bindings for wxWidgets. Multiple versions of wxWidgets are available, but I've only tested with python-wxgtk2.8, available in the repos. Detailed instructions for using it are in the README.

Enjoy! And please report any bugs.

---

