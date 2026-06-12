---
title: "Programming for Linux"
date: 2006-04-24
forum: The Cafe
---

### Post by CornMaster on 2006-04-24
Ok...be gentle.

I think I've finally made the switch to linux, and I'm interested in porting some of my applications to native linux languages.  Now there is no easy way to do this, so I'll probably have to rewrite...because most of my programs were in Visual Basic (hold back the tomatoes).

I know a little Java, and Perl.  I can also do some rudimentary shell scripting.  I've taken some programming classes in university, so I have a decent understanding of OO languages, but I never got to the point if designing GUIs, and if I want to make programs on Linux for public consumption, I'd really like to have a GUI, since I want to help attract new users by making stuff easier and more familiar.

So, I was reading somewhere that I can make interfaces with perl and Gnome/GTK+ but since I'm new to linux, I don't know what would be the most portable toolkit.  I was considering using Gambas, since it's similar to Visual Basic, but I wasn't fussy about it's stability and really couldn't figure out what was needed to make programs run on others computers.  I don't want to have my apps tied to either Gnome or KDE, and I'd like an easy way to draw interfaces (or at least a good tutorial on how to do them in code).

So, given these points, can anyone recommend a language/direction for me to take?

Most of my apps do not do any hardware access, or any specific OS functions, mostly just file maniuplation.

---

### Post by Compucore on 2006-04-24
Have you done some C++ programming as well by any chance> I know that you stated that you have done Visual basic. The reason why I am asking this is that with Ajunta for C++ and Eclipse for java programming would probably be your best bet for that. Maybe the others may know more than I do on this part. But at least with these two its a start in porting your applications that you have done from VB to linux. Does it have any naming conventions used from either java or C++??

COmpucore

---

### Post by Master Shake on 2006-04-24
If you did Visual Basic, try RealBasic.  It's a lot like VB, and VB apps can be ported to it.

As a plus, RealBasic is free for linux. ($100 for either the Win or PC versions)

---

### Post by Kvark on 2006-04-24
I'd suggest you try Python, it gets the job done quicker and neater then most languages. Check out [Python's official website]("http://www.python.org/about/") and the [Wikipedia article about Python]("http://en.wikipedia.org/wiki/Python_programming_language").

---

### Post by ssam on 2006-04-24
python and glade might be a good way to go. there are tutorials.

---

### Post by pianoboy3333 on 2006-04-24
Well, I know WxWidgets is pretty easy to use. I'm no expert, but I believe it uses what ever API the user has installed, so on Windows, it will use the windows API, on gnome, it'll look like GTK2, and on KDE, it'll look like a KDE app.

---

### Post by CornMaster on 2006-04-24
Everyone is saying that python is the new way to go.  So that's something I have to learn.  Also need to learn PHP for a project I'm working on this summer.

RealBasic seems pretty interesting.  If I were to write something in the Linux version, it would compile with the professional version and work cross platform right?  I ask because I'm working on a program for a friend...it was nearly finished in VB, but he stopped paying me, so I stopped working on it.  He's almost back on his feet, and if he wants me to finish it, it might be cool to have a cross platform version.  He would need to buy a professional license, but it should all be compatible.

I've looked at Glade as well.  At first look, it went over my head....and I haven't had time for a second.  Thanks for the suggestions.

---

### Post by Master Shake on 2006-04-24
The way I understand it, that is indeed the way RealBasic is supposed to work.

---

### Post by darkmatter on 2006-04-24
Python is a good way to get into programming for Linux... if your up to it, I'd also recommend Ruby... C is the 'standard' for GNOME... but you can use C++... even some C# if your into that kinda thing.

For toolkits, WxWidgets is probably the most portable.

And brush up on yer XML while your at it. ;)

---

### Post by futz on 2006-04-24
Another vote for Ruby and the ruby/gnome/gtk lib. It's a bit like perl, only less funky (I love perl). I just started learning Ruby and like it so far. Nice language.

Python is great too.

---

