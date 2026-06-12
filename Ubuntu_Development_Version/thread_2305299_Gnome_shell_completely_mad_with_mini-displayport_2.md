---
title: "Gnome shell completely mad with mini-displayport 2nd monitor"
date: 2015-12-04
forum: Ubuntu Development Version
---

### Post by fthx on 2015-12-04
Hi,

I do not experience issues with VGA (projector at work) but I do not manage to get working my 2nd monitor (mini-displayport dongle, to DVI or HDMI).
Gnome shell is flickering, activating and deactivating continuously the 2nd monitor. No success with the special key designed to change monitors settings.

I checked with the previous 4.3 kernel or the old 4.2 latest xenial kernel : same behaviour.
Maybe due to the latest mesa update ? (Don't hurt me if I'm wrong !)

Do you experience the same issue ?

---

### Post by QDR06VV9 on 2015-12-04
If you are talking about the flickering and tearing I too see that until I open some thing up IE: A file manager or a player or any app then all is good.
My two monitors are a 23" HP w2338h and Vizio 30" TV HDMI
Regards

---

### Post by fthx on 2016-02-03
Bump !
Still buggy ! With DVI I can obtain an extended display but not with HDMI. Furthermore, with DVI, Gnome does not give the right resolution (e.g. 1600 x 900 for my 2nd monitor instead of full HD, or full HD instead of 1600 x 900 for my laptop's screen, etc.).

I really want to make a bug report, but I do not know against what package : X (Intel's driver was updated yesterday with no effect), kernel, gnome shell (Apport show GS errors after plugin HDMI) ?

Thanks !

---

### Post by tista on 2016-02-03
@fthx,

I think you can file a launchpad bug report related to just **Gnome-Shell** only... Devs (or other people) may find which codes were "truly" related to this issue even if it will need a bit more time to track this issue down... Anyway nice findings and trials... :)
Unfortunately I have not any external displays connected via mini-displayport/DVI cable though...

Regards.
Tista

---

### Post by dino99 on 2016-02-04
Try to grab some usefull warnings/errors via journalctl/lshw/dmidecode (some hardware might be wrongly identified, or not identified at all) (possibly a kernel problem, but are intel-gpu-tools / intel-microcode installed ?)

---

