---
title: "Ubuntu Thin Client"
date: 2008-01-24
forum: The Cafe
---

### Post by Black Mage on 2008-01-24
Hey,

I'm trying to make a thin-client server and I'm wondering if I need any special equipment. Like can I just use a regular computer with a regular network card and DHCP server? No special equipment or installation?

---

### Post by koenn on 2008-01-24
depends how thin you want the client to be. If it's a diskless terminal, you need some software, such as a boot image that can be loaded of a network server.
If your clients need to boot of their network cards, you need a network card that supports that. NICs with PXE net boot are easiest. Older cards can be made to work as well but require some more work. 

Look up LTSP and Edubuntu/

---

