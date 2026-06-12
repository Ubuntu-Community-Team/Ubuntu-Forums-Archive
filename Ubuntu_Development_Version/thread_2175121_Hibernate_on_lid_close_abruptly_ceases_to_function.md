---
title: "Hibernate on lid close abruptly ceases to function"
date: 2013-09-17
forum: Ubuntu Development Version
---

### Post by ooddiittyy on 2013-09-17
I have a problem with hibernate functionality on a Sony Vaio Pro 13; via editing of polkit-1 files in /etc/ and /var/ (referenced in a number of other forum posts), I was able to get hibernate working on lid closure just fine, although I was never able to get it to show up as an option in the power menu on the desktop (perhaps due to interplay between the /var/ and /etc/ hierarchies?). Recently, however, I started up the laptop and noticed that the "hibernate" option is missing from the drop-down menu under "When lid is closed" on battery, where it once existed. What's strange is that a) it reverted without apparent cause and b) the "hibernate" option is still listed under "When power is critically low", so it's not as if the system has no reference to it whatsoever. I have also now tried modifying the /var/lib/../10-vendor.d/com.ubuntu.desktop.pkla file (based on yet another post) to no avail.


I'm on 13.10, pm-hibernate works fine and like I said, until today the fixes mentioned earlier worked like a charm. I have very minimal experience with Linux in general, and any help would be most appreciated.

---

