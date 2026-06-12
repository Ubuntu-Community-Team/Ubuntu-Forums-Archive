---
title: "Scala22 in 11.10 - error"
date: 2011-12-28
forum: Ubuntu Studio
---

### Post by 3w4v on 2011-12-28
When attempting to start Scala I get the following error:

```
GThread-ERROR **: file /build/buildd/glib2.0-2.30.0/./gthread/gthread-posix.c: line 348 (g_thread_create_posix_impl): error 'Invalid argument' during 'pthread_attr_setschedparam (&attr, &sched)'
Trace/breakpoint trap

```The Linux documentation is unclear. Under the Windows documentation is the following, which may or may not be related:

"If you get an error message about a missing entry point of libglib-2.0-0.dll,
or other error messages about dlls, your Gtk+ version is too old, or the PATH 
(environment variable) does not contain the location of the Gtk+ runtime
library. To check this, open the Windows Command Prompt and type "path" 
followed by Enter. It's also possible to have a conflict with another 
installed application that also uses Gtk+. In general it's best to have the
Gtk+ runtime library path at the beginning of the PATH variable. The Gtk+
installer puts it at the end however."

I know further that Scala is written in Ada and uses GtkAda, if this makes any difference. Scala is not available through the repositories - I downloaded the 64 bit Linux package from [the Scala website]("http://www.huygens-fokker.org/scala/downloads.html").

I appreciate any help solving this problem.

---

