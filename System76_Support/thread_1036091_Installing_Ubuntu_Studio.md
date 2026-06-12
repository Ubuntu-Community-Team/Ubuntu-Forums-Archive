---
title: "Installing Ubuntu Studio"
date: 2009-01-10
forum: System76 Support
---

### Post by chez17 on 2009-01-10
Hi guys,

I was wondering if there is anything I should know or do if I want to try to install Ubuntu Studio on a partition of my laptop.

I have a Pangolin, model panp4n that currently runs 64 bit Intrepid.

I got the iso, specifically:

[http://cdimage.ubuntu.com/ubuntustudio/releases/8.10/release/](http://cdimage.ubuntu.com/ubuntustudio/releases/8.10/release/)

Will this be compatible with the system? Will the system76 drivers still work for Ubuntu Studio?

Thanks,
Dave

---

### Post by MorphWVUtuba on 2009-01-10
It's supported & you can install Ubuntu Studio from the default repos:

```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

Alternately, you can search "ubuntustudio" from synaptic & install only the features you want, if you don't want everything.

:)

---

