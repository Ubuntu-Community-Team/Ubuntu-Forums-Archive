---
title: "Why don't more programs use the native help viewer?"
date: 2012-09-18
forum: The Cafe
---

### Post by dericke on 2012-09-18
From my limited (non-developer) understanding, writing documentation in DocBook, LaTeX, etc., makes it easy to build the same content into multiple formats. To me, this should make it really simple for a cross-platform project like LibreOffice or GIMP to provide documentation in each platform's native viewer--Yelp for GNOME, and whatever the KDE, Mac, Windows, etc. viewers are, with HTML files for those platforms that don't generally use such a program (XFCE?) Yet, neither LO nor GIMP use the native viewers, and instead have their own, independent help viewers. Heck, even Abiword , a GNOME application, uses plain HTML files instead of GNOME's own help browser (at least, this is true for the current version in Precise)

To me, this is a) a loss for usability, since I believe users should have a single source of first resort for documentation, and b) a waste of development hours. But again, I'm not a developer. So was it really easier for developers to write a new, cross-platform help viewer instead of documentation for existing browsers, or did they need some feature for their docs that isn't provided in a native viewer?

---

### Post by BrokenKingpin on 2012-09-20
Simply because it is less work for them as they do not need to handle 50 different scenarios, where doing their own once gets the job done.

With things not being standard across distros/OSs, it makes a lot of sense for cross-platform apps to just roll their own, which keeps it self contained.

---

