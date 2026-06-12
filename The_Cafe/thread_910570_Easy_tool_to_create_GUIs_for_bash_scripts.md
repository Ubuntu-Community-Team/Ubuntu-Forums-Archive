---
title: "Easy tool to create GUIs for bash scripts"
date: 2008-09-04
forum: The Cafe
---

### Post by Nonno Bassotto on 2008-09-04
During casual browsing I came across [this project]("http://buc.opensource.tk/"). It allows you to create GUIs for your bash scripts using just some XML. It took me a few minutes to write my first interface, just had to declare the elements I wanted to appear and a script associated to each button and so on.

The GUIs you can create are quite basic (for now at least), and in QT, but still nicer than zenity. For example I created an [alternative interface]("http://ubuntuforums.org/showpost.php?p=5723220&postcount=543") for the formidable [avatar-factory]("http://ubuntuforums.org/showthread.php?t=486359") by Yuzem (if you don't know what this is, be sure to check it out!).

This tool could be used for example to create graphical programs to accompany small tutorials. To install it, use the repositories
```

deb http://buc.billera.eu/ubuntu/ binary/

```
for 32 bit or
```

deb http://buc.billera.eu/ubuntu64/ binary/

```
for 64 bit. If you don't want to mess with the repositories, you find [here]("http://buc.billera.eu/portale/html/modules.php?name=Downloads&d_op=viewdownload&cid=2") the debs.

To run any program written with BUC, just do
```

buc pathoftheprogram.mc

```

Hope you like it as much as I did ;-)

---

### Post by Nonno Bassotto on 2008-09-10
Bump... is anybody just curious to try it out? :)

---

### Post by pp. on 2008-09-10
You may not have noticed, but with the exception of the license information all texts appear to be in Italian. I might be able to puzzle out what some of it means if I am very patient. However, I am not confident enough to try that software if I don't know what I am doing.

---

### Post by cmay on 2008-09-10
hi.
did you try post in programming talk. maybe there there are some there that could find it useful. by the way i hope you got my pm with last string  translation. 
thanks for sharing with us :)

---

### Post by qazwsx on 2008-09-10
There is also Kommander. [http://kommander.kdewebdev.org/](http://kommander.kdewebdev.org/)
But it is not limited to bash

---

