---
title: "how hard is compiling a program......in windows?"
date: 2008-05-26
forum: The Cafe
---

### Post by madjr on 2008-05-26
yes, on windows.

---

### Post by grossaffe on 2008-05-26
i guess it would depend on the program.  i compile java programs i write in windows all the time. (well, before i got into linux)

---

### Post by swoll1980 on 2008-05-26
I find it pretty simple

---

### Post by twright on 2008-05-26
not nearly as easy as on Linux though :)

---

### Post by DaveCradock on 2008-05-26
Depends upon the program mainly.

If it's written with C/C++ ... 
Compiling can be as easy as loading the project into the IDE and building.
But, more often than not...
Install the IDE (I miss you Visual studio!)
You sometimes have to make sure (if using Visual Studio) that you have installed the latest service pack for it.
Manually install all libraries needed by the program, setup the IDE to point to the newly installed library's include/lib dirs. Sometimes you'll have to compile these libs yourself and sometimes these libs depend upon other libs which also have to be compiled and sometimes, you have to manually edit some of the header files to get it to "know" it's being built on Windows.
Depending upon the program, environment variables may have to be set aswell.
Click on the shiny build button :)

I'm not sure about Linux, still learning/trying to find a decent IDE.. but when I was building LinuxFromScratch, typing "./configure && make && make install" was so much easier :)

---

### Post by PandaMine on 2008-05-26
Well, it can be just as easy as linux if you get something like minigw/cygwin and add the location of the ggc.exe to the path variable (then its the exact same thing as the gcc command on linux)

Only thing is that binaries created as a result of gcc ports on window are often larger and not as fast (proven with benchmarks) then if you would have used something like MV Compiler or the intel compiler

It really depends on the size of the thing you want to compile

---

### Post by samjh on 2008-05-26
It depends.

A lot of Windows projects are distributed as MS Visual Studio projects, which make building them almost a one-click process.

On the other hand, Unix/Linux-style source packages are harder to compile.  Cygwin and Mingw/MSYS help to make things easier, though.

---

### Post by kragen on 2008-05-26
Well, its pretty much exactly the same as on Linux really. If your talking about c++ or c programs, you need to install a c++ / c compiler (gcc will do nicely, but visual studio Borland c++ etc... all come with their own compilers), then it should all be plain sailing.

When you're talking about compiling a program though, do you mean writing your own program and compiling it, or downloading an open source program and compiling that? 
If you're talking about the latter then you may find that installing the dependencies is a little harder. Generally people don't do that sort of thing as much on windows so there probably isn't going to be an automated command to install all the required libraries, and the documentation might not be as good if your looking at the windows version of a Linux + windows targetted application.

Also, if your trying to compile a Linux targetted application on windows, you will definitely run into troubles! You will almost certainly need cygwin or another Linux shell alternative, but it should still be possible (and definitely a damn slight easier than trying to compile a windows app on Linux)

---

