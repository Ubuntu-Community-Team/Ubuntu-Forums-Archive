---
title: "Lost volume control"
date: 2014-01-06
forum: Ubuntu Studio
---

### Post by dmtparker on 2014-01-06
I tried posting this in the general forum, but think I did it wrong. I will delete it there and post here which is probably more appropriate.

Upgraded to 13.10 of Ubuntu Studio. The volume control disappeared. I've  seen lots of post about this in many different upgrades, but can't find  a solution. I have the "indicator plugin" displayed, but where the  volume contorl should be, there is just a blank monitor (like it shows  in the drop down menus when a menu item isn't really there.) Now, Pulse  Audio Volume Control is installed and works fine, but I miss my systray  control. I'm sure it is easy to get it back, I just cannot figure out  HOW?

---

### Post by Toz on 2014-01-06
It sounds like you are suffering from [this bug]("https://bugs.launchpad.net/ubuntu/+source/indicator-sound-gtk2/+bug/1208204"). See [comment #27]("https://bugs.launchpad.net/ubuntu/+source/indicator-sound-gtk2/+bug/1208204/comments/27") for a workaround. It looks like the bug will be properly fixed for 14.04.

---

### Post by cub on 2014-01-08
> **Toz said:**
>  It looks like the bug will be properly fixed for 14.04.
Yup, installed a fresh 14.04 yesterday and the bug is fixed there.

---

### Post by dmtparker on 2014-01-08
That worked. Thanks

---

### Post by chua on 2014-04-27
was having the same problem.
then i did this to bring it back.

sudo apt-get install unity-control-center

---

