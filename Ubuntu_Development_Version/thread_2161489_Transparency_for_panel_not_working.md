---
title: "Transparency for panel not working?"
date: 2013-07-10
forum: Ubuntu Development Version
---

### Post by loukingjr on 2013-07-10
I have Ubuntu 13.10 installed as a guest in VirtualBox. I notice I can't make the panel transparent with Ubuntu Tweak Tool or CCSM or whatever. Any thoughts?

---

### Post by mc4man on 2013-07-10
Well, you can make it transparent but it's quite possible that you won't want to do that due to this open, unconfirmed  bug, started in raring - 
[lpbug]1171658 [/lpbug]
Basically you have to enable a custom  Background Color which is done by raising _it's opacity setting to any value above 0_

But because the panel is now affected by the  Dash's opacity  setting, to have a transparent panel the Dash will also be trans or nearly so. Plus the Launcher & Panel will now use the Background Color you've chosen. That sometimes produces good results though often is terrible.

(you can leave the custom color @ #000000 if that fits your Desktop background.

Here I used to use a fully trans panel but now go with background of black, opacity set fairly high, 170+, panel opacity of 0, launcher opacity here or there... & no blur

If you fool around you may find something suitable, maybe even with a trans panel
(most custom colors tried here seemed too 'flat', have only really used black or a single r or b, no blur is a bit better  on older hardware, not an issue for you.

---

### Post by loukingjr on 2013-07-11
thanks. I'll give it a try.

---

