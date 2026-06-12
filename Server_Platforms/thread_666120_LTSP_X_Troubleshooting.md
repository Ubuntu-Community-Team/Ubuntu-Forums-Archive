---
title: "LTSP X Troubleshooting"
date: 2008-01-13
forum: Server Platforms
---

### Post by mjrmua on 2008-01-13
I´ve just set up of LTS server on Kubuntu 7.10.
Most of my clients are working however some of them give me a blank screen instead of the usual X Login screen.
I presume I need different XSERVER settings for these?
Can anyone suggest a systematic way of debugging this rather than trying values at random?

---

### Post by Dragonbite on 2008-01-14
You can modify /opt/ltsp/i386/etc/lts.conf and include the lines ```
[default]
X_DEFAULT_DEPTH=24
X_DEFAULT_RESOLUTION "800X600" "1024X768"
```

Here is a [[COLOR="Blue"]forum thread on setting up LTSP[/COLOR]]("http://ubuntuforums.org/showthread.php?t=368869")

---

