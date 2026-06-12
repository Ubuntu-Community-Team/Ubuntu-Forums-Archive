---
title: "Graphical glitches/artifacts?"
date: 2014-02-21
forum: Ubuntu Development Version
---

### Post by 3vi1 on 2014-02-21
Has anyone noticed any graphical glitches in the last few days, particularly with Intel HD4000 chipsets?

I generally use KDE as my desktop, so it's not impossible that these are new bugs there... though I've seen corruption in the URL bar of chrome which should be immune from kde-specific bugs.

When running apps like Dolphin and dragging the window around, I occasionally see some white blocks around the edges.

If not for the fact that booting from an older live image shows no issues, I'd think I developed hardware issues.  In just the last day, primusrun has stopped working too (it now produces solid black windows, though the apps appear to be running), while optirun (virtualgl bridge) still works.

---

### Post by 3vi1 on 2014-02-21
**Update:**  Decided to test by upgrading my graphics libs to what is in xorg-edgers, and...

ALL PROBLEMS GONE!  Even primus is now working properly.  Whew... not a hardware issue.  Looks like there might be some bugs in one of the libs pushed to trusty in the last few days.

**UPDATE:**  Problems returned when edgers updated their mesa/intel packages the next day.  :(  Backleveled to Saucy mesa, and intel driver from 2/10 to work around the issue.

---

