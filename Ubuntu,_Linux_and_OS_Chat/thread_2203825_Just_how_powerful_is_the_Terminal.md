---
title: "Just how powerful is the Terminal?"
date: 2014-02-05
forum: Ubuntu, Linux and OS Chat
---

### Post by courtneyking1990 on 2014-02-05
I'm a total Linux/computer newbie. Well I can use computers, but I can't do anything too difficult without simplified instructions but I do want to learn how to do these things without having to rely too much on other people. I bought two books on Linux that teaches you how to use it. I've learned a few basic commands and terms from the simpler book and I haven't started on the other yet. I'm a third of the way through the first one and there seems to be so many commands that do the same things you can with the mouse.

Could you do everything through the Terminal without even using the GUI? What is a power user and how do I become one? The Terminal seems like a pretty powerful tool, what could I start doing or learn how to do with my computer to fully utilize it?

---

### Post by dargaud2 on 2014-02-05
Well, yes, technically you can do everything, even drawing pictures using ImageMagick instead of Gimp/Photoshop... But basically the command line is irreplaceable for mass manipulation of data: filtering of text, renaming of numerous files, searching masses of data, programming simple tasks via scripts... But both are complimentary, like the F4 key in the dolphin file manager which opens a shell sync'ed with your navigation.

---

### Post by tgalati4 on 2014-02-05
Welcome to the forums.  Before the graphical user interface (GUI) there was only a terminal console.  So using computers with Unix (an operating system that predates Linux) required knowledge of several arcane terminal commands.  It takes several years to become comfortable with linux, so don't let the volume of information intimidate you.  Yes, you can do most things in the terminal.  Remember the GUI's came later, so the foundation of linux is based on the terminal and what you can do inside it.

Because linux is built on frameworks (layers) there are often several ways to do the same thing.  For instance I was trying to write a command to calculate the number of days until my 90th birthday.  I found at least 6 ways to do it.  [http://www.cyberciti.biz/tips/linux-unix-get-yesterdays-tomorrows-date.html](http://www.cyberciti.biz/tips/linux-unix-get-yesterdays-tomorrows-date.html)

---

### Post by Gone fishing on 2014-02-05
> Could you do everything through the Terminal without even using the GUI? 

Yes

You can configure the computer, set up services, set up networking, search and manipulate files, listen to music etc etc etc. If you were running a linux server you probbly wouldn't have a GUI. So yes you don't need a GUI but you probably want one

---

### Post by Impavidus on 2014-02-05
The simple GUI tools are often just a layer on top of the command line interface. You click at something and the program then calls a command line tool, which you could have called directly from the terminal.

And indeed, you can draw pictures using the command line. I make most of my somewhat technical or mathematical pictures (vector images) by typing code in a terminal. But I still use the GUI to view the output.

---

### Post by buzzingrobot on 2014-02-05
GUI's and character-based commands in a terminal are both interfaces to capabilities and functions built into the operating system.  What is different is the way users express their command, not in how the system responds.

For example, Linux provides standard routines to list the files in a directory.  The same routines will be triggered by an "ls" in a terminal or by clicking on a directory name in a file manager.  In both cases, the name of the directory will be collected and passed to the appropriate routine, which will generate a list of the contents of that directory, and pass the list back to the routine that asked for it.

Character-based commands in terminals are typically more capable than GUI commands because it is easier to expose all of the capabilities of an operating system in a character-based command than in a GUI.  A GUI must work with a limited amount of screen space, so its designers must decide how to make the best use of it.  Character-based terminal commands don't have that problem. They can offer a near endless list of options, based on the notion that few people actually memorize these commands but, rather, know how to look them up.

---

### Post by BoogeyOfTheMan on 2014-02-06
I still consider myself to be a linux noob, even though I've been using linux exclusively since 2009. Don't feel bad about having to ask people for help either, thats what these forums are for, and for the most part, everyone is extremely helpful and friendly. And, like the others have said, you can do everything from the terminal. Much faster in a lot of cases too, as long as you know the correct commands. 

It seems as though you are on the right track by reading a few books. I learned everything by trial and error, and with a healthy dose of help from these forums. (I have a hard time learning from books and tend to do much better by just trying things) But I have to say that the best way to learn, for me at least, is to break something, and then learn how to fix it. As I usually learn two or three other things in the process. 

One tool that I found really helpful is conky, its highly customizable, easily broken and fixed, and most importantly, not a critical component to anything.

Sorry for the ramblings, my meds just kicked in and made me a bit loopy.

---

