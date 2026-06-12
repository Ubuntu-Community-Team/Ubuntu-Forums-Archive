---
title: "Can we turn off the average background colour?"
date: 2012-03-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by snkiz on 2012-03-28
For Unity 2D and notify-osd. Its neat and all but I think I liked it better black. The average colour thing tends to pick up the contrast colour in most of my backgrounds. Looks horrible. Please developers add a dconf setting to turn it off.

---

### Post by bovender on 2012-03-29
+1

It does not look particularly nice... Especially the notify-osd should have the same color as the top bar (again).

---

### Post by bluebyt on 2012-03-30
I hope also, that we have an option to turn that thing off!

bluebyt

---

### Post by jbicha on 2012-03-30
I've never tried it but have you looked at com.canonical.unity-2d average-bg-color in dconf-editor?

---

### Post by mc4man on 2012-03-30
> **jbicha said:**
> I've never tried it but have you looked at com.canonical.unity-2d average-bg-color in dconf-editor?

That value in a unity 2d session will affect the Dash & launcher though not the osd notifications (unlike unity-3d where I don't think the settings matters anymore or atm

If will reset on login though I guess if one liked a different value than what is produced they could set to it thru a start up script/command

If wanting a nice almost black osd then the best one was produced by the next to last notify-osd package.
It was the first to "change background colour to use the same median colour used in the unity dash" except it didn't work quite right & produced a  dark, almost black color.

The package is here & still could be considered for use by many, contains all of the recent bug fixes excluding a dual screen one

[https://launchpad.net/ubuntu/+source/notify-osd/0.9.33-0ubuntu1](https://launchpad.net/ubuntu/+source/notify-osd/0.9.33-0ubuntu1)

---

