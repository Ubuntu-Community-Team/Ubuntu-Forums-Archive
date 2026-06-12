---
title: "What are &quot;-dev&quot; files?"
date: 2009-09-12
forum: Ubuntu Dev Link Forum
---

### Post by J05HYYY on 2009-09-12
What are -dev files (or development files)?
If I compile and install from source will these files be installed automatically - so I can develop the software anyway?
Couldn't find a real description anywhere.

---

### Post by lloyd_b on 2009-09-13
> **J05HYYY said:**
> What are -dev files (or development files)?
If I compile and install from source will these files be installed automatically - so I can develop the software anyway?
Couldn't find a real description anywhere.
If you mean the "...-dev" packages, these contain the various development files (mostly .h header files, but many other odds and ends as well) needed to compile programs to use the associated package.

For instance, "libglib2.0" is normally installed automatically when the system is installed, and it allows you to run programs that use the Glib library.  But if you wish to compile programs that use Glib, then you need to install "libglib2.0-dev".

As a rule, if you build from source, when you do the "make install" stage it will install any header files associated with the program/library that you are compiling.  But this is *not* guaranteed - it depends on how the maintainer has set things up in the "makefile".  You'll need to read the documentation for the program/library in question to be certain.

Lloyd B.

---

