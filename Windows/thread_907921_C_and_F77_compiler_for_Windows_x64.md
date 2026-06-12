---
title: "C and F77 compiler for Windows x64?"
date: 2008-09-02
forum: Windows
---

### Post by Erdaron on 2008-09-02
What I'm actually trying to do is install [NumPy]("http://numpy.org/") extension for Python. However, the available binaries don't seem to work on Windows XP x64, but source code is available and I'm trying to compile it myself. I've seen references to this, though no howtos or walkthroughs. NumPy compilation requires a C and F77 compiler.

I've been trying to read email lists and google for MinGW and NumPy on this, but everything is either a couple of years old, or involves messing with header files, which is well above my competence level.

There is a [64-bit version of MinGW]("http://sourceforge.net/projects/mingw-w64"), but I can't figure out how to use it. It seems to be just the libraries, not the compiler itself, but the project doesn't seem to be well documented.

I have tried installing 32-bit NumPy, but either the install fails, or importing the library fails. I've tried the most recent version (1.1.1) and the last stable version (1.0.4), both executable installers and MSI installers.

Am I missing something? Do these compilers come with Windows and I just don't know? Is there a workaround I didn't find?

---

### Post by LaRoza on 2008-09-02
> **Erdaron said:**
> What I'm actually trying to do is install [NumPy]("http://numpy.org/") extension for Python. However, the available binaries don't seem to work on Windows XP x64, but source code is available and I'm trying to compile it myself. I've seen references to this, though no howtos or walkthroughs. NumPy compilation requires a C and F77 compiler.

I can't help with your primary problem. You can, if you need to use this, use a virtual machine, unless you have to do this on the OS itself.

> 
Am I missing something? Do these compilers come with Windows and I just don't know? Is there a workaround I didn't find?
Windows doesn't come with compilers (it comes with script hosts for JScript and VBScript and .NET)

---

### Post by Erdaron on 2008-09-02
I would prefer to do this on the OS itself. This is not jeopardizing my work, as NumPy runs fine on my laptop (32-bit Windows) and in Ubuntu x64. It would be convenient to get it to work on XP x64 install, but not critical. So I can treat this as a learning experience.

The only compilers that are 64-bit that I could find are Intel's commercial compiler and MS VisualStudio, both of which are priced outside of my range.

It seems people have been trying to port MinGW to x64 since at least two years ago, shouldn't there be something that at least mostly works?

---

