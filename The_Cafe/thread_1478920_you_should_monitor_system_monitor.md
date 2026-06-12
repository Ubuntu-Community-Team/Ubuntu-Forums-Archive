---
title: "you should monitor system monitor"
date: 2010-05-10
forum: The Cafe
---

### Post by sdowney717 on 2010-05-10
I just noticed a java ?? running which consumed 96% of the CPU and heated up the CPU's 15 degrees C.
I dont know what it was, I have noticed it before. You can easily see it when the CPU activity window of system monitor is filling up with blue.
Just right click it and kill the processs. Otherwise for me it runs endlessly. If people dont notice this I suppose they will use more power, create more heat, and maybe slow down the system.

---

### Post by tom66 on 2010-05-10
Yes I too have problems with Java running after I close a tab in Firefox, have to kill it all the time.

---

### Post by philinux on 2010-05-10
Yes, I have cpu scaling and system monitor in the top panel.

Sun java has been deprecated in Lucid Lynx. Openjdk is now the default, i.e installing ubuntu-restricted-extras with recommends will install openjdk and the icedtea plugin. Openjdk has been certified by Java SE Test Compatibility Kit (TCK) and is compatible with the Java(TM) SE 6 platform on the amd64 (x86_64) and i386 (ix86) architectures. However sun-java is in the partner repo.
There's a bug regarding the icedtea plugin and certain applets.
[https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/551328](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/551328)
Not fixed yet. Workaround may be to create a new Firefox profile.

---

