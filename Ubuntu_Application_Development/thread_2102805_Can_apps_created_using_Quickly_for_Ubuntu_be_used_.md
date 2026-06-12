---
title: "Can apps created using Quickly for Ubuntu be used in other linux distros?"
date: 2013-01-08
forum: Ubuntu Application Development
---

### Post by styk3 on 2013-01-08
I need to write a small program to update my mongodb. I'm currently on ubuntu but I need to use it on other linux distributions. I would just like to make sure that applications using this method:

[http://developer.ubuntu.com/get-started/](http://developer.ubuntu.com/get-started/)

Can be run on other distros?

---

### Post by Cheesemill on 2013-01-08
You will need to repackage your application for the other target distros but apart from that you should be fine.

Quickly uses Python and the pygtk toolkit to produce applications, so they should run on any Linux that has these packages available.

---

### Post by styk3 on 2013-01-08
> **Cheesemill said:**
> You will need to repackage your application for the other target distros but apart from that you should be fine.

Quickly uses Python and the pygtk toolkit to produce applications, so they should run on any Linux that has these packages available.

Thank you. Haven't developed outside the web before so this is new to me, but I'm sure I'll find out how to do this as I go along.

---

