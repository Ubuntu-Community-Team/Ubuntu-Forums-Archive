---
title: "Vala language as a new way of development"
date: 2010-02-03
forum: Ubuntu Dev Link Forum
---

### Post by opengl_cpp on 2010-02-03
One of the worst problem when you try to develop and gui application is the variety of options available for linux. Although it can be seen as an advantage for linux, it could confuse both developer and end-users to run the application. 

And as we know, this is not the case with other OSes Like windows or BeOS/haiku and of course macosx.

since linux has no official desktop for itself you can develop your app using gtk+, gtkmm, qt, wxwidget, tk, fltk, ... Besides, all of these libraries have their own bindings to different languages such as C, C++, D, C#, Java, Perl, python...

All of these approaches are good in fact, but the problem is that if you are using GNOME desktop, you may find that you need some application that are natively compiled for KDE desktop, so to bring that app to life you have to download all its KDE dependencies. it is the same case for KDE users.

It can be said that in some situation the stability of non-native apps are lower and you may lose some of the app's functionalities. the problem can be worsen if you include some other minor desktop environments.

Anyway, ubuntu is based on GNOME desktop, and if we assume ubuntu is the most remarkable distro among other gnu/linux distos, then we can say GNOME desktop is the most popular gnu/linux desktop (:Dkubuntu --> KDE!!!:-$).

But it always was a big pain for me to work with gtk+ library, because It is written using C lang. C is a powerful lang but not for desktop apps, and its gtkmm is just a warper around gtk+ for C++ users.

My favorite lang is C++, but i think is not highly suitable for desktop app as its predecessor C. These two languages can take a developer a lot of time to create a full stable release of an app, hence we need another lang to accelerate our development process. C# is not a good choice, because of the managedcode it produces and heavy runtime overload on any typical App based on it, and above all it is a microsoft product . Java is somehow ...:confused: I dont know ... but you can see _not many_ (i said: not many useful, and not any useful) useful Apps developed by Java for linux users. Java has its own advantages, however.

So what remain for us?

After a lot of hardship in using gtkmm and wxwidget yesterday i found a new remedy. VALA language.

It has a similar syntax to C# but wont produce managedcode. it is translated to C code and compiled with gcc(isn't it funny:p). Additionally, it is build around GObject (heavily used in gtk+ apps). 
Vala can accelerate your development process dramatically while debugging is painlessly easy. Since it is compiled into binary code its runtime speed could be significantly good.

After all I have to mention that the words above are my opinion and C/C++ are my favorite Langs forever, but i think it is a good practice to uses tools in their particular time and place. In other words, when the execution speed is a big concern then C/C++ are the best choices, though VALA has a good speed as i mentiond before.

I forgot to say Vala can not eliminate the portability issue among various desktop environments, but could be a good choice for GNOME developers. It doesnt mean that it cannot be used by KDE users or even windows, mac. There are some ports of Vala to windows and Mac, and since it is based on GObject and GObject itself has already ported to many platforms you can keep multiplatform plans in your mind.

Now what is your idea?

---

### Post by ibuclaw on 2010-02-04
I've personally always wanted to add Vala to my list of "things /me can do well", but have never quite gotten round to it.

Instead, I still mostly work in C, D and Perl and Shell. :)

Regards
Iain

---

### Post by estiedi on 2010-06-29
Discovered Vala only a couple of weeks ago, tried it, love it.
Thumbs up for Vala!

---

### Post by Tahakki on 2010-06-29
Surely PyGTK is a good solution for this? It's easy and relatively cross-platform, though it's not compiled.

---

### Post by ibuclaw on 2010-06-29
> **Tahakki said:**
> Surely PyGTK is a good solution for this? It's easy and relatively cross-platform, though it's not compiled.

Vala is just a GObject preprocessor for C. Can't really get more cross-platform than that really. ;)

---

