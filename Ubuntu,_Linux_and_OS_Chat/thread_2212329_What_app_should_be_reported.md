---
title: "What app should be reported?"
date: 2014-03-20
forum: Ubuntu, Linux and OS Chat
---

### Post by MasterNetra on 2014-03-20
I use a old IDE drive as a backup and connect to it via a USB to IDE/SATA connector. Up until I think 13.04 I had no trouble connecting to it even if it took Ubuntu about a minute or two to recongize it. As of 13.10 though Ubuntu no longer seems able to recongize it, I have to load a live-CD of a older version of Ubuntu and transfer from it. I was wondering if anyone knew what app I should report in a bug report.

---

### Post by lykwydchykyn on 2014-03-20
HDD support is in the kernel, so report against the kernel.

Does it show up with:
```

sudo fdisk -l

```

Or, does dmesg have any errors related to it?

---

### Post by MasterNetra on 2014-03-20
I won't know until later, all I know is that that the computer seem to sense something plug in then decided to do nothing about it. It didn't seem to show up anywhere. Though will check it later, at the library for internet.

---

