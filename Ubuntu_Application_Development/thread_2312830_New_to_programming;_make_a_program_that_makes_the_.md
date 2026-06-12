---
title: "New to programming; make a program that makes the screen flash when button is touched"
date: 2016-02-07
forum: Ubuntu Application Development
---

### Post by starrtennis on 2016-02-07
Hi there. I'm new to programming--I've done some basic Java and Python in the past, but I've forgotten most of it.

I'd like to get back into it.

I was thinking a cool starter project would be to create a button in the top window tray that when you click it, it makes the screen flash.

What do you think would be the appropriate language and IDE to do this?

Many thanks.

Michael

---

### Post by ian-weisser on 2016-02-08
Any language with dbus bindings.
Most of what you will be doing is sending and receiving dbus messages and signals.
An IDE won't help much for that.
You can easily learn it in plain old Terminal.

---

