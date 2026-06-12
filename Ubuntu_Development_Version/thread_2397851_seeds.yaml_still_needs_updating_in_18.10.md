---
title: "seeds.yaml still needs updating in 18.10"
date: 2018-08-04
forum: Ubuntu Development Version
---

### Post by PaulW2U on 2018-08-04
I've just created bug report [#1785388]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1785388") in order to draw attention to the fact that if the current daily ISO is installed then the implication is that only one snap is available and that it won't be usable.

If seeds.yaml is re-ordered so that gtk-common-themes is initialised much earlier then a total of seven snaps will be available for use as follows:
```
paul@N1642~/D/Ubuntu> snap list
Name                  Version    Rev   Tracking  Publisher  Notes
core                  16-2.33.1  4917  stable    canonical  core
gnome-3-26-1604       3.26.0     70    stable/…  canonical  -
gnome-calculator      3.28.2     180   stable/…  canonical  -
gnome-characters      3.28.2     103   stable/…  canonical  -
gnome-logs            3.28.2     37    stable/…  canonical  -
gnome-system-monitor  3.28.2     51    stable/…  canonical  -
gtk-common-themes     0.1        319   stable/…  canonical  -
```
I'm not sure why we're seeing little progress with bug [#1772844]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1772844") but it seems to be now related to just 18.04. I'm not seeing that the issue has been fixed in cosmic as the bug report implies.

I've also logged this bug report on the ISO tracker.

---

### Post by P-I H on 2018-08-04
Added me to the bug report. I have the problem in the iso from 1/8 and 23/7.
Will check the iso from 4/8.

---

### Post by P-I H on 2018-08-04
The problem still exist in the 4/8 iso.

---

### Post by corradoventu on 2018-08-05
comment in [https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1772844](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1772844) says:
Indeed, fixed on 18.04 and broken on 18.10 is intentional, as the 18.04 "fix" was a horrible hack in livecd-rootfs to work around the bug in time for the point release, while I've been assured that 18.10 will get a proper fix in snapd instead.

---

### Post by PaulW2U on 2018-08-05
Yes, I saw that comment - added just a few hours after I created bug report [#1785388]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1785388") which is probably not needed now. I'll leave it to a developer to mark as a duplicate or whatever.

---

