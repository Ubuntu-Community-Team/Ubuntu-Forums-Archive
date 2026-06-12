---
title: "Preseeding after install"
date: 2010-08-05
forum: Server Platforms
---

### Post by kkinder on 2010-08-05
I've read a bunch of tutorials on using the Debian/Ubuntu Preseeding technique for automating installations questions upon install. They all discuss putting the preseeding config file in the bootable media you use to install.

I want to use preseeding, but after the fact. Something to the effect of:

```
apt-get install (packages) --preseeding-config=(file)
```

This is because I'm booting up boxes that are already configured with a particular image, and I want to automate subsequent installations that I don't want to put on the image itself.

Any advice?

---

