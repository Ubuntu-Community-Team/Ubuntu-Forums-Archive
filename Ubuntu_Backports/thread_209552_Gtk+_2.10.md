---
title: "Gtk+ 2.10?"
date: 2006-07-05
forum: Ubuntu Backports
---

### Post by andrewski on 2006-07-05
GTK+ 2.10 was [just released]("http://www.gtk.org/gtk-2.10-announcement.html") and I was wondering if it'd be suitable for a backport into Dapper.  I know that not all applications would take advantage of its features, but it is binary- and source-compatible with 2.8 thusly should have no problem with stability.

By the way, 2.10 is not yet in Edgy, but of course I'd be golden even if it was backported after it made it in.

---

### Post by FredB on 2006-07-06
Gtk 2.10.x will be in Edgy final. But backported to Dapper ? Until there is no critical software working only with gtk 2.10... :)

---

### Post by MadMan2k on 2006-07-06
applications would need to be recompiled/ updated for the new features in gtk 2.10, so: no.

---

### Post by FredB on 2006-07-06
Dapper is set to be 3 years long supported on Desktop. So a backport is still possible. Only time will tell. But I think I will be on Edgy right after RC release ;)

---

### Post by andrewski on 2006-07-06
[quote=MadMan2k]applications would need to be recompiled/ updated for the new features in gtk 2.10, so: no.[/quote] Are you sure?  The idea of being binary- and source-compatible, AFAIK, is that this would _not_ need to happen.

---

### Post by mlind on 2006-07-06
I reckon it's binary compatible with older versions, it wouldn't make much sense
otherwise. Wait until it gets packaged on Edgy, or Debian upstream.

---

### Post by MadMan2k on 2006-07-07
> **andrewski said:**
> Are you sure?  The idea of being binary- and source-compatible, AFAIK, is that this would _not_ need to happen.
it is - the recompile is only needed for the *new* features. I just wanted to point that backporting gtk2.10 alone will not change anything...

---

### Post by andrewski on 2006-07-07
> **MadMan2k said:**
> it is - the recompile is only needed for the *new* features. I just wanted to point that backporting gtk2.10 alone will not change anything...
...except for global support for color schemes, bugfixes, etc.

---

### Post by MadMan2k on 2006-07-07
> **andrewski said:**
> ...except for global support for color schemes, bugfixes, etc.
you forgot *new* bugs. and coloshemes require recompiling of the theme engines.

---

