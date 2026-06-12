---
title: "So I want to learn programming...now what?"
date: 2006-02-16
forum: The Cafe
---

### Post by PapaWiskas on 2006-02-16
Ok, I have beat around the bush long enough.  Coming from a Windoze world, I toyed with programming, well, actually read here and there.

But the more I use this Xbuntu, Ubuntu, Kubuntu, I am falling in love, hard and fast.  Never did I feel this way about an OS before.

So, my question is to all of you.  I want to start learning some programming, what language should I concentrate on?  I have seen things in JAVA, and PYTHON....not sure what else are my options.  I want to write things for the Linux environment, not worried about Windoze anymore.

I will tell you this.  If there is something out there, that has a GUI, that would be awesome, because I know myself, if I had a GUI, it would be easier for me I think.

Any suggestions, help, encouragement would be appreciated.

Thank you for your time.

Best Regards,
Papa

---

### Post by ember on 2006-02-16
Well, basically I think, you should think what you like to do most. If you want to do grafical GTK-apps, Python with PyGTK or Mono/C# with GTK# may be good options. If you did not do too much programming in advance, I guess Python is a bit easier to learn.

Personally I like PHP really much, but it allows very bad coding style, so you might want to try something stricter in advance.

It all really depends on what you like to do and eventually every programming language has its advantages and glitches.

---

### Post by Stormy Eyes on 2006-02-16
I'd recommend learning how to program the shell first; there's a lot you can do once you know how to write shell scripts. Start with [this HOWTO](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) if you're interested.

---

### Post by GeneralZod on 2006-02-16
[QUOTE=PapaWiskas]
I will tell you this.  If there is something out there, that has a GUI, that would be awesome, because I know myself, if I had a GUI, it would be easier for me I think.
[/QUOTE]

Eclipse is an *excellent* IDE for Java, and highlights many "schoolboy-errors" and tells you how to fix them - great for beginners.  It's *very* slow and bloated, though, so make sure you have a nice, fast, RAM-filled machine!

I'm sure there are HOWTO's for installing it on Breezy - I got mine  from the repos, but I can't remember which ones.

Note that as first *languages* go, though, I'd actually recommend something like ruby+GTK if you don't want to be a "serious" programmer, and C/C++ if you do.

---

### Post by fuscia on 2006-02-16
> **Stormy Eyes]I'd recommend learning how to program the shell first said:**
> this HOWTO[/url] if you're interested.

thanks.

---

### Post by Vanquirius on 2006-02-16
[QUOTE=PapaWiskas]So, my question is to all of you.  I want to start learning some programming, what language should I concentrate on?  I have seen things in JAVA, and PYTHON....not sure what else are my options.  I want to write things for the Linux environment, not worried about Windoze anymore.[/QUOTE]

Once you learn how to program in one language, it becomes much easier to learn a new one. I suggest you start with C, since it is very logical and readable and should introduce you to all the basics.

---

### Post by zkissane on 2006-02-16
[QUOTE=Vanquirius]Once you learn how to program in one language, it becomes much easier to learn a new one. I suggest you start with C, since it is very logical and readable and should introduce you to all the basics.[/QUOTE]

I'd say that once you learn one *procedural* language (like C) it becomes much easier to learn other *procedural* languages.  What's good in procedural languages often isn't so good in object oriented languages, and vice versa.  Learning C as a first step is fine, but you should be very careful to not get into the mindset of "this is how it's done in C; this is how it should be done EVERYWHERE!".  

If you want proof that this is bad, I'll show you some code from the simulation I work on.  It was originally written in Modula for VMS.  Now, it's "written" in C++, but when they ported it to Windows  (years before I joined the team), my coworkers said "this is how it's done in Modula; this is how it should be done EVERYWHERE!".  So now we have things like arrays where the 0 element is empty (because Modula's arrays started at 1), and functions that are pages long.

---

### Post by Lord Illidan on 2006-02-16
I first learned Pascal at school, then moved on to C, now, I am learning C++. I also flirted with python, quite nice, but I disliked the constant tabbing.

 Transitioning from procedural to object oriented is quite difficult, I am getting bogged down in pointers and classes. Preserverance is the name of the game.

Do you wish to program for KDE or GNOME? If so, KDE requires C++, I believe, and GNOME - C.

Have a look at QT, KDevelop - IDEs for KDE, and Anjuta - a great IDE for GNOME.
(Though they can be used under both window managers..)

If it is really your first attempt at Linux programming, try Python or C. If you are ambitious, try C++.

---

### Post by ember on 2006-02-16
Well, after all that comments another one by me:

If you want to get much insight into programming, I recommend you to learn:

- one scripting language like python, ruby, php
- one common object oriented programming language like java, c#, c++
- one functional programming language like gofer, haskell

Well plus 'C', if you want to do some really base level programming. Yet I would not recommend it as a starting point. Procedural programming can produce a lot of bad habits and it takes a really long time to retrain yourself (I am trying now for a couple of years and I still find myself doing thing the quick-and-dirty way quite often).

Also most desktop enviroments have several bindings, so you can programm your Gnome as well as KDE applications in nearly any major programming language. 

And if you want to know everything about algorithms in advance, buy 'The art of computer programming' ;)

---

### Post by PapaWiskas on 2006-02-16
Thank you for taking the time to reply to my posting.  This has given me the direction that I needed.

I think I will start out as fuscia said, with shell scripting to start off.  All of you have brought up some very good points.  I just have to start off slow and be patient and not try and rush it.

Thank you so much for your time.  This is what makes this community so great.

Best Regards,
Papa

---

### Post by ssam on 2006-02-17
i'd recommend learning python. but if you want an easy route into GUI programming you could try [gambas]("http://gambas.sourceforge.net/") (sort of like visual basic).

---

### Post by 3rdalbum on 2006-02-17
Buy an old old Mac and it should have Hypercard installed on it :p 

(I wish there was something like Hypercard for Linux...)

But seriously, I recommend Python. The MacPython IDE did all the tabbing for you (every time you pressed return, the new line would have the same number of tabs as the previous line, plus one if it ended in a colon) so if you find an Integrated Development Environment with the same functionality, that would be excellent. gEdit has Python code colouring.

With Python it's possible/easy to get the programs running on all three major platforms without changing the code. Tkinter, the GUI toolkit that comes with it, is pretty easy to use as well for beginners.

Unfortunately, to create interfaces in Python you still need to write code.

I recommend giving Java a wide berth, especially if you want the programs to run on OS X without opening huge security holes :p

---

