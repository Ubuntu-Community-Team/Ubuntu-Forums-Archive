---
title: "Gstreamer-properties"
date: 2014-12-24
forum: Ubuntu Development Version
---

### Post by zika on 2014-12-24
If I try to open it I get```
Failed to load UI file; please check your installation.
```
Any ideas before I start to look for free time to dwell on that?

---

### Post by mc4man on 2014-12-24
The gnome-media source is no longer maintained by Gnome,  whether they have a different means to do whatever the properties capplet does no idea. ( or maybe they think such stuff isn't needed.
Ubuntu/Debian have been carrying the old source for just the capplet, probably it broke on the new gtk & or glib. At some point it should be dumped entirely.

---

### Post by Yellow Pasque on 2014-12-25
IIRC, gstreamer-properties used to set the sinks in gconf for gstreamer0.10. Now, you can do that manually by running dconf-editor and looking at desktop/gstreamer/0.10/default-elements
As for gstreamer 1.0, I have no idea how to control the default sinks. Knowing GNOME devs and their aversion to giving users options, I wouldn't be surprised if default sinks were autodetect only.

---

