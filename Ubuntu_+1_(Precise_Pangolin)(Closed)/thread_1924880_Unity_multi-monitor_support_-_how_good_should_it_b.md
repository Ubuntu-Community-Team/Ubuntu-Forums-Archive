---
title: "Unity multi-monitor support - how good should it be?"
date: 2012-02-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by prana on 2012-02-13
I tried it for the first time and found a (IMO) a serious issue with it. I thought there were some improvements to multi-monitor support in Unity 5.2.

You can read about the bug here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/931255](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/931255)

Here is my description from the bug report:

Running i386 12.04 fully updated.

This happened when I connected my laptop to an external display. After connecting, I tried to do the following:

a) The display dialog insisted that my laptop was to the right of the external display so I corrected it so that it was to the left of the display. I also made the external display the primary display.

b) Then I tried to switch to a different workspace. The display code then did the same thing as above and tried to make the laptop the primary display and keep it to the left of the external display. I corrected it again then gnome control center crashed.

---

