---
title: "Clock 2.12.1"
date: 2006-01-04
forum: The Cafe
---

### Post by madebyjerry on 2006-01-04
I have been searching around to find how to change format from:

weekday, date month, time

to:

weekday, month date, time

I've tried dpkg-reconfigure locales to no avail.

I'm just learning to use Ubuntu, so assistance would be appreciated.

Jerry

---

### Post by bjourne on 2006-01-07
AFAIK, sadly you can't. The date format is hardcoded in the clock applet.

---

### Post by glotz on 2006-03-26
We just switched from daylight savings time to standard time. The Clock 2.12.1 updated itself via NTP but didn't notice the user of this change. I think it would be very handy and indeed needed feature to remind users of this fact. Also people are used to this on windows.

---

### Post by tageiru on 2006-03-26
I found a patch on the gnome bugzilla a while ago that did this. It lets you specify the format of the clock in html in a gconf string.

[http://bugzilla.gnome.org/show_bug.cgi?id=332737](http://bugzilla.gnome.org/show_bug.cgi?id=332737)

---

