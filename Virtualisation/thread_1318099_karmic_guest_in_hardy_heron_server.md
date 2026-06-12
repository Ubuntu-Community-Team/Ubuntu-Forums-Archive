---
title: "karmic guest in hardy heron server"
date: 2009-11-07
forum: Virtualisation
---

### Post by pbrille on 2009-11-07
Hi,

I've running a Hardy Heron 8.04 server x64 version with xen.
Now I'd like to use xen-tools to install a new Karmic installation for testing purposes.
I don't see karmic available for doing a debootstrap installtion.

What can I do?

THX

---

### Post by pbrille on 2009-11-10
There's no update via apt of the xen-tools which would include support for a debootstrap 9.10 installation. I don't see how a manual installation of the xen-tools version would work in my enviroment. I assume that the current version of the tools would include support for a karmic installation, does it?

---

### Post by fjgaude on 2009-11-11
Well, from my looking around, and trying things, 9.10 is not something that is ready for everything... lots of issues with VMware Server and other VM making software. I think we will have to wait for sometime before we get back to where 9.04 or 8.10 is.

---

