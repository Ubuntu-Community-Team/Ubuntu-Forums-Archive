---
title: "compiz refresh rate keeps resetting itself to 50"
date: 2013-04-22
forum: Ubuntu Development Version
---

### Post by Gnobody on 2013-04-22
My compiz refresh rate keeps resetting itself to 50 after a reboot, this causes visibly choppiness especially in games.

---

### Post by Gnobody on 2013-04-22
> **Gnobody said:**
> My compiz refresh rate keeps resetting itself to 50 after a reboot, this causes visibly choppiness especially in games.


I'm trying to employ my own work around by using a startup script ```
gsettings set org.compiz.profile:/unity/plugins/composite refresh-rate 200
```  which isn't working I have to either make the change in dconf-editor or compiz config settings manager.

---

### Post by Gnobody on 2013-04-22
[https://bugs.launchpad.net/compiz/+bug/1027868](https://bugs.launchpad.net/compiz/+bug/1027868)  I've followed a work around mentioned in the report by a fellow user but this a major bug that shouldn't have made it into the final release.  How are new users supposed to game on this OS if the performance is choppy by default?

---

### Post by dino99 on 2013-04-23
well, you need to pay attention to:
- the kernel itself : how fast can he handle rates ?  Do you use the "rt" kernel ?
- the graphic system (card/chipset) : how high can you push rates ? (see docs)
- and finally for displaying: is your LCD/screen able to handle high rates ? with which definitions ?

Glancing at dmidecode outputs might help.

note: compiz itself is only maintaining the "critical" issues, as that project is deeply redefined/rewritten with qt/been replaced by mir/unity-next in the near future release

---

### Post by bird1500 on 2013-04-23
- Gee, the kernel doesn't need "rt" to handle rates > 50
- almost every card can handle this, if the OP reported this I'm sure he's not running legacy hw.
- LCDs are designed around 60 FPS, regardless the graphics driver should have a setting for that, e.g. for benchmarking purposes.

---

### Post by Gnobody on 2013-04-24
This issue is a regression, it wasn't an issue in 12.10 because Compiz could detect the refresh rate.  AFAIK 50Hz is a legacy PAL standard that isn't even used in Europe anymore so this default setting makes no sense whatsoever.

---

