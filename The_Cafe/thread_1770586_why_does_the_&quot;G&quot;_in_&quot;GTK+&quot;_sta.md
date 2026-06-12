---
title: "why does the &quot;G&quot; in &quot;GTK+&quot; stand for GIMP and not GNOME?"
date: 2011-05-29
forum: The Cafe
---

### Post by u-noob-tu on 2011-05-29
i just found out that GTK+ actually means "GIMP Tool Kit", and not "GNOME Tool Kit". why is that?

---

### Post by el_koraco on 2011-05-29
Because it was originally created for Gimp, which stands for Gnu Image Manipulation Program, so I guess it would have been redundant to do a double Gnu.

---

### Post by Tibuda on 2011-05-29
Because the toolkit was created for GIMP before Gnome existed.

"GTK+ was initially created for the GNU Image Manipulation Program (GIMP), a raster graphics editor, in 1997 by Spencer Kimball and Peter Mattis, members of eXperimental Computing Facility (XCF) at University of California, Berkeley."
[http://en.wikipedia.org/wiki/Gtk](http://en.wikipedia.org/wiki/Gtk)

---

### Post by koleoptero on 2011-05-29
What makes you think that gnome is the only GTK+ based desktop environment?

---

### Post by Tibuda on 2011-05-29
> **koleoptero said:**
> What makes you think that gnome is the only GTK+ based desktop environment?

That's like asking what makes you think that GIMP is the only GTK+ based application?

---

### Post by Lucradia on 2011-05-29
> **Tibuda said:**
> That's like asking what makes you think that GIMP is the only GTK+ based application?

Plus One.

Pidgin is also GTK+ Based. XFCE is GTK+ for inside the windows.

GTK, however, does *not* pull gnome depends. Pidgin only pulls gconf because it gets proxy info from there. Ayttm, on the other hand, does not. However, ayttm is very out of date in ubuntu releases, and there is no PPA for ayttm.

---

### Post by Artemis3 on 2011-05-29
Gimp: 1996
Gnome: 1999

Gnome used Gimp's toolkit, not the other way around.
As others said, many more programs also use Gimp's toolkit, without any gnome dependencies.

In 1996, available free widgets were limited, and often authors decided to invent their own rather than use a commercial one. gtk is one of those that became more popular, at least before the qt license became friendlier. Oh and before you ask:

Qt: 1992
Kde: 1996

I hope you can already guess that programs using QT don't need to involve KDE for anything...

---

