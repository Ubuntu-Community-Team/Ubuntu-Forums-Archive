---
title: "icedtea-7-plugin ?"
date: 2012-02-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ft_ on 2012-02-05
Hi,

We got recent icedtea updates, including icedtea-7-plugin.
I set the correct (for me) java and mozilla-plugin alternatives, ie version 7.

When I open eg Geogebra (webstart) :
[http://www.geogebra.org/cms/en/download](http://www.geogebra.org/cms/en/download)
I can see that java-6 is still used instead of java-7.

javaws is showing only one alternative in a java-6 folder...

What's the problem ?

Thanks !

---

### Post by Sworddragon on 2012-02-05
I have just uninstalled icedtea-6-plugin so I have no problems. But I'm wondering why openjdk-6-jre is still needed if icedtea-7-plugin is installed. I can't remove OpenJDK 6 from my system without breaking it.

---

### Post by zika on 2012-02-05
> **Sworddragon said:**
> I have just uninstalled icedtea-6-plugin so I have no problems. But I'm wondering why openjdk-6-jre is still needed if icedtea-7-plugin is installed. I can't remove OpenJDK 6 from my system without breaking it.
default-jre and default-jre-headless icedtea-netx-common etc are not (yet) upgraded...

Question: Did You get icedtea-7 upgrades &#8222;regularly&#8220; or did You force it? At my place I had to force it (even though I still use Oracle Java/ SE)...

---

### Post by Sworddragon on 2012-02-05
I have forced the installation. A normal dist-upgrade wanted just to remove icedtea-plugin and install icedtea-6-plugin.

---

### Post by zika on 2012-02-05
> **Sworddragon said:**
> I have forced the installation. A normal dist-upgrade wanted just to remove icedtea-plugin and install icedtea-6-plugin.
Funny, at my place it all started with```
Will install 0 packages, and remove 3 packages.
67.4 MB of disk space will be freed
===============================================================================
[REMOVE, NOT USED] icedtea-6-plugin
[REMOVE, NOT USED] linux-headers-3.2.0-12
[REMOVE, NOT USED] linux-headers-3.2.0-12-generic
===============================================================================

```and that made me realize that icedtea-7 was available...

---

