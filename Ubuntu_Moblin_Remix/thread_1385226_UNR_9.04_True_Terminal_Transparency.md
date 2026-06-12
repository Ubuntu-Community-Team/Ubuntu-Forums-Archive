---
title: "UNR 9.04 True Terminal Transparency?"
date: 2010-01-19
forum: Ubuntu Moblin Remix
---

### Post by NOX89 on 2010-01-19
Hello,

I just bought the 1005HA from Newegg, and I installed UNR 9.04 because I like it better than 9.10. I finally got time to set it all up to my specifications, and the one thing I cannot get to work for the life of me is the transparency in the terminal. I use the terminal transparency a lot with programming, and specially with a screen so small I would love to have it. The only way I got this to work in my desktop dual boot to Fedora was to install Compiz-Fusion, and I was thinking for such a small install there has to be an easier way to get this to work!

I would be grateful for anyone who can help me! ^_^

---

### Post by arubislander on 2010-01-19
> **NOX89 said:**
>  The only way I got this to work in my desktop dual boot to Fedora was to install Compiz-Fusion, and I was thinking for such a small install there has to b

For transparency you will need to enable compositing. A sure bet is indeed, installing Compiz. But maybe enabling Gnome compositing would also work... Anyone knows for sure?

---

### Post by NOX89 on 2010-01-19
> **arubislander said:**
> For transparency you will need to enable compositing. A sure bet is indeed, installing Compiz. But maybe enabling Gnome compositing would also work... Anyone knows for sure?

How To Enable Compositing:

Step 1:
```
$ gconf-editor
```Step 2:
Go To apps > metacity > general

Step 3:
Check compositing_manager, your screen may flicker while it is reloading the Windows Manager.

---

Thank you arubislander, I appreciate your help :)

---

### Post by arubislander on 2010-01-22
> **NOX89 said:**
> Thank you arubislander, I appreciate your help :)

Glad to have been of some assistance :)

---

