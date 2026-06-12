---
title: "Is there a way to install uhci-hcd (for use with a modem)?"
date: 2010-07-27
forum: Server Platforms
---

### Post by marshall.robert on 2010-07-27
Hi,

I've been searching for hours now, and I can't find anything. I am trying to install a (win)modem, one BT Voyager 105, and when I run eciadsl-start it fails with this: 
```

/usr/bin/eciadsl-start: line 263: fatal: command not found
cat: /proc/bus/usb/devices: No such file or directory
Loading UHCI support... Warning: uhci-hcd module doesn't exist
```I believe I can get this module by recompiling the kernel or something, but this is a server which is running a website with a database for a game server and a mail server too, among other things, so that's not really an option. My main goal is to get this to replace my ever increasingly unreliable ADSL router.

So I ask; is there a way that I can get this uhci-hcd module without recompiling?

---

