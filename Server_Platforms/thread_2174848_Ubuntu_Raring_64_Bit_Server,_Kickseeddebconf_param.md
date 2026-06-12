---
title: "Ubuntu Raring 64 Bit Server, Kickseed/debconf parameter to skip security updates"
date: 2013-09-16
forum: Server Platforms
---

### Post by TPHkXAr on 2013-09-16
Hello everyone! 

I have a cobbler 2.2.2 setup running and although it successfully does deploy Raring, it gets stuck for about 5 minutes while it tries to resolve "security.ubuntu.com" which I'm guessing where it tries to get fresh security patches/updates? 

**I have it all setup on a private switch with no access to the public internet.**

Does anyone know the proper debconf/kickseed parameter I need to put in my kickstart file to get it to skip that? I tried the following parameters and they don't seem to be doing anything.

[B]preseed d-i pkgsel/update-policy select none
preseed d-i pkgsel/upgrade select none
preseed d-i apt-setup/services-select multiselect none[/B]

Any help is much appreciated!

---

