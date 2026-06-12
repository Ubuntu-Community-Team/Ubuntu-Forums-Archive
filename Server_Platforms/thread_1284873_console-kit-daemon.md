---
title: "console-kit-daemon"
date: 2009-10-07
forum: Server Platforms
---

### Post by MisterM on 2009-10-07
Hi,

I've been having [serious issues (link)]("http://www.howtoforge.com/forums/showthread.php?t=38128") with swap usage on our production server, and I believe console-kit-daemon is to blame. The server is running ispconfig with apache, php, mysql, postfix, mydns,...

Is it safe to remove the consolekit package on a server? As far as I could make out (from googling about it), this package is only useful in a desktop environment. When I try to remove it, it says the following packages will be removed: consolekit dbus dbus-x11. **Is it safe to remove all these packages in a server environment?**

---

### Post by MisterM on 2009-10-23
Anyone? :-?

---

### Post by druhboruch on 2009-10-24
I would also very much like to know the answer to your question...

---

### Post by druhboruch on 2009-10-26
I guess no one knows the answer so we will have setup test server and find out the hard way.

I will be setting up Karmic soon, so I will let you know in a few days.

---

### Post by MisterM on 2009-10-26
> **druhboruch said:**
> I guess no one knows the answer so we will have setup test server and find out the hard way.

I will be setting up Karmic soon, so I will let you know in a few days.

Thanks, that would be much appreciated.

---

### Post by druhboruch on 2009-10-28
I just installed Karmic RC server / minimal system.
Package console-kit-daemon is now called consolekit and it is not installed.  

I think that you could safely remove it and all dependent packages.

---

### Post by MisterM on 2009-10-28
> **druhboruch said:**
> I just installed Karmic RC server / minimal system.
Package console-kit-daemon is now called consolekit and it is not installed.  

I think that you could safely remove it and all dependent packages.

Thanks for reporting back!

I have now removed it, and everything seems to be working fine. :D
I do hope this solves my swap issue.

---

### Post by wootah on 2009-10-28
Well, D-BUS is used for InterProcess Communication (IPC), message passing if you will. You can use the dbus to signal the gnome-screensaver to activate or wake-up. For GNOME, it was developed to replace Bonobo (another IPC type service) and was based off of the DCOP of KDE (another IPC). ([http://en.wikipedia.org/wiki/D-Bus](http://en.wikipedia.org/wiki/D-Bus))

You can't just remove console-kit-daemon without it's dependancies?

As to console-kit, the main purpose (from a cursory glance at its documentation) is session management. ([http://www.freedesktop.org/software/ConsoleKit/doc/ConsoleKit.html](http://www.freedesktop.org/software/ConsoleKit/doc/ConsoleKit.html))

---

### Post by MisterM on 2009-10-28
> **wootah said:**
> Well, D-BUS is used for InterProcess Communication (IPC), message passing if you will. You can use the dbus to signal the gnome-screensaver to activate or wake-up. For GNOME, it was developed to replace Bonobo (another IPC type service) and was based off of the DCOP of KDE (another IPC). ([http://en.wikipedia.org/wiki/D-Bus](http://en.wikipedia.org/wiki/D-Bus))

You can't just remove console-kit-daemon without it's dependancies?

As to console-kit, the main purpose (from a cursory glance at its documentation) is session management. ([http://www.freedesktop.org/software/ConsoleKit/doc/ConsoleKit.html](http://www.freedesktop.org/software/ConsoleKit/doc/ConsoleKit.html))

Thanks for the explanation, but GNOME is not installed, or any other window manager for that matter. It's a server. So, I guess I'm OK?

---

