---
title: "C++ Compiler"
date: 2007-08-29
forum: Windows
---

### Post by warlorddagaz on 2007-08-29
I'm just beginning to learn C++, and I am not sure which compiler would be best to use.

I will mainly be writing for windows systems.

I have tried using cygwin and gcc, but my executables fail at runtime, needing the cygwin1 dll, which I would prefer not to need to distribute with my programs

As a keen supporter of open source software, I would prefer to use an open source compiler, but gcc has the above-mentioned problems.

I have just installed Microsoft Visual C++ Express edition, for it's compiler alone, but am unsure whether it would be better to use this or another compiler.

Any views, ideas ETC would be appreciated, but please bear in mind that I don't want an IDE - just a compiler

---

### Post by LaRoza on 2007-08-30
> **warlorddagaz said:**
> I'm just beginning to learn C++, and I am not sure which compiler would be best to use.

I will mainly be writing for windows systems.

I have tried using cygwin and gcc, but my executables fail at runtime, needing the cygwin1 dll, which I would prefer not to need to distribute with my programs

As a keen supporter of open source software, I would prefer to use an open source compiler, but gcc has the above-mentioned problems.

I have just installed Microsoft Visual C++ Express edition, for it's compiler alone, but am unsure whether it would be better to use this or another compiler.

Any views, ideas ETC would be appreciated, but please bear in mind that I don't want an IDE - just a compiler

Dev-C++, it is an IDE, but you don't have to use it.

[http://www.bloodshed.net/dev/devcpp.html](http://www.bloodshed.net/dev/devcpp.html)

Make a batch file, use your text editor to create a file named "cmd.bat", and add this, PATH=C:\Dev-cpp\bin.

Assuming that bin contains g++.

This way, you can use the page file to compile programs with g++, gcc, gdb, just like you would on Linux. The IDE, which I don't use, might be handy. I use Crimson Editor for code editing, you migh like that also.

You can also get Dev-C++ Portable, [http://sourceforge.net/projects/devcpp-portable/](http://sourceforge.net/projects/devcpp-portable/) so you can use it anywhere, of a flash drive.

---

### Post by warlorddagaz on 2007-08-30
Thanks - I'll give it a go

---

### Post by LaRoza on 2007-08-30
If you have an issue, let me know!

---

