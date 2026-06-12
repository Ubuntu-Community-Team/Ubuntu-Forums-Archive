---
title: "vmplayer and virtualbox recently stopped working"
date: 2013-04-20
forum: Virtualisation
---

### Post by kelargo on 2013-04-20
some upgrade took place this past week and neither virtualbox or vmplayer work. as soon as i try to start a VM the crash is fanstastic. I'm kicked out of xfce session and have to log back in. 
This worked two weeks ago.. any suggestions on what to look for to troubleshoot?

---

### Post by jejeman on 2013-04-20
See if X server is crashing. Look in Xorg.0.log & Xorg.0.log.old.
Also look in dmesg to see if anything segfaults.

---

### Post by wildmanne39 on 2013-04-22
*Thread moved to **Virtualisation**.*

---

