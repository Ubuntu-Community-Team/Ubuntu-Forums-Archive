---
title: "install openjdk *not* headless on cloud server?"
date: 2020-05-02
forum: Server Platforms
---

### Post by syadnom on 2020-05-02
I'm running an EC2 instance (also applies to the lightsail instance) and those are 'Ubuntu Cloud Image (instance)' as reported by tasksel.

When I install openjdk, this automatically installs the 'headless' version of the openjdk and openjre packages which lack sound and printing support.  My application needs to print so this has become a hard-stop as I can't seem to figure out how to force this to install the 'full' package.

any help greatly appreciated.

Thanks.

---

