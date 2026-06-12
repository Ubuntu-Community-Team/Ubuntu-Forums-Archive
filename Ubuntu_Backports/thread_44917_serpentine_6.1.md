---
title: "serpentine 6.1"
date: 2005-06-28
forum: Ubuntu Backports
---

### Post by dlpfmVfH on 2005-06-28
serpentine has a new release, just tested it, compiled it from scratch,
and it is an improvement, serpentine .5 didn't get my writer....6 works..

So I was hoping it gets into backports...cause it fixes a lot of things...for me...
it even has a muine plugin...

woopie

don't know if it is in breezy but I think it will be soon...

---

### Post by Slo Mo Snail on 2005-06-28
It's currently not in breezy... I'll package it then

---

### Post by cogumbreiro on 2005-06-28
[QUOTE=Slo Mo Snail]It's currently not in breezy... I'll package it then[/QUOTE]
 Hi, I am the developer of Serpentine and got this bug report a few days ago:
[https://developer.berlios.de/bugs/?func=detailbug&bug_id=4356&group_id=3081](https://developer.berlios.de/bugs/?func=detailbug&bug_id=4356&group_id=3081)

So it seems that nautilusburn is broken in Breezy, since I am also the developer of nautilusburn bindings I'll have to correct that problem too :)

I've just installed breezy and installed the sources of gnome-python2-extras, the packages has a bug since it does not depend on python-dev package as it should, i'm going to submit this to the bugzilla.

As soon as I have more info on this I'll post it here.

---

### Post by dlpfmVfH on 2005-06-28
as my post says, I did the compile in Hoary without a problem...
haven't burnt a cd with it yet..but the other serpentine 0.5 deb didn't even start up

---

### Post by cogumbreiro on 2005-07-02
serpentine 0.6.1 is already in Breezy, the python-gnome2-extras package was fixed, so everything is ok.

serpentine 0.5 didn't start for you because of a bug which was fixed in the last release.

---

### Post by Slo Mo Snail on 2005-07-03
Ok, I'll package it in a few minutes ;)

EDIT: done... seems fine for me ;)

---

### Post by cogumbreiro on 2005-07-03
Cool, thx!

---

