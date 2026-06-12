---
title: "How can i develop applications for Ubuntu?"
date: 2013-06-08
forum: Ubuntu Application Development
---

### Post by protoss96 on 2013-06-08
I am beginner with linux programming and i was wondering if there is any IDE where can i write applications for Ubuntu? I heard that Ubuntu is written in C, so can i just use Code::Blocks and write something in C and run? Btw i know for Ubuntu SDK but i don't know where to start with learning code or how to install. Thanks in advance.

---

### Post by protoss96 on 2013-06-08
And i know C++, C and Assembly can i write apps with that?

---

### Post by T.J. on 2013-06-09
There are several options, depending on your learning curve and level of experience.  If you are coming from a Windows environment, you may have some trouble adjusting to the fact that Linux or more specifically, UNIX in general  - does not have a mandated User Interface.  There are several to choose from &#8211; all of which run on top of X11 &#8211; (which we will call for the sake of simplicty) a generic GUI framework.  Along with your choice of development language, your favorite Desktop Environment might affect your final decision, although programs developed using one desktop typically works just fine in another.  You can run Gnome programs inside of KDE, for example.

There are several very good DE's to pick from.  My personal favorites are CodeBlocks and Kdevelop/QtDevelop.  CodeBlocks is very generic (There are versions for Windows, Linux, etc) and  it can theoretically work with almost any development setup: KDE, Gnome &#8211; whatever.  The same can be said for QT/Kdevelop &#8211; however it is primarily for KDE/Qt and leans heavily in those areas.  There are literally dozens of others: Eclipse, Anjunta, etc so it's a large field.   Linux has all the languages that Windows has (and many it does not) &#8211; with the exception of a workable VB.NET.  Generally speaking, you want to expect that the languages you will use on Linux follow international standard rather than Microsoft's.  One notable exception might be Mono &#8211; a version of C#.  They try to follow Microsoft's reference implimentation closely.  Linux itself is written in C with some assembly added for good measure. So your skills in C/C++ and assembly will still be of value to you. 

Each of those DE's can be installed with very little hassle.  I encourage you to post more about what you plan and then we can narrow the field somewhat to something that best suits your style.

I'd also suggest that you take the time to familiarise yourself with the POSIX (Portable Operating System Interface) standard to some degree.  I know that a lot of people will call that &#8220;old school&#8221; - but should you follow POSIX API's as much as is feasible, if you decide to port your code to Mac, another Linux, BSD, or any other UNIX type system, it will be much easier.

---

### Post by protoss96 on 2013-06-09
thank you so much for replying, i will look up  for POSIX now, thanks again

---

### Post by T.J. on 2013-06-09
You're welcome.  I'm sorry my first answer seemed vague, and did not answer your question directly.  Under the assumption that you're interested in CodeBlocks you can install it using the Software Center, or from a terminal, if you prefer:

*sudo apt-get install codeblocks codeblocks-contrib*

Either way, it should be on your menu when you finish. Installing the contrib package for codeblocks adds some extra items that you may want.

---

### Post by vykuntamsrinivas on 2013-06-16
hello all!
           i have passion to develop apps for ubuntu.I have a little exposure to linux and i know shell scripting C,C++ and java as well.Now i am using DEBIAN 7.As T.J  suggested in previous post  i'll  go for code blocks (IDE) installation.could you please tell  what tolearn   after  IDE installation? :confused:

---

### Post by MG&amp;TL on 2013-06-16
> **vykuntamsrinivas said:**
> hello all!
           i have passion to develop apps for ubuntu.I have a little exposure to linux and i know shell scripting C,C++ and java as well.Now i am using DEBIAN 7.As T.J  suggested in previous post  i'll  go for code blocks (IDE) installation.could you please tell  what tolearn   after  IDE installation? :confused:

A couple of points:
[LIST=1]
[*]Welcome to the forums!
[*]Make a new thread next time.
[*]Install Ubuntu. Debian isn't Ubuntu, even if it is the 'father'.
[*]Learn about Python, GTK+, and probably Qt, then about Debian packaging at your leisure, then you're probably good to go. You'll need to learn about other things as required for your project.
[/LIST]

---

### Post by mhall119 on 2013-06-16
The best way to get started is to visit [developer.ubuntu.com]("http://developer.ubuntu.com/get-started/") to get the Ubuntu SDK installed and follow the app development tutorial to learn how to write your own apps.

---

### Post by vykuntamsrinivas on 2013-06-17
Thanks  for the reply  MG&TL  and mhall119,

       yeah  i  have  started  learning PYTHON.Could you please tell me How to join  ubuntu project,Actually it is my passion to be an OS developer.I  completed my engineering from Computer Science stream  and i learn  operating systems,networking,c,c++ and java . I am good at coding and   interested in open source as well.Can you please  suggest  the way to  reach my goal?

---

### Post by MG&amp;TL on 2013-06-17
> **vykuntamsrinivas said:**
> How to join  ubuntu project,Actually it is my passion to be an OS developer.

Depends on what you count as 'OS': ubuntu mostly deals with interface and other considerations, not necessary the underlying kernel or other pieces which make up the picture. If you're interested in all of it, try [http://community.ubuntu.com/contribute/developers/](http://community.ubuntu.com/contribute/developers/).

If you're just interested in the *kernel* that Ubuntu and other linux distributions use, I'd suggest joining the LKML (Linux Kernel Mailing List), and searching around for 'how to get started linux kernel'.

You might be a little inexperienced; in my limited experience, the world of software engineering is radically different to that of computer science.

---

### Post by vykuntamsrinivas on 2013-06-18
Thanks a lot**  MG&TL**,
                             you make my way more clear....once again thank you!
                               [**[COLOR=#DD4814][/COLOR]**]("http://ubuntuforums.org/member.php?u=1320682")

---

### Post by mni on 2013-07-13
> **MG&TL said:**
> Depends on what you count as 'OS': ubuntu mostly deals with interface and other considerations, not necessary the underlying kernel or other pieces which make up the picture. If you're interested in all of it, try [http://community.ubuntu.com/contribute/developers/](http://community.ubuntu.com/contribute/developers/).

If you're just interested in the *kernel* that Ubuntu and other linux distributions use, I'd suggest joining the LKML (Linux Kernel Mailing List), and searching around for 'how to get started linux kernel'.

You might be a little inexperienced; in my limited experience, the world of software engineering is radically different to that of computer science.

Hi MG&TL,

This thread is discuss about How to make application for ubuntu platform. I have read from [http://developer.ubuntu.com/get-started/](http://developer.ubuntu.com/get-started/). The site explain to install ubuntu SDK. It seem for developing mobile application, correct me if i am wrong. And i want developed for Desktop. Is there any project that currently running..?. Because i want to contribute as developer. If somebody know, please tell me.



Best Regards,
**Iqbal**

---

