---
title: "File Roller 2.11.1 backported"
date: 2005-05-27
forum: Ubuntu Backports
---

### Post by ow50 on 2005-05-27
File-roller has finally changed the "extract here" functionality.

Changes since the hoary version:
```
version 2.11.1
--------------
        * Do not create a _FILES folder anymore (#167261).
        * Allow to extract more archives at once.  Added an --extract-here
          command line option.
        * Use g_filename_display_name and g_filename_display_basename when
          appropriate.
        * Prevent renaming of files to silently overwrite other existing
          files (#168287).
        * Header cleanup (#171618).
        * Allow stock labels to show through, be nice to translators (#172867).

version 2.10.2
--------------
        * Fixed bug #300238: Unable to gunzip "gzip'd ubuntu mail archives".
        * Plugged a little memory leak related tooltips.
```
Backported from breezy.
In hoary-backports-staging/main/binary-i386/.

---

### Post by thechitowncubs on 2005-05-28
thank god

so much easier! great backport!

---

### Post by mariuss on 2005-07-08
[QUOTE=ow50]        * Do not create a _FILES folder anymore (#167261).
[/QUOTE]
I really, really, miss this feature! Is there a way to re-enable it?

Why on Earth was it removed?

Marius

---

### Post by Fluffy, the jolly sheep on 2005-07-09
I guess this kind of things depends on personal preference and the kind of archives you get to deal with. Personally, I like it better without this feature. You can read some discussion on why it has been changed back in the [bug report](http://bugzilla.gnome.org/show_bug.cgi?id=167261) and it's comments. If you'd like the old file-roller back, you can re-install the non-backports version in synaptic (package menu -> force version).

---

