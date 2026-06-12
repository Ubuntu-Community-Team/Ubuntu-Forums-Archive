---
title: "Packages: Options used during build"
date: 2008-11-16
forum: Server Platforms
---

### Post by sprucio on 2008-11-16
I'm currently looking for a way to see what type of options were used when Ubuntu built the squid3 package. According to the documentation, the option "enable-ssl" is need during compile time.

Does anyone know how I can check if this(or other options) were used during compile time?

---

### Post by psusi on 2008-11-16
Get the source package ( apt-get source squid ) and look in the debian/rules file for where it runs configure and see what it gets passed.

---

