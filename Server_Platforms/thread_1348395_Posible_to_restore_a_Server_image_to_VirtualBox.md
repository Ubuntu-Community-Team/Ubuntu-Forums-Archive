---
title: "Posible to restore a Server image to VirtualBox?"
date: 2009-12-07
forum: Server Platforms
---

### Post by tiger.woods on 2009-12-07
I'm curious if there is a way to restore an image of a server to VirtualBox so that I could run some testing/compiling on it as opposed to running it on the server itself?

Thanks for any input.

TW,

---

### Post by memilanuk on 2009-12-07
In theory, yes.  If you imaged your system with Clonezilla and stored the image on your network somewhere accessible to Virtualbox, you should be able to 'boot' a virtual machine using clonezilla and restore from that image to the new virtual machine.

In practice... haven't tried it yet.  Let me know how it goes ;)

---

