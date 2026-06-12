---
title: "Custom kernel module on start-up"
date: 2013-01-21
forum: Server Platforms
---

### Post by smartdipu on 2013-01-21
Hello experts,

I have a custom kernel module foo.ko that I want to be loaded when the system boots. I know that I can move it to /lib/modules/`uname -r`/...., add entry inside /etc/modules and it will work.

However, my requirement is bit different: I want to load it from a different directory. How can I tell modprobe to look into the /mypath/lib/modules directory instead of /lib/modules?

Additionally I want to perform some additional tasks such as using mknod to create some files in /dev. 

I can do all this with an init.d script but I believe there's a better way out there.

Please help. Thanks for your time. 

Version: Ubuntu 10.04 LTS Server edition

---

