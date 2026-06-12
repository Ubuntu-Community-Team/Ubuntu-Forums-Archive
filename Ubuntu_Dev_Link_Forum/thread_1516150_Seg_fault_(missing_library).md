---
title: "Seg fault (missing library?)"
date: 2010-06-23
forum: Ubuntu Dev Link Forum
---

### Post by aosmith on 2010-06-23
Hey guys I'm getting a segmentation fault when I run some code that was re-factored from windows, it uses some advanced math (trig functions to be exact) so I have to compile with the -lm flag.  I have a feeling that I am missing a runtime library or something along those lines.  Any ideas?

---

### Post by MindSz on 2010-06-24
What language are you using?

In C, you need to include the 'math.h' library and then compile with the -lm option.

---

### Post by vikas.sood on 2010-07-26
use ldd to find what libraries are missing.

---

