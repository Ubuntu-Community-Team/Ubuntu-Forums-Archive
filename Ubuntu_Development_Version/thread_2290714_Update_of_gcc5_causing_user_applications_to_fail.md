---
title: "Update of gcc5 causing user applications to fail"
date: 2015-08-14
forum: Ubuntu Development Version
---

### Post by crcarson on 2015-08-14
This is really a continuation of the post by syntaxerror74 ("V5" mass-update of libraries....) but as a casual application programmer I wanted to more clearly state the problem as I see it.

After an Update a couple of days ago where the gcc libraries were updated with V5 my user application using gtkmm/mysql failed to run (segment exceptions).  Thinking since the compiler was updated, I need to recompile to get around the error.  The compile was OK but the link to the library routines failed with "undefined referenced" to such items as Glib::ustring::ustring.  Not knowing if this was my problem (miss use of code exposing a problem on the new environment) I change the code many times but couldn't get around the link errors.  Found some info indicating that you need to compile with the -D_GLIBCXX_USE_CXX11_ABI=0 to force the compiler to use the old libraries.  Have tried this and it seems to help but the link is still failing on some string calls from mysql++.  Not sure at this time I have to wait for mysql to update their component or there is some other compiler/linker options I need to add to get my applications working again.

---

### Post by crcarson on 2015-08-17
Checking after each apt-get Update and found today the link errors returned even tough had -D_GLIBCXX_USE_CXX11_ABI=0 specified on the compile.  Removed the -D parameter and now I get a complete compile/link and the application runs as expected.

---

