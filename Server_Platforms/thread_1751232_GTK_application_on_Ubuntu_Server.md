---
title: "GTK application on Ubuntu Server"
date: 2011-05-06
forum: Server Platforms
---

### Post by darknite64 on 2011-05-06
Hey guys,

I have a server running Ubuntu Server 11.04. It works like a charm.

Now, I have an application that I must run on the server. When I try to start it as-is, it displays *Gtk-WARNING **: cannot open display*. I assume I have to install some software for this to work. Probably X, Gnome/KDE and GTK.

Unfortunately, the application is custom made, and has no CLI-based alternative. Note that despite the fact that the application seems to be using GTK, I don't actually have to use the GUI. I just want to start the application.

My question is: **What are your thoughts on getting this - GTK requiring - application to work on the server?** What would be my next step?

Thanks in advance!

---

### Post by dtfinch on 2011-05-06
Xvfb might work.

[http://ubuntuforums.org/showthread.php?t=1740572](http://ubuntuforums.org/showthread.php?t=1740572)

---

