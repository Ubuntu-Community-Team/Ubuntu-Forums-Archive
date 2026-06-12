---
title: "need help with wine.."
date: 2010-06-19
forum: Wine
---

### Post by psudheera on 2010-06-19
hey friend i need some help here since i'm new to ubuntu(to linux also)...this is the problem.

i installed wine on ubuntu 10.04 and install [c-free 4.1]("http://www.programarts.com/cfree_en/index.htm") .The installation is completed no errors.and [c-free]("http://www.programarts.com/cfree_en/index.htm") is working perfectly except its unable to output any thing to terminal.Is there any way to solve this?(or a software same to c-free working with ubuntu) please pay your kind attention to this guys.  
thank you in advance :lol:

---

### Post by anewguy on 2010-06-19
I'm curious as to why you want to use a C/C++ set in Wine, when it is free in native Ubuntu?  While not by default an IDE as C-Free is supposed to be, there are tools in Ubuntu which you can tie C/C++ in to and have an IDE.

Just curious........

Dave ;)

---

### Post by Elfy on 2010-06-19
moved to wine

---

### Post by psudheera on 2010-06-19
> **anewguy said:**
> I'm curious as to why you want to use a C/C++ set in Wine, when it is free in native Ubuntu?  While not by default an IDE as C-Free is supposed to be, there are tools in Ubuntu which you can tie C/C++ in to and have an IDE.

Just curious........

Dave ;)

can you name some c/c++ tool pls??

---

### Post by Nr90 on 2010-06-19
Anjuta IDE

---

### Post by anewguy on 2010-06-19
I believe the C compiler gcc is installed by default, and you can install the g++ compiler as well, both in Synaptics Package Manager.

As Nr90 posted, Anjunta IDE can also be installed from Synaptics Package Manager and used with gcc and/or g++.

Dave ;)

---

### Post by psudheera on 2010-06-20
thanks guys..i'm gonna try Anjunta IDE...

---

### Post by psudheera on 2010-06-22
oh! god help me..i'm on another problem..i have installed  Anjunta IDE and no problem with installation.when i try to execute my program theres a error massage " Program '/home/sudheera/c/puts.o' does not have execution permission".
what does it mean.my account is  the only one in this computer and i think it have administrator privileges.i'm using 10.04.please anyone can help me...?

---

### Post by anewguy on 2010-06-22
> **psudheera said:**
> oh! god help me..i'm on another problem..i have installed  Anjunta IDE and no problem with installation.when i try to execute my program theres a error massage " Program '/home/sudheera/c/puts.o' does not have execution permission".
what does it mean.my account is  the only one in this computer and i think it have administrator privileges.i'm using 10.04.please anyone can help me...?

If you have it linking to gcc or g++ correctly, I *think* it should by default be creating an output file that should already be executable.  So, try the following:

- open a terminal window (applications/accessories/terminal

- type:

cd c <press enter>

ls -al puts.o <press enter>

The permissions are listed at the front - starting with owner, then group, then world.  It also lists who owns the file - is it showing your userid?  

You can try:

sudo chmod +x puts.o <press enter>

Then try your program again.

It would probably be best if you posted back the output that shows from the "ls -al puts.o" so we can see what it says ourselves.

Dave ;)

---

### Post by asdfoo on 2010-06-22
object files are not executables, you do not run them.

This is off-topic here, open a thread in a different subforum since this is no longer related to Wine.

---

### Post by anewguy on 2010-06-22
> **asdfoo said:**
> object files are not executables, you do not run them.

This is off-topic here, open a thread in a different subforum since this is no longer related to Wine.

I thought that since it wasn't the default a.out that perhaps they had specified puts.o as the output file.  I know about the .o extension and how it is normally used, but thought that adjunta as surely creating an executable.  My mistake - glad you caught that.  

With that in mind, and bearing in mind that I'm an old school text-edit then command line compile guy, is there a setting in adjunta to specify the output as object only, or perhaps a toggle for linking?  I'm curious in case I decide to try it in the future.

Thanks,
Dave ;)

---

### Post by anewguy on 2010-06-22
> **asdfoo said:**
> object files are not executables, you do not run them.

This is off-topic here, open a thread in a different subforum since this is no longer related to Wine.

Please note that originally this thread was in the absolute beginners forum, then one of the moderators moved it to the wine forum.

Basically this thread has never really been about Wine.  It was opened that way by the OP due to not knowing about the tools available in native Linux.

Dave ;)

---

