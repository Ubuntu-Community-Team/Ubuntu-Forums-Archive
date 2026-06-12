---
title: "Programming Languages and how to use them."
date: 2005-02-25
forum: The Cafe
---

### Post by Pitbull11188 on 2005-02-25
I'm a new linux user who would like to get my hands on some programming tools that I could learn, I currently have Visual Basic knowledge and would like to gain some python and c++ knowledge. Are there any places where I can get(or apt-get) these two programs? Also, anywhere that has some good FAQs or tutorials on said languages.

---

### Post by Yukonjack on 2005-02-25
Here you go, should get you going in the right direction.
Installing basic development tools.
sudo apt-get install build-essential

Some good links to tutorials and more.
[Python](http://www.python.org/) 
[Linoleum](http://linoleum.leapster.org/) 
[DDJ](http://www.ddj.com/) 

Lots of good info.

---

### Post by DJ_Max on 2005-02-25
Python & C++ are not programs, their languages.
Anyway, they are come default with most Linux distros, including Ubuntu.

---

### Post by Ironi on 2005-02-26
First of all, do you want to write applications primarily for Qt/KDE (C++), Mono (GTK#), or GTK+ (C)? There are ways to write e.g. C++ apps using a GTK+ interface, but in general you should decide which toolkit(s) you want to target before choosing which language(s) to learn. Python (a strictly interpreted language), OTOH, has bindings for Qt, Mono, and GTK+.

You probably won't find anything online that will teach you C++ (besides, you'll have to learn bits of C first). At least, I haven't found anything good -- I'd like to know if something is out there, though. A search on e.g. Amazon for "C++ programming" will point out a few books that you might want to buy. [Here's a list of books as well.](http://developer.kde.org/documentation/books/index.html)

Python should be easy to learn using only online sources. Here are a few links:
[http://pythoncard.sourceforge.net/learning_python.html](http://pythoncard.sourceforge.net/learning_python.html)
[http://www.freenetpages.co.uk/hp/alan.gauld/](http://www.freenetpages.co.uk/hp/alan.gauld/)
[http://docs.python.org/tut/tut.html](http://docs.python.org/tut/tut.html)

HTH

---

### Post by Leif on 2005-02-26
For learning C++, there are plenty of resources available, just google c++ tutorial, learning etc. To get you started, you can get Bruce Eckel's Thinking in C++ book online at : 

[http://64.78.49.204/](http://64.78.49.204/)
[http://www.smart2help.com/e-books/ticpp-2nd-ed-vol-two/Index.htm](http://www.smart2help.com/e-books/ticpp-2nd-ed-vol-two/Index.htm)

I haven't actually used that book, but I found his Thinking in Java very useful. And I really don't agree that you need to learn C before you can learn C++. You can learn C++ perfectly well without ever looking at C.

---

### Post by tim1 on 2005-02-26
[QUOTE=Ironi]Python (a strictly interpreted language), OTOH, has bindings for Qt, Mono, and GTK+.[/QUOTE]

I might be wrong, but does it make any sense to have mono bindings for python? I think not.
Both Python and mono have Qt and GTK bindings anyway.

greets, tim

---

### Post by jdong on 2005-02-26
tim, sure it does. What if your python app needs to call a routine from a Mono-based library? ;)

As far as what to learn, I'll risk being flamed.... **C/C++ is kind of dated**... To develop full-blown programs in C++, it takes a *long* time, compared to the newer, ultra-high-level languages (i.e. VB.NET, C#, Python, Java).

I recommend you learn Python, which is an extremely powerful yet simple-to-learn language.

I'm just starting to learn this language, too, and even this early, it doesn't fail to amaze me how instantly I become productive in it.

I'm currently writing a set of Python scripts to automate editing sources.list, installing Java, etc.

---

### Post by Leif on 2005-02-26
I can't believe I'm letting myself get dragged into this tired old flamewar  :p 

It really depends on what he wants to do with it. I personally use Java for ease and compatability. Python is probably a great choice for something that works fast, and I intend to learn it properly in the near future. But, if what you're aiming for is not necessarily GUI-based applety stuff, C/C++ have a very honourable place, and will also teach you a lot about how things work. The question is whether you really need to know the down & dirty stuff C teaches you.

---

### Post by jdong on 2005-02-26
[QUOTE=Leif] I personally use Java for ease and compatability. Python is probably a great choice for something that works fast, and I intend to learn it properly in the near future.[/QUOTE]

Umm, if you want compatibility, you really wouldn't look towards Java..... There's at least 5 implementations, each being incompatible in the tiniest ways. It provides little interactivity with the OS, which I really resent.

Python, before I learned it, I really did think of it as a "scripting language". However, even to now, I've seen nothing that's impossible to do in Python.

---

### Post by eldrich_rebello on 2005-02-26
this is off topic but please tell me how to start a c++ compiler/ide in ubuntu?
i've tried anjuta but it does'nt compile.any other ide's?

---

### Post by jdong on 2005-02-26
Please ask your question in the Programming forum. It's too off topic in this discussion.

---

### Post by Leif on 2005-02-26
[QUOTE=jdong]Umm, if you want compatibility, you really wouldn't look towards Java..... There's at least 5 implementations, each being incompatible in the tiniest ways. It provides little interactivity with the OS, which I really resent.
[/QUOTE]

Well, sticking to sun's implementation, all code I've written in java so far has worked without a glitch on linux, windows and osx. Of course, I don't need to interact with the OS, I only use it to try out algorithms for my research.

I think the thing that worries me about python is that it's so new. It's bound to go through some major changes, and may also go out of fashion as quickly as it became fashionable. I realize this may apply for a lot of languages, including java. I'm just worried that one day in a couple of years I'll get nostalgic about the oh-so-terrible programs I'm writing now, and may have to hunt down some discountinued python interpreter.

---

### Post by Pitbull11188 on 2005-02-26
Thanks for all the advice everyone! I'm probably going to try to learn python and c++ but i want to know which one is "better" as in more reliable, ease of use, and a harcore debugger or is it just personal preference. Thanks.

p.s. YukonJack I entered the command you gave me and it worked however where do i go to access the tools?

---

### Post by Leif on 2005-02-26
They are both very reliable, but for starting up I'd say python is a better choice. C/C++ shines when you need greater control, efficiency etc., which is not really necessary most of the time.  Python is very versatile, and probably easier to learn.

---

### Post by jdonnell on 2005-02-26
[QUOTE=Leif] I'm just worried that one day in a couple of years I'll get nostalgic about the oh-so-terrible programs I'm writing now, and may have to hunt down some discountinued python interpreter.[/QUOTE]

The chance are pretty slim that python will wither away since it's popular and open source. I'm sure some enthusiast or company would maintain python if Guido (the creator of python) decided to hang it up. That's the beauty of open source. The same can't be said about java. What if sun collapses and IBM decides java isn't important to IBM any longer?

---

### Post by jdong on 2005-02-26
Python ain't going anywhere. Heck Google is written in Python. Do you think Google would let Python die?

---

### Post by DJ_Max on 2005-02-26
There are quite a few popular programs writeen in both languages. Gentoo's Portage (the best package manager available). And as jdong said, Google uses Python. I'll start out with Python, it's syntax is simple, and has some good OOP.

Also, look at Ruby.

---

### Post by Yukonjack on 2005-02-26
[QUOTE=Pitbull11188]Thanks for all the advice everyone! I'm probably going to try to learn python and c++ but i want to know which one is "better" as in more reliable, ease of use, and a harcore debugger or is it just personal preference. Thanks.
p.s. YukonJack I entered the command you gave me and it worked however where do i go to access the tools?[/QUOTE]

Go to the python site and read some of the tutorials for beginner, download the tutorials you will need them to learn.
It's good way to start learning python and all the things it can do for you.
To start python start your terminal and type python it will show you the version of python you are using and will be in the python module.
To exit python CTRL-d will bring you back to the terminal.
Enjoy :)

---

### Post by jdong on 2005-02-26
[QUOTE=DJ_Max]There are quite a few popular programs writeen in both languages. Gentoo's Portage (the best package manager available). And as jdong said, Google uses Python. I'll start out with Python, it's syntax is simple, and has some good OOP.

Also, look at Ruby.[/QUOTE]

Don't forget YUM is written in Python. Notable? Perhaps. Think about how QUICKLY Fedora was able to write a clone of APT, and how well it integrates with the ANACONDA INSTALLER (err, which is written in python, too!)

---

### Post by DJ_Max on 2005-02-26
[QUOTE=jdong]tim, sure it does. What if your python app needs to call a routine from a Mono-based library? ;)

As far as what to learn, I'll risk being flamed.... **C/C++ is kind of dated**... To develop full-blown programs in C++, it takes a *long* time, compared to the newer, ultra-high-level languages (i.e. VB.NET, C#, Python, Java).

I recommend you learn Python, which is an extremely powerful yet simple-to-learn language.

I'm just starting to learn this language, too, and even this early, it doesn't fail to amaze me how instantly I become productive in it.

I'm currently writing a set of Python scripts to automate editing sources.list, installing Java, etc.[/QUOTE]
I have to agree with you there, C++ is a pain, not only it's syntax, but pointers.  :?  And it in order to write an actual useful application, you have a pretty large app. I prefer Java, but note it's not for newbies.
Also, take a look at [D](http://www.digitalmars.com/d/)

---

### Post by jdong on 2005-02-27
[QUOTE=DJ_Max]I have to agree with you there, C++ is a pain, not only it's syntax, but pointers. [/QUOTE]

Pointers are not too bad to master, but it's just that the langue isn't high-level enough, doesn't enforce good programming style, and certainly plain doesn't **make sense** in a lot of cases:

Python enforces decent indentation style. Sort of EVIL, but it works quite well. It also makes use of Exceptions, which is something that C really should do....


C: Still plenty if traces of machine behavior. YOU CANT RETURN FRICKIN ARRAYS

---

### Post by mark on 2005-02-27
I've become interested in learning *some* new programming language, probably something like Python.  My last programming experiences were in 808x/Z80 assembly language, self-defensive BASIC (both interpreted and compiled) and enough TurboPascal (does that date me?) to convert a printer utility I wrote in assembler for CP/M to a .EXE for DOS.

I guess what I'm looking for is more of a "best practices" document in current programming techniques.  I'm reminded of a book I once had called (don't laugh!) *The Little Book of BASIC Style*.  Rather than attempting to teach the language, it tried to impart generally sound programming practices (I know, I know - "sound programming practices" and BASIC is an oxymoron).  Anybody know of anything like this, a little more up-to-date?

(Hopefully, I'm not "brain-damaged" by my earlier use of BASIC to the extent that I can't learn any new tricks...)

---

