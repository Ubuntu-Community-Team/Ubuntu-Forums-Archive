---
title: "synaptic progress indicator fails/false-flag"
date: 2012-06-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-06-28
This is the second time this has happed on two different installs. Synaptic stops showing progress in the progress dialog box but it still installing updates in the background, then fails on a compiz pkg and is corrected after hitting <apply> after  closing error box.

dpkg: dependency problems prevent configuration of rhythmbox:
 rhythmbox depends on libmusicbrainz5-0; however:
  Package libmusicbrainz5-0 is not installed.
 rhythmbox depends on gir1.2-rb-3.0 (= 2.97-1ubuntu1); however:
  Version of gir1.2-rb-3.0 on system is 2.96-0ubuntu4.
dpkg: error processing rhythmbox (--configure):
 dependency problems - leaving unconfigured

---

### Post by mc4man on 2012-06-29
the compiz-gnome thing is just one of those things - libcompizconfig0 needed to be updated before compiz-gnome, synaptic, (apt) wasn't doing it that way

---

### Post by ventrical on 2012-06-29
Ahh... thanks mac ! :)

---

