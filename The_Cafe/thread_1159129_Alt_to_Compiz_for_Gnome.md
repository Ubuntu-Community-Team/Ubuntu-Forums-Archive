---
title: "Alt to Compiz for Gnome?"
date: 2009-05-14
forum: The Cafe
---

### Post by stwschool on 2009-05-14
It seems to me that Compiz is a bit ropey. It just doesn't play nice with ATI drivers, causing a flickering effect on movies, etc, and a common solution to gnome issues does seem to be to turn compiz off.

The trouble is, its functionality is very useful. Things like compositing allowing me to use Docky, and Expo, are much appreciated.

Now I notice KDE doing all this so much more smoothly, and what's more working on an ATI driver, but the problem here is that I honestly don't get on as well with KDE as I do with gnome.

So the question.. is there an alternative that will give me compositing, gnome and Expo (to be fair it's the only effect I use but it's great for eye-candy and with 8 desktops on it (or 12 if I'm feeling adventurous) it's a great boost to my productivity).

---

### Post by coldReactive on 2009-05-14
Yeah, same here, I don't like KDE much, but I would love an alternative to compiz. It also has to integrate into metacity like the current compiz does.

---

### Post by RaZe42 on 2009-05-14
For expo I don't know, sorry. But If you only need compositing you can always enable the metacity built-in compositing

```
gconf-editor
```

go to apps > metacity and change the compositing option from false to true (From the top of my head, someone correct me if I'm wrong)

---

### Post by stwschool on 2009-05-14
> **RaZe42 said:**
> For expo I don't know, sorry. But If you only need compositing you can always enable the metacity built-in compositing

```
gconf-editor
```

go to apps > metacity and change the compositing option from false to true (From the top of my head, someone correct me if I'm wrong)
Interesting, you learn something new every day, now if I can just get that expo alternative (can't live without it, I'm that sad).

---

### Post by Regenweald on 2009-05-14
> **RaZe42 said:**
> For expo I don't know, sorry. But If you only need compositing you can always enable the metacity built-in compositing

```
gconf-editor
```go to apps > metacity and change the compositing option from false to true (From the top of my head, someone correct me if I'm wrong)

No you're correct, Docky works just fine with Metacity compositing, until just yesterday my machine was compiz free and i had no compositing problems at all.

---

### Post by Mr. Picklesworth on 2009-05-14
Didn't Mandriva have a neat compositing window manager going?...


Oh aha!
[http://polishlinux.org/apps/window-managers/metisse-you-thought-you-knew-what-3d-was/](http://polishlinux.org/apps/window-managers/metisse-you-thought-you-knew-what-3d-was/)

It's a full window system, though; not just a window manager.

---

### Post by ufugu on 2009-05-14
Also of note is Xfce's built in compositing window manager, xfwm.

No expose, but nice transparency options and a natural shadow.

Yet another option is to use Openbox either on it's own or with Gnome and run it with xcompmgr.  Also no expose but some really lovely effects can be achieved. A seach through the forum will give you some tutorials on Gnome+Openbox.

Any compositor will allow you to run Docky etc.

Lots of options besides Compiz!

---

### Post by Mr. Picklesworth on 2009-05-14
Oh gee, didn't realize you were just concerned about compositing. You can use GNOME's default window manager with compositing. For now (since the feature is not considered "finished" yet), open gconf-editor (System Tools -> Configuration Editor), navigate to /apps/metacity/general and set compositing_manager to True. Disable desktop effects in Appearance preferences so Ubuntu goes back to using Metacity and you should end up seeing a very attractive composited window manager with nice thumbnails in the window switcher :)

---

### Post by stwschool on 2009-05-14
I'm after compositing yes, but I'm also keen to keep expo, it's the one thing I would struggle to do without.

---

