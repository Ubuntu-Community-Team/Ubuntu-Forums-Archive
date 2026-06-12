---
title: "system support package in karmic not installable"
date: 2009-10-01
forum: System76 Support
---

### Post by viridari on 2009-10-01
I know karmic is still not considered stable, but I installed it on my Pangolin Performance and then immediately tried to install the System76 support package.

I got an error back:
```
dpkg: unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor
```

---

### Post by viridari on 2009-10-01
Nevermind. The GUI package installer spawned by Firefox was choking on it. But if I download the package and install it from a shell with dpkg, it works fine.

---

### Post by thomasaaron on 2009-10-02
While the System76 Driver .deb package will *install* on Karmic, it will not *run* on Karmic. 

We won't release a package compatible with Karmic until 9.10 is actually released.

---

### Post by jtappin on 2009-10-06
> **thomasaaron said:**
> 
We won't release a package compatible with Karmic until 9.10 is actually released.

Will you be announcing here when it's available or should we assume that when karmic-final hits the Ubuntu servers the System76 drivers will also be available?

---

### Post by thomasaaron on 2009-10-06
We always post an announcement on the forums.

---

### Post by jtappin on 2009-10-07
Thanks for the info. I didn't have a System76 machine at the time of the Jaunty release.

---

