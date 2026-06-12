---
title: "System crash at startup on Starling"
date: 2013-05-22
forum: System76 Support
---

### Post by fredsea on 2013-05-22
I was half-hoping that this issue would eventually go away with an Ubuntu upgrade, but it's ben persistent throughout my Starling's life. Mind you, the netbook is great: it does everything I need (sometimes at a slow pace, but I am not at the races), and is light and easy to carry around. So, it's annoying that every time it boots, I get a crash report ("something crashed or crashed in the past", but no way to know what it is that crashed, at least from the crash report I can see). Nothing seems to be affected by this crash, and I recall somebody posting a script a long time ago, to block the reports (not the crash itself), since it didn't seem to affect anything anyway. In other words, I live with this "feature" without trouble, but I still wonder if there is a way to fix this thing, whatever it may be.

By the way, I am running LXDE right now, but this constant crash-at-boot has been happening with other desktops as well.

Thanks. :confused:

---

### Post by hansdown on 2013-05-22
Hi 
fredsea.

I routinely check out mosy versions, and it does happen with all of them.

A quick fix was posted for ubuntu 11.04.

It works for newer versions.

[https://eebrinker.wordpress.com/2011/04/23/solution-crash-report-that-crashes-ubuntu-11-04/](https://eebrinker.wordpress.com/2011/04/23/solution-crash-report-that-crashes-ubuntu-11-04/)

---

### Post by isantop on 2013-05-23
These sorts of "micro-crashes" are actually extremely common, and in almost all cases, the system can (and does) recover automatically. In recent versions of Ubuntu, the system no longer blocks the error messages (which it used to do).

There should be an option to "Ignore future crashes of this program version". If you check that, uncheck report, it should hide the messages until the package causing it is updated (As a quick fix).

---

