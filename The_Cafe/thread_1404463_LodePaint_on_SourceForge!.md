---
title: "LodePaint on SourceForge!"
date: 2010-02-11
forum: The Cafe
---

### Post by Zeemvel on 2010-02-11
Hi, I'm making a painting program, called "LodePaint". Its features are currently somewhere in between KolourPaint and Gimp.

And I put it on SourceForge now, to try to make it an actual real life project instead of something sitting on my harddisk that only I know about.

[https://sourceforge.net/projects/lodepaint/](https://sourceforge.net/projects/lodepaint/)

You can download it both as binary or as source code from SourceForge, whichever suits your preference the best (see the compilation instructions text file for compiling it since there's no makefile yet).

What do you think of the program? And could the project have any future?

P.S. You need 3D hardware acceleration, unfortunately it won't work with software OpenGL drivers. It's a 2D painting program but it's so that the GUI is implemented with OpenGL. It's not so that it requires the latest 3D hardware (it works on a GeForce 2 for example), but without any it's too slow.

---

### Post by Simian Man on 2010-02-11
Hey Lode, I remember when you posted this on Gamedev.net :).  When I run it, however, I get this:
```
"Error: Unable to set video. SDL error message: Could not create GL context"
```

I'm guessing that's because this is a 32-bit binary, and I'm running 64-bit Linux.  I had to install 32-bit versions of a few libs to even get your program to load.  You should put up a source archive or at least a 64-bit build.

---

### Post by Zeemvel on 2010-02-11
> **Simian Man said:**
> Hey Lode, I remember when you posted this on Gamedev.net :).  When I run it, however, I get this:
```
"Error: Unable to set video. SDL error message: Could not create GL context"
```I'm guessing that's because this is a 32-bit binary, and I'm running 64-bit Linux.  I had to install 32-bit versions of a few libs to even get your program to load.  You should put up a source archive or at least a 64-bit build.

Hi, you can get the code from sourceforge as follows.

First check out the source code with SVN in some directory:

svn co [https://lodepaint.svn.sourceforge.net/svnroot/lodepaint](https://lodepaint.svn.sourceforge.net/svnroot/lodepaint) lodepaint         	

Then follow the instructions in "compilation_instructions.txt" in the doc folder. SDL and OpenGL libraries are required to be able to link.

And then execute the resulting executable, and hopefully it'll work!!

---

### Post by Zeemvel on 2010-02-12
So... Did you have any luck getting it to work?

---

