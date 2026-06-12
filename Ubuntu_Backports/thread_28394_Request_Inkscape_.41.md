---
title: "Request: Inkscape .41"
date: 2005-04-20
forum: Ubuntu Backports
---

### Post by benplaut on 2005-04-20
I looked into the release notes for this mere one one-hundreth version upgrade, and it includes better layer support.

Layers are the weakpoint of Inkscape, so pleeeeaaase make an update?  :razz: 

Thankee very much  :grin:

---

### Post by Burgundavia on 2005-04-20
This is already in Breezy, so it should be fairly easy.

Corey

---

### Post by benplaut on 2005-04-20
[QUOTE=Burgundavia]This is already in Breezy, so it should be fairly easy.

Corey[/QUOTE]

k, thanks

---

### Post by Virtual DarKness on 2005-04-25
I've tried to backport inkscape but it miss libgc version 6.4+..

```
checking libgc version 6.4+... no
configure: error: libgc (the Boehm Conservative Collector) 6.4+, is needed to compile inkscape -- http://www.hpl.hp.com/personal/Hans_Boehm/gc
```

I think I could backport that too but don know if it is "safe" or if it will create some problem with the other software installed..

please (expecially jdong ;) ) let me know.

bye,
Giovanni.

---

### Post by jdong on 2005-04-25
Taking a look at reverse dependencies, it's not safe to make this library update, unless many Universe packages are rebuilt. This would also make Hoary-backports binary **incompatible** with Hoary, which I want to avoid.


Unfortunately, at this point, I will not be able to create the backport because of libgc. :(

---

### Post by Virtual DarKness on 2005-04-26
mm.. the "dirty way" seems to work: the package created with alien from the inkscape-0.41-1.static.i386.rpm downloadable from the inkscape web site works; it gives an error that I also had some time ago (but maybe not in kubuntu, can't remember) on startup about missing extensions and it seems to be slower but for who that need it is better than nothing :-P

let me know if you try it.

bye,
Giovanni.

---

### Post by benplaut on 2005-04-26
i added debian sid to my sources list, installed .41, and removed them.

it works perfectly  :razz:

---

### Post by Virtual DarKness on 2005-04-26
doh! didn't thought at the bad boy!

I'll try to backport it from sid then ;)

bye,
Giovanni.

edit:
same problem as above.. but this time it requires also the "-dev" package of libgc.. isn't it possible to install just the update "-dev" package and then build a static version of inkscape? (and if yes.. how? :D)

---

### Post by jdong on 2005-04-26
No, it's **NOT** ok to introduce statically linked packages. It's got to violate Debian packaging policies, and I don't want to do that.

---

### Post by f76 on 2005-09-14
Does this mean that there is as of yet no safe way to use .42 under ubuntu hoary?
Is anyone running it under hoary? do you have any problems ?

thanks

---

### Post by tseliot on 2005-09-14
Why don't you use autopackage?

---

