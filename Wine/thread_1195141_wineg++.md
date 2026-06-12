---
title: "wineg++"
date: 2009-06-23
forum: Wine
---

### Post by wbest on 2009-06-23
Can somebody explain to me, what wineg++ is, and where/when I use it?
I'm a little unclear about the man page's explanation (what's MinGW?).
Does it still have all the same options as vanilla g++, like -I?  The man page seems to say that, but I want to make sure.
Is it really a version of g++ or is it used in make files and stuff?
Do I run it in Wine, or Terminal?  Neither seems to have worked for me so far.
 
Pardon any spelling mistakes, the spell check is not working right in this forum for me (I can't install anything, as I'm at work)...plus I'm a little tired right now...I should probably get a coke or lunch or something.

---

### Post by cogadh on 2009-06-24
Wineg++ is a compiler wrapper that is for taking Win32 source code and compiling it with WineLib to create a Linux binary that should run natively on a Linux system (in theory). Unless you are trying to compile Win32 source code into a Linux compatible form, you shouldn't need to do anything with it ever.

MinGW is basically a Windows port of GCC and Binutils.

---

