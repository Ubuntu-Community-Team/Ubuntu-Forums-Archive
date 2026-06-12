---
title: "QT Creator and adding Libraries"
date: 2014-05-22
forum: Ubuntu Application Development
---

### Post by atsmith6 on 2014-05-22
Hi

If I've posted to the wrong forums please accept my apologies.  I'm new here.

My question is related to using QT Creator 3.0.1 using QT 5.2.1 in Ubuntu 14.04, i.e. the default as installed by the software centre.

When I create new C++ Library (New Project... , Libraries , C++ Library), then a C++ executable project with (New Project... , Application , QT Console Application), and then attempt to add the library to the project with Right Click, Add Library, Internal Library the library dropdown is empty and doesn't allow me to choose any library in my build tree.

I've tried saving a custom session and I've ensured that I've build everything in both debug and release. I've tried this with both static and dynamic libraries.  As a work-around I am able to add the library, after building it, as an external library but I want to add it as an internal library properly so that the build dependencies are handled correctly.

If anyone can point out what I'm missing or doing incorrectly I'd highly appreciate it.

Kind Regards


Anthony

**[COLOR="#0000FF"]EDIT[/COLOR]: I've found the answer and update here for anyone new to Qt Creator who has the same problem.  You need to create a "Subdirs" project as a parent to the application and library projects.  These sub-projects can then see each other and refer to each other as needed.**

---

