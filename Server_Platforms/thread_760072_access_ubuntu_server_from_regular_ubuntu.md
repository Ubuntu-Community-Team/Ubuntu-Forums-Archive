---
title: "access ubuntu server from regular ubuntu"
date: 2008-04-19
forum: Server Platforms
---

### Post by rotatorkuf on 2008-04-19
hi all

I've had a server before, It was set up with windows 2003 server os. I was able to access this system using the remote desktop connection in windows xp regular and work with it through the gui.

What i'm wondering is if I can do the same thing with ubuntu 7.10?

Can I connect to the server [which I already have set up using ubuntu 6.0.6] through the gui?

I know I can easily connect to it using the terminal, but i'm trying to avoid the terminal connection.

---

### Post by conjur3r on 2008-04-19
Yes you can, but to access a GUI on the server, you need a desktop installed first.  The server comes minus any GUI/desktop.  This is what differs between the server and desktop versions.  Once you've installed a desktop (ubuntu-desktop, kubuntu-desktop, xubuntu-desktop, and so forth), you can use remote login or VNC to obtain a GUI from another machine.

---

### Post by volkswagner on 2008-04-20
You can also try webmin.  This can give you web based GUI without running a GUI on your server.

---

### Post by ikonia on 2008-04-20
webmin is not packaged or supported by ubuntu, and has massive security holes in it, so not recommended

Using X11 over the internet is not really advised, neither is havine an X11 service running on a direct internet connected machine.

The server edition is intended to be managed by a secure remote connection on something like ssh using the command line interface.

You can do things like ssh tunneling for X11, but the exploits on X11 make is still unrecommended.

---

