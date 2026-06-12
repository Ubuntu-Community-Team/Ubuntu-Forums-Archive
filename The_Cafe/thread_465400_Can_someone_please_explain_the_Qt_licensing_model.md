---
title: "Can someone please explain the Qt licensing model?"
date: 2007-06-05
forum: The Cafe
---

### Post by Kimm on 2007-06-05
I'm thinking about writing a program. I want the entire program to be Open Source, but in order to actually gain something from it (this would substitute my lack of work at the moment), I would want to restrict the amount of spreading possible. I would still prefer to use the Open Source version of Qt4.

In their Business Model I read this:
"If you wish to use an open source version of Trolltech's products, you must contribute all your source code to the open source community at large, according to the terms of the applicable open source license."

Earlier in the text they refer to the GPL, but this quote makes me wounder if it has to be the GPL.

So... I guess my question is this... would it be OK for me to use, say the Creative Commons Attribution-Noncommercial-No Derivative Works 3.0 License?

PS.
This software would later be licensed as GPLv3 :)

---

### Post by Luggy on 2007-06-05
If you don't want to have to pay to use QT you must give your source code and licence your code under the GPL.

If you do not want to give out the source code or use the GPL you have to pay to use QT.

> If you are using Qt commercially - that is, for creating proprietary software for sale or use in a commercial setting - you must purchase a commercial license from Trolltech. **Alternatively, if you wish to write Open Source software you can use the Open Source version of Qt, released under the GPL. _If you use the Open Source version you must release your application and complete source code under the GPL as well._**
[http://trolltech.com/developer/knowledgebase/114/]("http://trolltech.com/developer/knowledgebase/114/")

---

### Post by Tuna-Fish on 2007-06-05
> **Kimm said:**
> I'm thinking about writing a program. I want the entire program to be Open Source, but in order to actually gain something from it (this would substitute my lack of work at the moment), I would want to restrict the amount of spreading possible. I would still prefer to use the Open Source version of Qt4.

In their Business Model I read this:
"If you wish to use an open source version of Trolltech's products, you must contribute all your source code to the open source community at large, according to the terms of the applicable open source license."

Earlier in the text they refer to the GPL, but this quote makes me wounder if it has to be the GPL.

So... I guess my question is this... would it be OK for me to use, say the Creative Commons Attribution-Noncommercial-No Derivative Works 3.0 License?


That is not an open source license, so no. The minimum limit for OS licenses is no limits on derivative works, and no limits on use or distribution, sources included. Otherwise you could call MS's shared source initiave OS. If you want to benefit from a Qt4 program commercially*, you have to pay Trolltech. Their position on their work is thus quite the same as yours.

What you could do is use GTK, it is LGPL so you can link to it from anything.

(* The usual disclaimer about that selling a product is not the only way to make money, software as a service is legal here if it is licensed under appropriate license.)

---

### Post by Luggy on 2007-06-05
I'm not sure about the fine points in whether or not you could sell GPLed code... if you could then there you go. 

I'd still stick with QT though. It's sex in C++ form.

---

### Post by Kimm on 2007-06-05
Thanks for clearing this up!

Yes... I thought about using GTK, but I find that it doesn't integrate very well in Windows. I also looked into wxWidgets, but in the end I found that wxWidgets was to much to learn... while I have some experiance with Qt4 (and I find it to be (as Luggy so nicely put it) "sex in C++ form.")

Edit:
Oh! and btw.. I'll be going with the GPL afterall ^^

---

