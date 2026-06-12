---
title: "How can I get cairo clock set up?"
date: 2006-04-10
forum: The Cafe
---

### Post by ezphilosophy on 2006-04-10
I asked mcduck about his clock and he mentioned that it is cairo clock.

[http://ubuntuforums.org/showthread.php?t=153312&page=2]("http://ubuntuforums.org/showthread.php?t=153312&page=2")

But, when I ./configure, I get this:

> checking for GTK_DEP... configure: error: Package requirements (cairo >= 1.0.0
         pango >= 1.10.0
         pangocairo >= 1.10.0
         libglade-2.0 >= 2.5.1
         librsvg-2.0 >= 2.13.91) were not met:

Package libglade-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libglade-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libglade-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_DEP_CFLAGS
and GTK_DEP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I do indeed have libglade-2 and librsvg-2 but the latter can't be upgraded to >= 2.13.91 in the repos.

I don't have a whole lot of experience with the make utility and hope to get some input.  :-|

---

### Post by 23meg on 2006-05-08
You seem to be using Breezy; you need to be running Dapper to meet its dependencies.

---

