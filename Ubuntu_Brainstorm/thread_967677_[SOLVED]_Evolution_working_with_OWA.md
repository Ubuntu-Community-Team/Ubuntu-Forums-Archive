---
title: "[SOLVED] Evolution working with OWA"
date: 2008-11-02
forum: Ubuntu Brainstorm
---

### Post by Coruba67 on 2008-11-02
Hi guys,

Not really sure if this is the place to come to ask this, bascially I was wondering how Evolution (or where I can go to find more information about it) connects with Exchange via OWA.  I am writing a PHP app at the moment and would love to know where I can go to find the information I need to get the calendar appointments from exchange (or OWA)...

Any help would be awesome!  Thanks

---

### Post by smartboyathome on 2008-11-02
You can look at the code. Run this to get it:
```
mkdir evolution && cd evolution
apt-get source evolution
```
It will basically fetch the source of evolution for you, which you can look at to see how they do it.

---

### Post by Coruba67 on 2008-11-02
Thanks mate, I'll check it out!

---

