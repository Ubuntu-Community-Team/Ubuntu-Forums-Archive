---
title: "Develop apps using C++"
date: 2015-02-19
forum: Ubuntu Application Development
---

### Post by diego-stamigni on 2015-02-19
[COLOR=#404040][FONT=Roboto]Where can I find any kind of documentation for develop apps for Ubuntu (and Ubuntu phone) in C++?&#65279;[/FONT][/COLOR]

---

### Post by TheFu on 2015-02-20
Welcome to the forums.

It would help us to help you if we knew your background.  For example, developing C++ applications on Ubuntu is just like developing C++ applications on Fedora, CentOS, Debian, Solaris, AIX, HP-UX, Irix, *BSD and all the other Unix-like OSes. Same-same.

If you are coming from the MSFT world, there will be much to learn, since we use the entire platform as the development tool, not some IDE. Sure, some people use an IDE, but I think they are the exception, not very common at all.

I work with 3 windows - editor, make, debugger
[http://www.youtube.com/watch?v=keWNLqW31r4](http://www.youtube.com/watch?v=keWNLqW31r4)  might give you an idea.

You might find lots of videos using huge java-based IDEs. If you are a beginner, be cautious about starting with an IDE. They hide important details that you need to understand. After a few months, use whatever you like. By that point you'll understand those little details that need to be configured in any project tool.  I use geany for this reason. Small, fast, editor when vim isn't enough.

[https://stackoverflow.com/questions/623040/c-development-on-linux-where-do-i-start](https://stackoverflow.com/questions/623040/c-development-on-linux-where-do-i-start) provides some more ideas and explanations.

Update: I've been re-reading ***The Art of Unix Programming*** by Raymond. There's a chapter that explains the tools and how the entire platform is used for development.

I wouldn't write Ubuntu-specific applications. It is relatively easy to make cross-platform applications that run on OSX, Windows, and 8+ *nix versions/flavors (Linux is just 1) thanks to Qt and/or GTK toolkits. Don't be limited unless it is required/mandatory.

---

### Post by mkamenjak on 2015-04-02
> **diego-stamigni said:**
> [COLOR=#404040][FONT=Roboto]Where can I find any kind of documentation for develop apps for Ubuntu (and Ubuntu phone) in C++?&#65279;[/FONT][/COLOR]

[https://developer.ubuntu.com/en/](https://developer.ubuntu.com/en/)

---

