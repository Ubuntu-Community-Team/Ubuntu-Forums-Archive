---
title: "Compiling Python apps for windows with py2exe"
date: 2008-12-29
forum: Windows
---

### Post by dodle on 2008-12-29
I am trying to make an application for windows using python & py2exe.  Creating the application isn't a problem, my goal is to make the app look for the python.dll in a directory other than the executable's.  For example: I have python25.dll in C:\Windows.  If I compile the program with py2exe(excluding python25.dll), then try to run the executable I get the following error:
> The specified module could not be found.
LoadLibrary(pythondll)failed
Does anybody have any idea how to make my app look for python25.dll in C:\Windows?

---

### Post by Grant A. on 2008-12-29
nevermind.

---

