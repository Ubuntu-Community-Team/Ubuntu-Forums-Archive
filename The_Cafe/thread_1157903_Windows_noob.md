---
title: "Windows noob"
date: 2009-05-13
forum: The Cafe
---

### Post by nothingspecial on 2009-05-13
I`ve now got a desk and a pc. A very old looking one.

I don`t want to use windows really, I`m not familiar with it.

I am allowed to install ubuntu on one condition - that I can get the windows specific software to work. Dual booting is no good because I can`t boot windows every time the phone rings. 
It is business software ie it does sales processing, customer records, sales history, invoicing, etc etc.

The IT bloke says he`s not helping - fair enough.

Would a virtual machine cut it? How easy is it to run windows software in a VM.

Is there an opposite of wubi?

Should I just forget it and do what I`m supposed to be doing instead of messing about with linux at work.

---

### Post by damis648 on 2009-05-13
A VM would probably work fine; just
```
sudo apt-get install virtualbox-ose
```
and go from there.

---

### Post by skymera on 2009-05-13
WUBI isn't a virtual machine. It's Ubuntu but installed inside Windows.

Virtual Machines work well, i run XP in one on Ubuntu 7.04.

---

### Post by nothingspecial on 2009-05-13
Ok I`ll give it a go.

---

### Post by HavocXphere on 2009-05-13
Your options are either using WINE or Virtualbox (or something like it).

I'd go with Virtualbox with XP in it. Be sure to install guest additions (just google...you'll find info).

I would strip down the XP install as much as possible too. Switching off all the window effects should make a noticable difference.

Don't put Vista in virtualbox VM...it works but its not fun.

---

