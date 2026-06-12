---
title: "Best IDE and PL to use in Linux???"
date: 2008-01-22
forum: The Cafe
---

### Post by Dr-KDE on 2008-01-22
I need your advice about the best IDE and PL to use in Linux, I will give you a  background about myself so you can better guide me.  
 

 I am kind of new to Linux/Ubuntu, but settling down fast. My background is in computer science I worked for 5+ years as a software developer before going into academic research. I have used several programming languages including  
 

 [LIST=1]
[*]C/C++
[*]C#  	
[*]VB (MCP)
[*]Java
[/LIST] 

 Sadly all the target OS I programmed on were MS Windows based (PC and hand-held). Although I have a good working knowledge about the Windows API,  I am not familiar with the Linux architecture and programming for Linux.


    
 Currently I am using C# in my academic research as my computer science department is partially sponsored by MS. I have written my first Linux application using Mono but I didn't like the Mono IDE. Also, it seems to be slow and unpopular between Linux users.  
  Which are the best tools/PL to create general GUI Linux applications. I don't want to create a pure KDE or GNOME application. I would prefer to write an applications which runs well on both desktops. Honestly, I think both Gnome and KDE are good desktop managers, but some of the KDE applications are better and vesa versa. I already have a huge headache from the KDE/GNOME debate.  
 

 For the time being I want to write small Linux utilities which will do small tasks for me. However,  In the future I plan to contribute to the open source community so I prefer to write applications that runs well on  most Linux distribution. I have already ruled out Java and C#/Mono so far (advice me if I should use one of them).  
 

 I would like to hear Linux programmers ideas about this subject.  
 

 Many Thanks

---

### Post by Steveway on 2008-01-22
If you allready know C and C++ i would advise to use them since they are commonly used in most Linux applications.
I can't help you with a choice between IDEs (I'm a Python-beginner using SPE.)
The best would be if you'd get a whole bunch of them from Synaptic and then just try them all and stick with the one you like the most.
Well the choice between GUI-toolkits is your problem, if you have the time then try to write something using both and stick with the one that you prefer.
If you worry if they will run on the other DE then just minimize the use of DE-specific things, like depending on the kde-libraries instead of using plain QT and vice versa.
This is Linux, you have the choice.
Also yes C# is slow and I hate it, including the guys "programming" with it. Beagle? Seriously. Dude...

---

### Post by Incense on 2008-01-22
I don't know if it does C# or not, but I really like KDevelop. 

[http://www.kdevelop.org/]("http://www.kdevelop.org/")

---

### Post by igknighted on 2008-01-22
Looking at your handle and your Konqi avitar, I am assuming you are a KDE user.  If this is the case, you may want to focus on c++ as it is the primary language for KDE (and the qt toolkit).

If you want something a little more high-level (closer to C# than C), you might try python.  It's interpreted, and often used as a scripting language... but is also capable of rapidly developing code and has bindings for all the major windowing toolkits (gtk+, wxwidgets, qt, etc.), and the code is very readable.  Plus 90% of the Ubuntu-specific code seems to be written in it, so if you stay with Ubuntu you will likely see it a lot.

Tough to go wrong, really.  There are tons of choices available for programming on linux, and tons of tools to assist you.  Personally, I like using a text editor for coding (kate/kwrite and Scite, sometimes Gedit) and compiling via the CLI.  But as mentioned, kdevelop is a gread IDE.  Anjuta is another good one, and Eclipse is also a good choice.  If you have used Java, I suspect you have encountered Sun's NetBeans, which I believe may support application development in other languages as well, tho I could be wrong.

Good luck and welcome!

---

### Post by Dr-KDE on 2008-01-22
Thank you all for your replay's. I am currently running Ubuntu with several KDE applications on top. I was using Kubuntu but found it not very stable. I tried OpenSuse as well for a short time, but decided to stick with Ubuntu because I like the online community and I don't like Novel.

I am reading several articles right now and I think I will use c/c++ && Python for a while and see how things are going. I might use KDevelop as well

---

