---
title: "Problem importing audio rosegarden / sox"
date: 2009-06-13
forum: Ubuntu Studio
---

### Post by jjsh on 2009-06-13
I've just installed Ubuntu Studio 9.04, then Rosegarden.

When I try to drop a wav file into a track, it says that it can't convert it, which ties in with a warning that sox isn't present as a helper program when Rosegarden starts.]

Typing 'sox' in a console suggests that it's there on my system, as it comes up with all the switches.

What do I need to do to get this working?

Many thanks

---

### Post by loudness on 2009-06-14
You need this patch:

[http://rosegarden.svn.sourceforge.net/viewvc/rosegarden?view=rev&revision=9677](http://rosegarden.svn.sourceforge.net/viewvc/rosegarden?view=rev&revision=9677)

  -loudness

---

### Post by Oasu4g on 2010-01-02
How do you install it?

---

