---
title: "Source for 2.6.24-12-xen?"
date: 2008-04-17
forum: Virtualisation
---

### Post by tinkertim on 2008-04-17
Hello to all. I'm using Hardy with 2.6.24-12-xen, I want to obtain the kernel source to take out some bloat that I'm not using.

I got the source package for linux-image-2.6.24-12-xen , however there are a lot of symbols in the binary package that aren't in the source package - in particular all of the dom-0 stuff. 

Examples are XEN_INTERFACE_VERSION , XEN_PRIVILEGED_GUEST, etc .. 

Is there some other package or patch that I need, if so does anyone know where to find it?

I've been grabbing the source packages for all of the Ubuntu supplied modules and others, I don't see dom-0 ops in any of them.

Any help is appreciated :)

---

