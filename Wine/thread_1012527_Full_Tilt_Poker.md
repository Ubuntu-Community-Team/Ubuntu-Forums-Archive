---
title: "Full Tilt Poker"
date: 2008-12-15
forum: Wine
---

### Post by Bakon Jarser on 2008-12-15
I had no text in wine and the solution in the faq is to add this line to the registry:

[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"

This breaks Full Tilt Poker. No images are displayed now, including cards. But without that in the registry I get no text which is equally bad. The error message in the terminal is:

fixmerender:X11DRV_AlphaBlend Unable to AlphaBlend without Xrender

I'm using Ubuntu 8.10 with wine 1.1.10.

The no text bug is not in ubuntu 8.04 so I may have to switch back. Does anyone have any ideas?

---

### Post by Bakon Jarser on 2009-01-01
Still broken with wine 1.1.11.

Also I think this is only a problem with the nvidia 96 driver.  Is there a beta version of this driver that I can try?

---

### Post by Bakon Jarser on 2009-01-03
Still have this problem with 1.1.12

---

