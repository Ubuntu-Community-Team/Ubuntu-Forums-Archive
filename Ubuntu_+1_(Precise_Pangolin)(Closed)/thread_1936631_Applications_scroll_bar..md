---
title: "Applications scroll bar."
date: 2012-03-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Bobhuber on 2012-03-06
If I open up the dash in Unity and the applications lens and attempt to use the scroll bar (very thin white bar on the right) to find the app I looking for it closes the window or lens unless I'm extremely careful with the mouse. There is no wide scroll bar overlay as one would have in a normal window . Very annoying to say the least. Anyone else having this problem? I'm running inside Virtualbox so I hesitate to even try and report it as a bug.

---

### Post by dino99 on 2012-03-06
testing inside virtual system is quite useless, as a third app can disturb the processes.

---

### Post by mc4man on 2012-03-06
If you are using a left click & drag then it would appear you'd need to be very careful not to click in the 'border' area or the Dash will close
(scroll wheel or touchpad scroll area scrolling are obviously not affected

If this is your case then maybe a left click in the border area should not close the dash, a bug on that would seem reasonable

---

### Post by Bobhuber on 2012-03-06
> **mc4man said:**
> If you are using a left click & drag then it would appear you'd need to be very careful not to click in the 'border' area or the Dash will close
(scroll wheel or touchpad scroll area scrolling are obviously not affected

If this is your case then maybe a left click in the border area should not close the dash, a bug on that would seem reasonable
That's exactly what is happening. Anything on the border closes the window. I won't even get into the ridiculous statement by dino99  about vbox usage and testing being useless.
I've been testing and using Ubuntu on separate partitions and in Virtualbox for quite a few years.

---

### Post by grahammechanical on 2012-03-06
I usually use the scroll-wheel but you are right about the slimness of the slider. It is a design failure. There is a large enough gap between the edge of right hand column and the Dash border to allow that slider to be wider than it is.

Regards.

---

### Post by mc4man on 2012-03-06
The Dash will continue to use the overlay-scrollbar, no question there.
What could be though is whether the border is part of the Dash & clicking in will not close or the current where it does close.

So in that vein filed a bug directed towards Design, maybe they'll consider, maybe not. If so then they'll decide which way to go, ect.

[https://bugs.launchpad.net/bugs/948511](https://bugs.launchpad.net/bugs/948511)

---

### Post by mc4man on 2012-03-09
There was a Design bug on this some time ago - clicking on the border should not close the Dash

Was never fixed, maybe this time around
[https://bugs.launchpad.net/ayatana-design/+bug/839472](https://bugs.launchpad.net/ayatana-design/+bug/839472)

---

