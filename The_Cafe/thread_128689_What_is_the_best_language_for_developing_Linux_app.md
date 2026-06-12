---
title: "What is the best language for developing Linux applications?"
date: 2006-02-12
forum: The Cafe
---

### Post by sbasak on 2006-02-12
There are so many to choose, like C++/Python/TCL-TK etc., that I am confused!

Is there any language which is capable of developing Window like application in Linux?

I tried Mono in Knoppix, but looked like it is not stable.

Thanx for suggestions!

;)

---

### Post by prizrak on 2006-02-12
The best language is C++ for anything :). Graphical front ends well there are many choices. GTK+ is nice and easy, there is also Qt. There is Java if you don't need speed, kinda depends on what you are looking for.

---

### Post by drfalkor on 2006-02-12
C/C++ and python (I'm not sure),... And using the gtk+ lib files ! :)

---

### Post by papangul on 2006-02-12
For net oriented applications java is a good choice.
For fast, lightweight frontend based applications you might find fox-toolkit useful. [http://www.fox-toolkit.org/home.html](http://www.fox-toolkit.org/home.html)

---

### Post by wrtpeeps on 2006-02-12
that question is really a matter of opinion.

---

### Post by somuchfortheafter on 2006-02-12
my vote goes to python or c++

---

### Post by GeneralZod on 2006-02-12
C++ or Ruby :)

---

### Post by Lovechild on 2006-02-12
C#

---

### Post by atoponce on 2006-02-12
[quote=wrtpeeps]that question is really a matter of opinion.[/quote] I agree.  More than opinion though, rather than deciding what language is best for all Linux apps, you need to decide what language will best suit you or your clients needs.  Sticking to just one language, IMHO, is suicide if you are a contractor.  A programmer should be as dynamic as the clients he/she serves.  That may even include programming non-Linux applications.

---

### Post by kleeman on 2006-02-12
Fortran???

---

### Post by ssam on 2006-02-12
if you are new to programming python is very good. its easy to learn and you can use gtk or glade to make it look like any other ubuntu application. its not the best for raw speed, but you can always recode the bottle necks in C if you need. the built in agorithyms like sort() are already coded in optimised C so they are pretty fast.

if you are making applications that are more processor bound (maybe graphics editing) then C/C++ might be faster, but it takes longer to learn and longer to develope an an application.

C# / mono, is interesting. there are lot of good desktop apps being built with it currently, (f-spot, muine etc). you may want to research the politics behind it and see if you agree. (please no flames)

java has issues similar to mono. (although the free java implementations are coming along well) lots of people consider java slow, but this may be an old misconception.

---

### Post by ebash on 2006-02-12
Try using an interpreted language like Perl, Python or Ruby.
Do not get fooled by the misconception that you code will be slow, it won't. Plus you won't believe how fast you will be making your application.

If you use GTK then I strongly suggest that you use glade for all of your GUI. You will then just need to concentrate on the functionality of your application, no need to fight with layout problems.
Using glade has great advantages because your GUI is all encapsulated in a XML file, if you really like to change the programming language all that you need to do is take your XML glade file and implement the callbacks in the other language. It is as simple.

If you like programming with an IDE then you might want to consider Java with Eclipse and the Java Gnome bindings. You will code slightly more than with a scripting language but on the other hand you will have the IDE to assist you. Take a look at [ Java-Gnome and Eclipse]("http://java-gnome.sourceforge.net/cgi-bin/bin/view/Main/EclipseDevelopment")

---

### Post by ebash on 2006-02-12
For simplier things some times a few bash lines with zenity can make GUI application.

[zenity]("http://freshmeat.net/projects/zenity")

---

### Post by sbasak on 2006-02-13
Thanks chaps for answers.

Let me clarify something. I want to develop applications in Linux for fun and not for a living! I already know VB.NET and C/C++. I don't have any problem with C/C++ but the only caveat is that I've developed only console mode applications in C/C++ and all Windowed applications in VB.NET. Developing GUI with C/C++ code looks like daunting to me.

So, I need basically something where I can draw GUI very easily. 

One more thing, as I use Knoppix & Ubuntu mainly, the applications I develop, should be ready to run in these Linux distros. Since they both use Debian, am I correct in guessing that an executable compiled with C/C++ in Knoppix will work in Ubuntu (and vice versa)?

Thanx.

---

### Post by gord on 2006-02-13
C/Python + wxwidgets to handle the gui. works on loads of stuff so your application won't be tied down to gtk or something like that, you can use c++ as well but i don't see the point if you use python ;)

---

### Post by stimpack on 2006-02-13
For fun = python, most fun language ive ever learnt except for 68000 on an Amiga. If I was coding a big app it would still be C but for everything else I use python, its a joy.

---

