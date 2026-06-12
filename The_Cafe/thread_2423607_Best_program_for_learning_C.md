---
title: "Best program for learning C?"
date: 2019-07-26
forum: The Cafe
---

### Post by ProDigit on 2019-07-26
I would like to learn programming in C.
I have Notepad ++ installed, and though I love it, I can't seem to get everything set up, to compile the code.

So I was wondering if there's a good program, that's easy to use, that has 2 windows; 1 code, and window 2 being the executed/compiled window (where I can see the program working, or it's output).

Anyone can help me find a good program for Linux 18.04 or 19.04 (64 bit) please?

---

### Post by fragglebliss on 2019-07-26
What you are after can be done in either Emacs or (G)Vim. The former proibably being the easier of the two, if you're unfamiliar.

The program you use has nothing to do with "learning" C programming. That comes from books, library, internet, course, college etc. The program you use is simply a tool to execute your knowledge.

---

### Post by Skaperen on 2019-07-27
it sounds like you are looking for an IDE.  lots of C programmers, like me, have never needed to ever use one.  what i can do it set up 2 terminal windows side by side.  i have a big wide 1920x1080 display that can do that.  in the left terminal window i can run my editor.  i happen to run emacs, but you can run any editor you prefer.  in the right terminal window i can run the "make" and "make test" commands.  you can switch the windows, if you prefer.  i *can* do that, but what i actually do is run a bunch of virtual workspaces (over 100 of them in total).  i put a nearly full screen terminal window in each of two workspaces with the editor in one.  then i just switch workspaces as needed.

all i need to do in the non-edit window is be sure my current working directory is the directory of the project i am working on, then all i need to do is run the "make" command.

you need to learn about make files.  they let you define your project in terms of dependencies an how each dependency is created,  in the one file name "Makefile" would be the definition of how to build the executable file from all of the compiled binaries.  any of those that are missing or out of date relative to the source will result in the binary being (re)built.

---

### Post by ProDigit on 2019-11-30
Sounds like complex to me!
I'm just a beginner.
I already found some IDE software.
Once I'm good with coding, I can go over this other method you are explaining.

---

### Post by bernard010 on 2019-12-01
Here is a good place to start Learning C Programming.

    [https://www.learn-c.org/](https://www.learn-c.org/)

---

### Post by dons1955 on 2019-12-14
Though this website may be outdated in certain cases (not in case of C i think) but they are very straightforward and easy to follow:
[https://www.tutorialspoint.com/cprogramming/index.htm](https://www.tutorialspoint.com/cprogramming/index.htm)

why not c# though? C# is easier and most easy to consume language

---

### Post by wolftrax on 2019-12-15
I really like geany because its simple and easy to use and it has a console window output everyttime  you compile and run the code and it has syntaxt high lightning.  

aboout learning C I would recommend you get the book the C programming language by dennis ritchie and brian w kernighan and find online tutorials and use youtube videos as well.  
perhaps something like this one [https://www.youtube.com/watch?v=KJgsSFOSQv0](https://www.youtube.com/watch?v=KJgsSFOSQv0) or [https://www.youtube.com/watch?v=-CpG3oATGIs](https://www.youtube.com/watch?v=-CpG3oATGIs)  and there is full courses in C that are hours long.  I downloaded them using youtube-dl and I can watch them when I feel like it on a ordinary television set because I burned them on DVD so I can watch them while I sit in the front of the computer and I also have the PDF  tutorials I used and like printed out so I can read them when I want. one of the PDF tutorials I printed out is this one [https://www.it.uc3m.es/pbasanta/asng/course_notes/ctut.pdf](https://www.it.uc3m.es/pbasanta/asng/course_notes/ctut.pdf)

if you want to use two windows (terminal ) then I usually use two terminals in full screen but use two desktops with nano as editior and the compiling process I use the other terminal for that so I wont have to open nano and fix errors and typos all the time.

---

### Post by TheFu on 2019-12-15
While I don't like IDEs - Linux is an IDE already - **geany** isn't too bad and will force some knowledge that you need to understand. You'll need to configure the compiler, project and debugger, which is the basics for any C programmer to know.  

C really isn't the best 1st language to learn.  Some thoughts about that: [https://blog.jdpfu.com/2011/10/19/how-to-learn-to-program](https://blog.jdpfu.com/2011/10/19/how-to-learn-to-program)  Learn C as a 2nd language, not first.

Lots of free online course exist.  **EdX** has a bunch.  You can pay or not. The knowledge is free and I've never been asked for any C certificate at any job.  I like getting a book and working through it from the start to the finish.  **The Hard Way** books are good. They used to be free online, but seem to have gone to a paid version.  Some people think they need to pay for knowledge or they need to pay to force themselves to actually follow through. Nothing wrong with that.  I've paid for training over the decades, but always tried to get the company to pay first.
Many universities have online courses for free. You pay to get official credit and a pretty certificate, but the knowledge is free.  MIT, Georgia Tech, Standford, Harvard all have free courses.

Why not learn C#?  There are many technical and political reasons NOT to learn C#.  The Linux kernel and drivers are written in C, not C++ and not C#.  C# is for end user applications.  Not being tied to mono is a good reason on its own.  In using C, you'll learn proper memory management that "managed" languages don't require.

For a long time, using the K&R C book was excellent advice and you'll still come across K&R style C code from time to time, but C18 is a very different language worth your time learning. It is the "stable" release that any new project should use today.  It has some excellent protections that didn't exist in prior versions of the language.  K&R code could be 47 yrs old.  Language design has come a long way since then.  Having an editor that understands the different versions of C will be helpful.  I use a vim extension for switching different languages.

I use 4 terminal windows
* editor (vim w/ C plugin and my personal style plugins)
* make/building;  Can run gmake, cmake, ant, whatever
* debugger
* function lookup/reference (man pages); ctags, indentation/style tools, DVCS stuff; when you work in a team, everyone has their own preferred styles, but the project should have a standard that gets applied before check-in is allowed.

This same setup works for every language.  The power of a Unix shell is freakin' amazing, in the hands of an expert. Normal end-users have no idea. None.

---

