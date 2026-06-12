---
title: "Compile first C++ program with gcc."
date: 2015-12-06
forum: Ubuntu Application Development
---

### Post by sethanath2 on 2015-12-06
Hi,

I know Ubuntu Studio has "gcc", and I want to use it to compile my first C++ program. 
Can you let me know the steps to set "gcc" to work perfectly for my first program?
Do we need to set any "environment variable" in the OS? 
Back in college, I needed to set "class path" for my Java programming, and I am guessing there might be something similar for this "gcc".

I am planning to use eclipse as the editor for C++.

Now, I found this command on the internet "sudo apt-get install eclipse eclipse-cdt g++", but should I need anything else?

Thank you so much.

---

### Post by TheFu on 2015-12-06
g++ -c file.C
 or 
g++ -c file.cc
 or 
g++ -c file.cpp

That will compile it.  Eclipse is kinda overkill for C/C++.  The vast majority of old-time C programmers use vim for their editor. After all, Unix (the entire environment) is an IDE for programming. Limiting oneself to just a single monstrous tool seems counter intuitive.

I think you want the basic development tools ... those are packaged in a metapackage ... can't remember the name ... let me google ... [https://askubuntu.com/questions/24197/how-can-i-install-commonly-used-developer-tools](https://askubuntu.com/questions/24197/how-can-i-install-commonly-used-developer-tools) .... "build-essential" is what you want.

For more complicated programs, you'll want to use cmake or gmake and a "Makefile" - this is how Unix programmers manage project dependencies and only build the parts that matter. We also add build options like INCLUDE directories and LIB directories for the compile and link stages this way.  Much easier to type 'make' to rebuild whatever needs rebuilding and not the entire project.  Basically, it is upArrow<enter> in the "build" terminal all day long. Or !!<enter> if the arrow keys are too far away. ;)  Using a mouse just slows us pros down.

Development on Windows is performed within a tightly coupled IDE, compiler, linker, and project management tool. Unix doesn't work that way, but it can.  I would suggest you do whatever the teacher of the class suggests, but if I were teaching, I'd forbid any IDE be used on Unix for the 3 months of the beginner class. Those tools hide very important details and when something breaks in the dev environment, you'll be stuck without the skills to fix it.  OTOH, if you have 3 terminals - editor, gmake, debugger and use each for that specific purpose, you'll learn the way to code that will last the rest of your life, regardless of which IDE you decide (if any) to use later. Don't cheat yourself from that skill.

Make sense?

---

### Post by mystics on 2015-12-06
Relevant comic given TheFu's comments: [http://xkcd.com/378/](http://xkcd.com/378/)

> **sethanath2 said:**
> Can you let me know the steps to set "gcc" to work perfectly for my first program?

You should be able to just install it. Some IDEs will require you to set the compiler you want to use, but at least on Linux, it is a simple install of the compiler.

> Do we need to set any "environment variable" in the OS? 
Back in college, I needed to set "class path" for my Java programming, and I am guessing there might be something similar for this "gcc".

If you were running Windows, then you would need to do that. On Linux, the executables are stored in /usr/bin. This is a well defined place that is looked to when making a call to things like javac, gcc, and python. Windows is more flexible in where things are stored (generally speaking), but this comes at the cost have not having a well-set environment. As a result, Windows requires you to set the path to where the executable is so that programs know where to look for that compiler.

> I am planning to use eclipse as the editor for C++.

Now, I found this command on the internet "sudo apt-get install eclipse eclipse-cdt g++", but should I need anything else?

To my knowledge, the Eclipse in the Ubuntu repositories is not up-to-date. It might be better to go with something like Code::Blocks (or Vim if you want to please all the hardened C/C++ programmers). Not only is C++ supported by Code::Blocks by default, it is more up-to-date in the Ubuntu repositories (to my knowledge).

---

### Post by sethanath2 on 2015-12-06
Thank you so much both of you. I will try it some more to see.

---

### Post by brian-mccumber on 2015-12-06
Geany is another good editor for writing and compiling c/c++ code that is available in the software center. It was a little tricky to figure out how to compile in the editor while using a library like gtk, but I got it figured it fairly quickly. I also use it to write basic code using FreeBASIC which will also compile from the editor.

---

### Post by sethanath2 on 2015-12-06
Let me try Eclipse as such IDE looks so cool :) 
I know I headed the wrong way with my subject line, but maybe I get lucky with it.

Here are the steps that I did.


[LIST=1]
[*]Installed OpenJDK Java 7 from "Ubuntu Software Center". 
[*]Eclipse in "Ubuntu Software Center" is too old. By googling, I found out that I should download the Eclipse Installer (Release 4.5.1) from "http://www.eclipse.org/downloads/", which I chose the Linux 64 bit version. 
[*]By extracting the downloaded file, clicked on , I was able to install the software to "/home/erick/eclipse/cpp-mars/". 
[*]From Eclipse IDE, 
[/LIST]

[LIST]
[*]Clicked "File", "New", and "C++ Project".
[*]Chose "GNU Autotools/Hello World C++ Autotools Project" in "Project Type", and "GNU Autotools Toolchain" in "Toolchains".
[*]Clicked "Finish"
[/LIST]


5. Edited the file "/home/erick/workspace/HelloGtkmm/configure.ac" to be

[INDENT]dnl Process this file with autoconf to produce a configure script.

AC_PREREQ(2.59)
AC_INIT(HelloGtkmm, 1.0)


AC_CANONICAL_SYSTEM
AM_INIT_AUTOMAKE()

AC_PROG_CXX

PKG_CHECK_MODULES([MYAPP], [gtkmm-3.0] >= 3.0.0])

AC_CONFIG_FILES(Makefile src/Makefile)
AC_OUTPUT

[/INDENT]
6. Edited "/home/erick/workspace/HelloGtkmm/src/Makefile.am" to be

[INDENT]AM_CPPFLAGS=$(MYAPP_CFLAGS)
bin_PROGRAMS=gtkmmhello
gtkmmhello_SOURCES=HelloGtkmm.cpp
gtkmmhello_LDADD=$(MYAPP_LIBS)
[/INDENT]
 
7. Edited "/home/erick/workspace/HelloGtkmm/src/HelloGtkmm.cpp" to be

[INDENT]============================================================================
 Name        : HelloGtkmm.cpp
 Author      : 
 Version     :
 Copyright   : Your copyright notice
 Description : Hello World in C++,
 ============================================================================
 */

#include <gtkmm.h>

int main(int argc, char *argv[])
{
  Glib::RefPtr<Gtk::Application> app =
    Gtk::Application::create(argc, argv,
      "org.gtkmm.examples.base");

  Gtk::Window window;
  window.set_default_size(200, 200);

  return app->run(window);
}
[/INDENT]
 
8. Eclipse showed many errors. I will have to do the following to remove them.


[LIST]
[*]Clicked "Project" and "Clean..." from Eclipse menu. 
[*]From "Project Explorer", right clicked "HelloGtkmm", and "Reconfigure Project". 
[*]From "Project Explorer", right clicked "HelloGtkmm", and "Build Project". 
[/LIST]
[INDENT]
However, those error messages are still there as you can see from the attachment.

Can someone help?

  
[/INDENT]

---

### Post by sethanath2 on 2015-12-06
> **sethanath2 said:**
> [INDENT]
However, those error messages are still there as you can see from the attachment.

Can someone help?

[/INDENT]


Here is each error message, starting from the top.

Description    Resource    Path    Location    Type
Error 127 occurred while running autoreconf    HelloGtkmm        -1    Configure Problem

Description    Resource    Path    Location    Type
Function 'create' could not be resolved    HelloGtkmm.cpp    /HelloGtkmm/src    line 16    Semantic Error

Description    Resource    Path    Location    Type
make: *** No rule to make target `all'.  Stop.    HelloGtkmm             C/C++ Problem

Description    Resource    Path    Location    Type
Method 'run' could not be resolved    HelloGtkmm.cpp    /HelloGtkmm/src    line 22    Semantic Error

Description    Resource    Path    Location    Type
Method 'set_default_size' could not be resolved    HelloGtkmm.cpp    /HelloGtkmm/src    line 20    Semantic Error

Description    Resource    Path    Location    Type
Symbol 'app' could not be resolved    HelloGtkmm.cpp    /HelloGtkmm/src    line 15    Semantic Error

Description    Resource    Path    Location    Type
Symbol 'app' could not be resolved    HelloGtkmm.cpp    /HelloGtkmm/src    line 22    Semantic Error

Description    Resource    Path    Location    Type
Symbol 'Application' could not be resolved    HelloGtkmm.cpp    /HelloGtkmm/src    line 15    Semantic Error

Description    Resource    Path    Location    Type
Symbol 'RefPtr' could not be resolved    HelloGtkmm.cpp    /HelloGtkmm/src    line 15    Semantic Error

Description    Resource    Path    Location    Type
Type 'Gtk::Window' could not be resolved    HelloGtkmm.cpp    /HelloGtkmm/src    line 19    Semantic Error

Thank you.

---

### Post by steeldriver on 2015-12-06
Did you install the libgtkmm-3.0-dev development package? Can you build your example from the command line, for example using

```

g++ HelloGtkmm.cpp -o HelloGtkmm `pkg-config gtkmm-3.0 --cflags --libs`

```

Choosing a gtkmm application (however simple) as your first C++ compilation exercise is... ambitious, imho

Choosing to build a gtkmm application using autotools under Eclipse as your first C++ compilation exercise takes it to a whole other level :D

---

### Post by sethanath2 on 2015-12-06
> **steeldriver said:**
> Did you install the libgtkmm-3.0-dev development package? Can you build your example from the command line, for example using

```

g++ HelloGtkmm.cpp -o HelloGtkmm `pkg-config gtkmm-3.0 --cflags --libs`

```

Choosing a gtkmm application (however simple) as your first C++ compilation exercise is... ambitious, imho

Choosing to build a gtkmm application using autotools under Eclipse as your first C++ compilation exercise takes it to a whole other level :D

Here are the steps that I did.

erick@erick-asus-a8n32-sli-deluxe:~$ cd "/home/erick/workspace/HelloGtkmm/src/"
erick@erick-asus-a8n32-sli-deluxe:~/workspace/HelloGtkmm/src$ g++ HelloGtkmm.cpp -o HelloGtkmm `pkg-config gtkmm-3.0 --cflags --libs`
Package gtkmm-3.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkmm-3.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkmm-3.0' found
HelloGtkmm.cpp:11:19: fatal error: gtkmm.h: No such file or directory
 #include <gtkmm.h>
                   ^
compilation terminated.

I hope someone can help me further.

---

### Post by steeldriver on 2015-12-06
As mentioned, I think you will need to install the libgtkmm-3.0-dev package - either using your favourite package manager, the Software Center, or via a terminal using

```

sudo apt-get install libgtkmm-3.0-dev

```

---

### Post by sethanath2 on 2015-12-06
My mistake! I will need to install gtkmm first. I will do it now.

---

### Post by sethanath2 on 2015-12-06
> **sethanath2 said:**
> My mistake! I will need to install gtkmm first. I will do it now.

Here are the steps that I have just performed.

$ sudo apt-get install libgtkmm-3.0-dev
$ cd "/home/erick/workspace/HelloGtkmm/src/"
$ g++ HelloGtkmm.cpp -o HelloGtkmm `pkg-config gtkmm-3.0 --cflags --libs`

I no longer get error message, and I can see executable file in  "/home/erick/workspace/HelloGtkmm/src/".

---

### Post by sethanath2 on 2015-12-06
However, here is one of the issue I found from Eclipse. I do not have "Pkg-config" tab in eclipse.
This website mentioned that I will need to drag the "Install" file over to Eclipse Workspace to install, which I have just done now, but I still cannot see "Pkg-config" tab.

[https://marketplace.eclipse.org/content/pkg-config-support-eclipse-cdt](https://marketplace.eclipse.org/content/pkg-config-support-eclipse-cdt)

I hope someone can help me further.

---

### Post by sethanath2 on 2015-12-08
> **sethanath2 said:**
> However, here is one of the issue I found from Eclipse. I do not have "Pkg-config" tab in eclipse.
This website mentioned that I will need to drag the "Install" file over to Eclipse Workspace to install, which I have just done now, but I still cannot see "Pkg-config" tab.

[https://marketplace.eclipse.org/content/pkg-config-support-eclipse-cdt](https://marketplace.eclipse.org/content/pkg-config-support-eclipse-cdt)

I hope someone can help me further.

I am able to get Pkg-config to work with Eclipse now.
Please see the different post below.

[http://ubuntuforums.org/showthread.php?t=2305636](http://ubuntuforums.org/showthread.php?t=2305636)

Thank you so much for your time. I was able to compile my first C++ with gcc too.

---

