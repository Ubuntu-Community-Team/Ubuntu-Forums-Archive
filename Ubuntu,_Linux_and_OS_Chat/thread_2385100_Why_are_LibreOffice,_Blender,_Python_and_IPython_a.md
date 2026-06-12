---
title: "Why are LibreOffice, Blender, Python and IPython are faster under Ubuntu?"
date: 2018-02-16
forum: Ubuntu, Linux and OS Chat
---

### Post by egslava on 2018-02-16
I have a laptop. Before there was installed Windows 10. It was quite fast OS, but quite annoying, so now there's installed Ubuntu 16.04.3 LTS (Xenial). I noticed, that some programs start up almost instantly under Ubuntu:

[LIST=1]
[*]Python Interpreter. 
[*]LibreOffice Writer. 
[*]Blender 
[*]GIMP 
[/LIST]
 
I mean, in comparison with Windows and OS X they start up almost INSTANTLY, especially Blender & Writer.

Meanwhile on some programs there's no (or almost no) difference: Spyder IDE, Intellij IDEA.

So I just wonder the reason behind it. I heard an opinion that it's because of the most of the linux apps use shared libraries so they are already loaded somehow. But I'm curious to know a bit more about it.

Thanks in advance! :)

---

### Post by TheFu on 2018-02-16
Intellij is java based.  Java is slow.  Java uses lots of RAM. Don't know anything about Spyder.  Java was slow in 1995, 2005, 2015 and will continue to be slow at loading in to 2050, based on the last 20 yrs of unnoticeable improvements.

IMHO.

The other programs are likely compiled from C or C++.

I don't understand why people use 1 program and call it an IDE, when the entire Unix/Linux OS is an IDE.  [https://sanctum.geek.nz/arabesque/unix-as-ide-introduction/](https://sanctum.geek.nz/arabesque/unix-as-ide-introduction/) It is crazy configurable and customize-able.

---

