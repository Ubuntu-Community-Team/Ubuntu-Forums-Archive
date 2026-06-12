---
title: "microphone disappears upon installing Lucid"
date: 2010-06-24
forum: System76 Support
---

### Post by VOLKOV9 on 2010-06-24
I just did a clean install of Lucid.  So far everything seems to be working except for the built-in microphone.  I remember that in Karmic or Intrepid I had to fiddle some settings to get it working, but the audio configuration appears different now.  I've tried everything in System > Preferences > Sound > Input to no avail.  I tried searching this forum as well as knowledge76 for similar posts as well - if I missed it, please point me in the right direction.

Thanks in advance for the help.

---

### Post by tech newbie on 2010-06-24
Try to open a terminal and type:

```
gstreamer-properties
```

Under audio tab, in the Default Input. Try changing the device and click test. Talk into mic when test is on. When u get a working setting click ok and close it.

---

