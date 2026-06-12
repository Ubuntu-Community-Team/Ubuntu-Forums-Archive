---
title: "fonts in ubuntu"
date: 2007-03-14
forum: The Cafe
---

### Post by karellen on 2007-03-14
I can't call it a real problem, but more likely kind of a personal dissatisfaction: why the fonts in ubuntu don't look so good like the ones in certain windows applications? for example...in xp I use office 2007, and I love what it does with fonts. I have there fonts like "calibri" or "segoe ui" that look smooth and polished and I really like them...in ubuntu I use evolution, firefox and so on, but the fonts in evolution can't compete with the ones in outlook 2007...:(. I've tried many work-arounds: installed msttcorefonts, used anti-aliasing....but no, still it's not the same. maybe it seems like a childish problem, but for me it's important how it looks when I write and e-mail or a document....I know they are proprietary closed fonts...but this doesn't make me feel better :(. I was curious: does anybody around here have the seem issue with fonts like I do? what's your opinion

---

### Post by silhouette on 2007-03-14
Well, Ubuntu (and Linux in general) use a different way to render fonts than Microsoft does, due to copyright/licensing issues, so there's no way to get them looking exactly like they do in Windows. However you can come pretty close, or even better IMO. I've found that following the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=235526) improve fonts immensely (note that it says it applies mainly to LCD monitors, but I'd think it'd work on CRT monitors too, if that's what you have). Note that after you install the packages and run "dpkg-reconfigure fontconfig" you must restart X to see the changes. Before you do so it's probably a good idea to check System > Preferences > Font and experiment with hinting. "Slight" or "Medium" works best.

Calibri is a Windows Vista font and can be downloaded [here](http://jeffmilner.com/index.php/2005/07/30/windows-vista-fonts-now-available/) along with other Vista fonts.

---

### Post by karellen on 2007-03-14
thanks :), I'll try and see what I can do. probably install the fonts from the second link as I don't have LCD monitor nor CRT with Trinitron

---

