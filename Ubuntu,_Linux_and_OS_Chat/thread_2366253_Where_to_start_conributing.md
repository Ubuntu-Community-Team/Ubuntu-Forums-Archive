---
title: "Where to start conributing?"
date: 2017-07-15
forum: Ubuntu, Linux and OS Chat
---

### Post by marko-borkovic on 2017-07-15
[B]Hello!
[/B]
My name is Marko I'm a 14 year old programmer that just started out in Linux development.

I really want to contribute to Ubuntu OS because I think it would be awesome to know Linux internals and kernel.

Where can i modify Ubuntu code and where can i learn to modify it?

I already know C, C++, Python and Php,

Are there any good learning sources?

Thank you!

P.S. I'm also interested in creating my own Linux distributions

---

### Post by vasa1 on 2017-07-15
Maybe here: [https://wiki.ubuntu.com/One%20Hundred%20Papercuts](https://wiki.ubuntu.com/One%20Hundred%20Papercuts) ?

---

### Post by oldos2er on 2017-07-15
Moved to Ubuntu, Linux & OS Chat.

[https://wiki.ubuntu.com/ContributeToUbuntu](https://wiki.ubuntu.com/ContributeToUbuntu)

[https://community.ubuntu.com/contribute/](https://community.ubuntu.com/contribute/)

[https://community.ubuntu.com/contribute/developers/](https://community.ubuntu.com/contribute/developers/)

[https://wiki.ubuntu.com/UbuntuDevelopment](https://wiki.ubuntu.com/UbuntuDevelopment)

---

### Post by vocx on 2017-07-15
> **marko-borkovic said:**
> [B]Hello!
[/B]
My name is Marko I'm a 14 year old programmer that just started out in Linux development.

I really want to contribute to Ubuntu OS because I think it would be awesome to know Linux internals and kernel.

Where can i modify Ubuntu code and where can i learn to modify it?

I already know C, C++, Python and Php,

Are there any good learning sources?

Thank you!

P.S. I'm also interested in creating my own Linux distributions
First of all, you have to understand how open source software works. Open source gives you ultimate freedom to do whatever you want. This also means that usually there is no clear organization and things happen randomly, at the discretion of the individual developers.

Ubuntu is not a single entity. Think of it like a country. What really makes a country is not the name but the people that live and work inside it. So, Ubuntu, like a country, provides a generic environment of software, but what really makes it an operating system is all the programs that are inside of it: office programs, text editors, web browsers, terminals, games, programming environments, network managers, window managers, music programs, video programs, drawing programs, printing programs, etc. Contributing to any single program is contributing to "Ubuntu" as a whole, in the same way that working for a business, a store, a school, a factory, etc. contributes to a country's economy.

So, when you say, "I want to contribute to Ubuntu", what you should really think is "I want to contribute to program _______". Also, it is not as simple as knowing the syntax of a few programming languages. If you want to contribute to a single program, you need to learn how the source code for that program is structured. In real life, working for a bank, or for a school, or for a fire department, or for a hospital, or for an oil field, or for a car workshop, or for a accountancy firm, or for a graphical design studio, or for an orchestra, or for a public library, etc. is different every time. You need different skills and knowledge for each job. So, in software and in Ubuntu it is the same. You need to learn the framework that makes that program work. You need to learn about libraries such as GTK+, QT, that provide a graphical interface, you need to learn about libraries that interface with the web, with databases, with numerical software, with remote servers, etc. Unfortunately, most people will not hold your hand and tell you exactly what you need to learn. Other programmers will expect you to learn on your own. They will want you to investigate the source code yourself, read manuals, learn to compile, add functions, and fix bugs all by yourself. Only when you have proven yourself, they will consider you competent to take on bigger responsibilities. This is a bit like learning to become an electrician or learning a foreign language all by yourself. You first learn as much as you can on your own, and maybe later, somebody will help you advance to the next level.

At your age, 14 years old, no programmer will take you seriously. You first need to prove yourself by writing small programs, writing documentation for existing programs, or fixing bugs in other programs, before people will consider you knowledgeable. It's the same in any knowledge based field. If a person comes to me and says, "I'm a 14 year old architect that just started designing houses", I will not trust that person, because even if he knows a few things about sketching, he probably does not have enough experience in his field to really be great at it. It will take many years until somebody can show mastery in their field.

The Linux kernel is a beast of its own. It's a huge "program", and it deals a lot with physical hardware, processors, video cards, USB devices, PCI buses, etc. You can spend a lifetime programming user software, but maybe you will never learn a thing about the kernel. So, do not worry about it, unless you really want to go into electronic circuit design, embedded hardware systems, microcontrollers, and things like that. Usually for this you need a university degree in electrical engineering or a related field. It is not for the casual programmer.

Creating your own Linux distribution is not very complicated, but it's also not extremely useful. A Linux distribution, like Ubuntu, is nothing but a collection of packages that other people have developed. Ubuntu is itself based on Debian. That means Ubuntu developers take Debian packages, make a few modifications, and package everything again. It's basically the same product, just packaged in a new box.

In summary, my advice to you is: contribute to a particular program. What program do you like? How can you make it better? Ask yourself these questions, and try to answer them on your own.
[LIST]
[*]Where is the source code?
[*]How can I run it, or compile it?
[*]What dependencies do I need? What libraries do I need?
[*]How can I run the compiler, and link the appropriate libraries?
[*]How can I add new functions to the code?
[*]What outstanding problems it has?
[*]How can I create a basic user interface? A basic window with some text and a few buttons?
[*]How can I create a basic GTK+ program with C or C++?
[*]How can I compile a basic QT program with C++?
[*]How can I talk to the developers of the program? What mailing lists, IRC channels, and forums they use?
[/LIST]

---

### Post by deadflowr on 2017-07-15
[Find a Task]("https://ubuntuforums.org/showthread.php?t=2260620")

---

### Post by cariboo on 2017-07-15
> **deadflowr said:**
> [Find a Task]("https://ubuntuforums.org/showthread.php?t=2260620")

+1 to this

---

### Post by QIII on 2017-07-15
> **vocx said:**
> 
At your age, 14 years old, no programmer will take you seriously.

Linus was 20 when he started working on Linux and 21 when he announced it.

Just sayin'.

---

### Post by vocx on 2017-07-15
> **QIII said:**
> Linus was 20 when he started working on Linux and 21 when he announced it.

Just sayin'.
What is your point?

Is your point that his age has nothing to do with it?

Or is your point that he was actually a computer scientist who knew what he was doing?

It's better to make a point, and not just imply something. Just saying.

---

### Post by QIII on 2017-07-15
> **vocx said:**
> Is your point that his age has nothing to do with it?

This.  Neither the OP's age nor Linus' age are particularly relevant.  Nor is mine ... on the other end of the scale.

---

### Post by Rocky_Bennett on 2017-07-16
A person could always start at the beginning;

[http://www.tuxradar.com/hca](http://www.tuxradar.com/hca)

---

