---
title: "Memory issues/leak"
date: 2006-05-19
forum: Server Platforms
---

### Post by zac1333 on 2006-05-19
Here's my setup:

SuperMicro P3TDLE with Dual P3 1.4GHz CPUs
512MB RAM
PCI SATA Card connected to Maxtor 80GB SATA drive

Here's what I installed (in order):

Ubuntu server
SSH
MySQL
Apache 2
PHP4

The only variation is that I have apt-cacher running on another machine here in the office, so I modified the sources.list on this machine to point to the apt-cacher machine.

As of right now, when I run top, it shows this:

Mem:    515936k total,   258616k used,   257320k free,    99440k buffers
Swap:  1502036k total,        0k used,  1502036k free,   107620k cached

Last night, when I left, memory usage was around 145000k.  Why is this happening?  This machine is behind a firewall, so there isn't anything open to the outside world.

---

### Post by tribaal on 2006-05-19
Linux manages memory in a different way than other OSes:
When your system doesn't use all your RAM, linux uses the spare space to cache disk data. Whenever your system needs to use more RAM the disk cache will be cleared and your application will be loaded in it's place.

This is especially useful when you run databases and webservers, since it can serve stuff that would otherwise have to be fetched on the disk (which is really longer).

More info on the subject [here]("http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf").

- trib'

---

### Post by zac1333 on 2006-05-19
Ahh ok, that link you sent me explains it well.  So I'm guessing I should not be worried about watching memory usage, since it will automatically transfer back memory to applications from disk cache if it's needed.

Thanks!

---

