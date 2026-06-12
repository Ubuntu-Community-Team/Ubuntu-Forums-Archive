---
title: "settings won't open just goes through motions and nothing"
date: 2019-04-26
forum: Ubuntu Development Version
---

### Post by andreacristiano on 2019-04-26
so for some reason settings wont open no matter what I try they just stopped working any help??

---

### Post by andreacristiano on 2019-04-26
(gnome-control-center:12666): GLib-GIO-ERROR **: 08:56:43.033: Settings schema 'com.system76.hidpi' is not installed
Trace/breakpoint trap (core dumped)
this is the error I get

---

### Post by dino99 on 2019-04-26
Can you share with us some details: which DE ? maybe a screenshot or a detailled howto reproduce that problem. Also tell us details about the config, in case it can be hardware related.
Can you get details from a terminal command, or some error logged into journalctl ?

From your previous post, you might get more support from system76 forum
[https://support.system76.com/articles/hidpi-multi-monitor/](https://support.system76.com/articles/hidpi-multi-monitor/)

---

### Post by andreacristiano on 2019-04-26
I just tried something out of the blue and it worked!


**sudo apt-get install hidpi-daemon**

---

