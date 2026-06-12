---
title: "Learning Python - useful? Inputs.. please."
date: 2008-07-09
forum: The Cafe
---

### Post by hellmet on 2008-07-09
Everybody I know already knows or is learning Java. I'm sick of hearing about Java now, and I've decided to learn something new. Like Python. I've heard Python is like Java, easy, and very powerful. But, I'm yet to see openings in Python (atleast in my city).

I want to know if learning this language would be useful - career wise, and if it actually is useful - otherwise.

Thanks for your inputs!!

---

### Post by bruce89 on 2008-07-09
Career wise, probably not.

I assume it's because companies don't like their source code visible (Python's interpreted).

---

### Post by regomodo on 2008-07-09
`

---

### Post by Mr. Picklesworth on 2008-07-09
Python is very useful. It's a well respected language, and is used *frequently* in the open source community. For example, Ubiquity (Ubuntu's installation wizard) is written in Python, as well as gnome-app-install! Contribution to open source projects looks good on a resume, unless said resume is going to a company that is opposed to what I assume are your allegiances. While I have only a year of experience in that lesson, I have learned that working for such a company is not a great thing for the soul.

Because Python is used so widely, you can also expect there to be lots of Python bindings for the libraries that matter. There are even bindings for the Ogre 3D engine :)
Really any GNOME stuff, be it glib, libwnck, gtk, gdk, Glade, dbus, etc. works with Python. Lots of panel applets are written with the language. Python apps are often desktop integrated, which is really unusual for a cross platform scripting language. I think this is helped by core Python not being polluted by arbitrary modules such as 'one size fits all' UI libraries. (If you really need, I believe wxwidgets works). If you were to poke around with apt-get source, I think you might be surprised by how many things here are written in Python. Isn't it cool? Impossible to guess without seeing the source!
Other cross-platform languages like Java just don't work out that way. I immediately admit that I do not know Java very well, but it seems to me that Java is all about being one tight (and huge) package which can be pushed smoothly from platform to platform. Actual platform-specific code is not a simple act. As a result, a Java app can "just work", but also stands out like a sore thumb.

Having said that, I must say I rarely encounter Python in the commercial software world (to which I have very little exposure), although it reportedly has many applications for high-end tech organizations like NASA. It is, however, really fast, easy to learn, powerful (nice bonus from being a scripting language, making stuff like runtime reflection dead easy) and great for group projects since messy Python code is an impossibility.

It has a lot of math functionality, again helped by being a scripting language with "duck typing". Some people use the Python shell as a calculator because it handles all sorts of crazy numbers without complaining. Hash tables (crazy fast dictionary lookups) are handled automagically by the Dictionary data type, which means way less work on the developer's end and really good performance because, let's face it, the developer would not have bothered otherwise.

---

### Post by bruce89 on 2008-07-09
> **regomodo said:**
> It's likely that i'm wrong, but i thought there was a way to "compile" Python to a nice binary?

AFAIK, you can turn it into bytecode, but it's easily reversed.

> **Mr. Picklesworth said:**
> For example, Ubiquity (Ubuntu's installation wizard) is written in Python!

That explains a lot.

---

### Post by cdekter on 2008-07-09
> **bruce89 said:**
> AFAIK, you can turn it into bytecode, but it's easily reversed.


Actually the same is true for Java - .java files are compiled into .class files, which are bytecode, and put into a .jar (which is really just a zip file). Google a program called "Jad" and you will see, Java programs can be very easily decompiled.

---

### Post by dracule on 2008-07-10
I love python. I use it A LOT.

Python is just marginally slower than C in a lot of stuff with psyco, but like 99.99% of the time you will not see a difference if you are beginning but as you go along you can write stuff in C. also psyco jacks up the speed alot. 

Yeah, python isnt that great for the commercial world. Probably if there was a way to hide your source, companies would use it more. 

but in the opensource world it is very popular. 

I think i remember reading that someone wrote an operating system in almost all python. that is pretty impressive. 

I learned Java. it is a fat pig, I really really dislike it. but it was for a class so i had to learn it.

---

