---
title: "How to develop Ubuntu apps for beginners?"
date: 2018-12-05
forum: Ubuntu Application Development
---

### Post by k9r4n on 2018-12-05
Hey!

I'm new to the development community, and I have zero experience with any proper programming languages. I've only used HTML and CSS, and that's obviously not going to help me. Anyway, I would love to learn to develop Ubuntu apps, so could anyone point me in the write direction? What language is the most popular, easiest, best compiler, how to write the programs using Gedit (I don't like IDE's, so if it's possible to go around them, I'm taking that path :)) and any recommendations you would make to a new app developer. 

Many thanks and appreciation to all and anyone that can help

k9r4n

---

### Post by freemedia2018 on 2018-12-05
I also don't prefer IDEs. I think they are obviously very useful if you need to manage a lot of different files (though if Gedit or Geany do what you want, by all means, go ahead with those.)

If you have zero experience with programming languages, I would recommend Python as a very good first language. Think Python from Green Tea Press (free to download) is the book that helped me learn Python. I would also recommend starting with simple text-based applications first. Why? Because they are typically easier than working with the GUI.

Of course if you want to work with the GUI first, Python does give you options. PyQt lets you create Qt-based applications that will work in Ubuntu, and PyGTK will let you create GTK-based applications. You can look up tutorials for both PyQt and PyGTK and this will give you some idea of which is better for you. Personally I would be inclined towards PyQt but by the time I decided, I don't know what I would choose.

Although Python is not a compiled language, it is available to basically all users of Ubuntu. It runs websites like Youtube and Google uses it extensively.

Speaking of websites, you could also get your feet wet with coding by using Python as a backend for your HTML and CSS. Personally I prefer doing GUI stuff using HTML, despite the fact that I hate HTML and CSS-- I still prefer them to most GUI frameworks. It would let you make use of some of the experience you already have.

IDE/editor is a personal choice, unless you're getting paid to use a specific one.

I just wrote this tutorial recently, which will give you a quick overview of different concepts and syntax in Bash, Python and Javascript, if that helps: [https://ubuntuforums.org/showthread.php?t=2407322](https://ubuntuforums.org/showthread.php?t=2407322)

Happy Coding!

---

### Post by k9r4n on 2018-12-05
Hey!

Unfortunately I am not being paid to use a specific one, but I may try out a couple IDE's just to see if there are any out there that are really simple. yeah I've been looking into Python, actually borrowing a book on programming Minecraft using Python. Haven't got a compatible version of Minecraft for it yet though, just the Windows 10 edition. Seems like a good way to start for now though. I much prefer creating GUI's as well, and recently learned to make a chrome web app. It's not done yet, but I'll provide a link if you want to see it once it's done. 

What is the difference between GTK and Qt? Do only certain system support either? 

HTML and CSS are my favorites right now, though I think that's just because I don't know how to code in any other mark-up language or programming language. I need to learn desperately though, especially if I want to be a software developer and web designer. so far, most of my websites are HTML and CSS based only, with pretty limited functionality. I think I need to learn some design tools as well, because they're still looking kind of weird. I use Bootstrap to make them fully mobile compatible, but I don't use anything else other than the column tags from the css files. I don't want to have to rely on it too much, if you get what I mean?

Thanks for the help, and I will be sure to learn real soon! I'll keep you updated on things.

k9r4n

---

### Post by freemedia2018 on 2018-12-05
> **k9r4n said:**
> What is the difference between GTK and Qt? Do only certain system support either? 

In terms of something like Ubuntu, it isn't really either/or. Ubuntu supports both, there are even other options like Tk (though most of the time, Tk-based apps look pretty ugly) but the most common are GTK and Qt. I have always thought of GTK as more common, and Qt as better-looking. But I don't know how many would agree, or whether that's out of date, or if those are the best ways to describe the difference. Fundamentally, GTK is part of GNOME, and KDE apps use Qt. But whether someone uses GNOME or KDE primarily, you can use PyGTK or PyQt on either of those setups. I still think systems with only (of the two) GTK libs are more common than systems that have only KDE libs. 

I would make my choice on a preference for Qt, but ultimately I would likely choose whichever one was easier to write code for. That depends partly on the library and partly on the language. The relationship (in code) between the language (Python) and the library (PyGTK) is the "bindings"-- PyGTK provides bindings to the GTK library for the Python language. Even if someone has GTK installed, they will still need to install PyGTK if you create a Python application that uses it.

---

### Post by sulton on 2019-08-26
In the beginning, language is not so important as the ability to build algorithms, logical thinking, the ability to use Google.
In many languages, you can develop programs for linux,
but which one is best for you right now no one will tell you.
My advice is to start with Python, they say one of the easiest language to learn.
After 1-2 years, try Java, C/C++/C#, Go, Perl, Javascript and then you will definitely decide on the language.

---

### Post by cruzer001 on 2019-08-26
My method of learning is to take a app and take it apart.  After doing this enough times you find yourself learning how to do things in languages like css and python.

---

### Post by TheFu on 2019-08-26
Necro-post == bad.

Programming GUIs is 10x harder than doing non-GUI programs.
```
#!/bin/bash
echo "Hello World."
```

is a complete Bash program.  The perl, python, go, ruby, C, C++ and most other language versions are about the same.
As soon as we add a GUI in, we need to bring in at least 10KB of more code and many more external libraries.  That holds even if you just get a tiny popup with an "OK" button to close it.

Qt vs GTK vs Wx vs the other 30 options.
By far, GTK is more likely to be used on any Linux distro than any other toolkit.  GTK and Qt libraries are both full featured and huge.  Either can be used for any cross-platform programming needs on Linux, Windows, OSX and BSD systems that have GUI capability.  As a non-KDE user, I won't load any programs that are built using Qt.  My systems aren't bursting with RAM, so I'm unwilling to have a program that needs 900MB of RAM to load the Qt libraries on my system.  If I were a KDE user, I'd probably feel the same about GTK.
If you want more detailed comparisones, google "gtk vs" and that will return comparisons for gtk.  This works for almost any software or hardware for which you want to find competitors.  "python vs" .... 

100% agree that a good first language is python.  Do that and only that language for about 6 months.  Then keep up with python and start learning C.  C is the language that almost every other language is built from and based on. Because C is lower-level, you'll learn how computers REALLY work.  That will make your python coding better.  After those 2 languages, learn whatever other languages you want or get paid to learn.

Don't get hung up on GUI stuff for at least the first month.  You can learn to make web-gui programs on day 2 or 3, if you like, but desktop GUIs are much harder because, as a beginner, you just don't have the background to understand call-backs and event loops.  It isn't hard, but there are more important things to be learning in the beginning.

---

### Post by ryansenn on 2019-09-13
Depending on what you are trying to build I believe that you could also use electron to make use of your html/css knowledge. It does mean using javascript/typescript however. Also performance will never match a native app, but again depending on what you are trying to build it may not really matter.

---

### Post by robbdt on 2019-12-11
Bootstrap is a great fully featured CSS framework.  
When I was learning I found it to be cumbersome and difficult to learn especially with the grid system.

I was better off just learning CSS-Grid {display: grid;} functionality. And the best tip I ever received was to start designing mobile first and then expanding from there with all of the CSS breakpoints expanding from a core mobile design.

I've watched over the years how mobile traffic is slowly over taking regular web browser traffic.  Most of the websites I operate now run about 50/50 mobile vs regular traffic.

---

### Post by coffeecat on 2019-12-11
Back to sleep, old thread. 

Closed.

---

