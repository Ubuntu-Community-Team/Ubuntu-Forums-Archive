---
title: "Develop something in Gnome and try to learn C++?"
date: 2010-03-14
forum: The Cafe
---

### Post by Kdar on 2010-03-14
I had few C++ classes before, basic class and class which touched on object oriented programming, trees, arrays.. etc

But I never had chance to make that programming somewhat meaningful  (just doing different in class assignments for programming from command line).

Can I develop something for Gnome or KDE? 
I just want to have experiance using this programming skills and see it do something, not just some programs from command line.

Is there some tutorials on this? At least to create simple things.

---

### Post by JDShu on 2010-03-14
Gtk and Qt libraries are probably what you're looking for. Go check them out. In addition if you want to make games, Allegro and SDL are two libraries that you can access.

---

### Post by Kdar on 2010-03-14
Gnome is using C? right? So if I want to continue using C++ should I develop something under Qt? or

---

### Post by JDShu on 2010-03-14
Google is your friend ;)

C++ interface:
[http://www.gtkmm.org/](http://www.gtkmm.org/)

Qt uses C++ by default. There are other interfaces should you need them.

---

### Post by Kdar on 2010-03-14
What is difference between Gtk+ and Gtkmm?

Banshee is made using C++, I think, right?

---

### Post by matthew.ball on 2010-03-14
There's also a really nice cross-platform "native" widget framework available for C++ - [wxWidgets]("http://www.wxwidgets.org/").

If you want a GUI builder for it, there's [wxFormBuilder]("http://wxformbuilder.org/").

---

### Post by OutOfReach on 2010-03-14
> **Kdar said:**
> What is difference between Gtk+ and Gtkmm?

Banshee is made using C++, I think, right?

The original GTK toolkit is written for C, just plain C. Gtkmm just provides a C++ interface to GTK, making things a bit more object-oriented.

Banshee isn't made in C++ actually, it's made in C#.

---

