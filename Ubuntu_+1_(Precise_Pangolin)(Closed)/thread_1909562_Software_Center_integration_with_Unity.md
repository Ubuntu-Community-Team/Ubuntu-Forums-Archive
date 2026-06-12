---
title: "Software Center integration with Unity"
date: 2012-01-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-01-15
[https://code.launchpad.net/~bilalakhtar/unity/software-center-integration-for-o/+merge/71905](https://code.launchpad.net/~bilalakhtar/unity/software-center-integration-for-o/+merge/71905)

Interesting merge proposal. The link includes the testing procedure.

Regards,
Effenberg

---

### Post by ronacc on 2012-01-15
I wonder what this will do to gnome-shell , will it lose software center ?

---

### Post by jbicha on 2012-01-15
This has nothing to do with GNOME Shell. Think of it as a bonus integration feature for those using Unity; Software Center will continue to work fine with other desktops.

---

### Post by MG&amp;TL on 2012-01-15
I think the better integrated Unity gets; the better people will think of it. Particularly as we still get people asking how to use apps not in the launcher.

---

### Post by t1497f35 on 2012-01-15
The software center feels heavy weight: cold start ups take like 4-8 seconds to start, I care about this more than about wiggling icons. But since it's written in a scripted language I'm unsure if the startup time issue can be fixed.

---

### Post by MG&amp;TL on 2012-01-15
> **t1497f35 said:**
> The software center feels heavy weight: cold start ups take like 4-8 seconds to start, I care about this more than about wiggling icons. But since it's written in a scripted language I'm unsure if the startup time issue can be fixed.

I think they're focussing on speed this release.

Not as bad as you'd think, do a few "file"s in /usr/bin/, quite a few are python scripts.

Lightweight alternatives are available.

---

### Post by t1497f35 on 2012-01-15
> **MG&TL said:**
> I think they're focussing on speed this release.

Not as bad as you'd think, do a few "file"s in /usr/bin/, quite a few are python scripts.

Lightweight alternatives are available.
Sure, but while a small python script is a good choice for a script - and as fast as any other script, doing rather big and sophisticated desktop applications, like the software center, shouldn't be done in a scripted language. Vala is lately used as a substitute for scripted/interpreted languages since Vala has matured quite a lot lately. Not starting a programming language war here, mind you, just saying that it's better to use fast/compiled languages for big apps that are central to Ubuntu. By choosing a scripted language you develop the big app faster but the big app performs more slowly because aside from a scripted language being a priori slower, you also need time to parse the file, check for errors, compile it and only then start executing it - it takes time and CPU cycles doing it every time you launch a scripted app.
Of course there's also the HDD playing a big role, but it would be a start.

---

### Post by MG&amp;TL on 2012-01-16
> **t1497f35 said:**
> Sure, but while a small python script is a good choice for a script - and as fast as any other script, doing rather big and sophisticated desktop applications, like the software center, shouldn't be done in a scripted language. Vala is lately used as a substitute for scripted/interpreted languages since Vala has matured quite a lot lately. Not starting a programming language war here, mind you, just saying that it's better to use fast/compiled languages for big apps that are central to Ubuntu. By choosing a scripted language you develop the big app faster but the big app performs more slowly because aside from a scripted language being a priori slower, you also need time to parse the file, check for errors, compile it and only then start executing it - it takes time and CPU cycles doing it every time you launch a scripted app.
Of course there's also the HDD playing a big role, but it would be a start.


I agree, but frankly, if you know that, you could probably use APT directly far faster than using any frontend. 

I would also point to you LSC, a light software centre being developed for 12.04. There's a launchpad page you can get a PPA or tarball from. That's in python too, but we're planning a vala port, and the python app is very light to start with.

---

### Post by effenberg0x0 on 2012-01-16
I totally agree using apt directly is unbeatable in terms of speed. But I like the concept of Software Center, specially considering the average PC user. The idea of having a properly formatted GUI / friendly description of the software, with screenshots, reviews, one-click install, etc. It makes sense for the non-IT users out there. 

And I fully agree to t1497f35. I'm not a Python specialist, I've only been looking into it recently. IMO, code optimisation in Python can help but it's not magic. Sure, routines in C can be embedded, but it looks like that's not something Python developers like to do commonly. And, if that was the case, why not go C/C++ from scratch? 

Don't take me wrong here (also not trying to start a language war): I appreciate Python RAD aspects, it's very cool in many aspects. But I disagree it is the best choice for larger projects. Vala, on the other hand, sounds like a more valid option (if developers want to avoid C/C++ - it seems like the tendency these days). AFAIK vala source code is converted into C code and only then compiled normally via gcc. So there's no performance loss. It's a good idea.

---

### Post by lucazade on 2012-01-16
While Vala is a great option, I still prefer the Python-Cython combination, especially for gtk apps.
> Cython is a language that makes writing C extensions for the Python language as easy as Python itself. Cython is based on the well-known Pyrex, but supports more cutting edge functionality and optimizations.
The Cython language is very close to the Python language, but Cython additionally supports calling C functions and declaring C types on variables and class attributes. This allows the compiler to generate very efficient C code from Cython code.
This makes Cython the ideal language for wrapping external C libraries, and for fast C modules that speed up the execution of Python code.

Obviously c++ for qt4 stuff..

---

