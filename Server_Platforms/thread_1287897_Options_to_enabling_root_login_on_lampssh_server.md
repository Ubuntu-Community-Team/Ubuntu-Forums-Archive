---
title: "Options to enabling root login on lamp/ssh server"
date: 2009-10-10
forum: Server Platforms
---

### Post by jeffsa12 on 2009-10-10
Below is a copy and paste from a previous post of mine at [http://ubuntuforums.org/showthread.php?t=1281777](http://ubuntuforums.org/showthread.php?t=1281777)

I'm using Nautilus to manipulate the file system on my server w/o X installed, via remotely on my local network from a Linux desktop, Gnome+ all extras installed.

What other applications would work this way, and I'd appreciate any reference info on doing so.

Could I just control SSH root login from my local network only as a secure alternative?

> I did a fresh 8.04 32 bit lamp/ssh server install on real (not virtual) hardware today and got my website back up.

The Nautilus connection to a remote file system via ssh server works awesome!!

This really should be promoted more often as a great option to installing a GUI on Ubuntu server to the newbs and GUI lovers like me.

I did have to enable root login on my server to manipulate files remotely using Nautilus though. Sorry, it's not allowed to explain how to do that here. Perhaps someone will step in and explain an option thats better in this situation...

Could always disable root login after getting things set up...Now I'll have to go find that command!!

---

### Post by Iowan on 2009-10-11
> **jeffsa12 said:**
> Could I just control SSH root login from my local network only as a secure alternative? You *should* be able to limit SSH users (including **root**?) to specific machines or networks, but I don't remember the details.

---

