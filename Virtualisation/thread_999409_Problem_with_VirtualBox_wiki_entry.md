---
title: "Problem with VirtualBox wiki entry"
date: 2008-12-01
forum: Virtualisation
---

### Post by Ash Velveteen on 2008-12-01
On the Ubuntu wiki entry to install virtualbox, it says to type 

> sudo apt-get install virtualbox-ose virtualbox-ose-modules-`uname -r'

However, when I do this, it says
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package virtualbox-ose-modules-uname -r

I'm not entirely sure how to deal with the error message. Also, I'm a linux newb, so I may not know things that should be obvious :?

---

### Post by bodhi.zazen on 2008-12-02
I assume it is a typo

Those are back tics ` on my keyboard by the number 1

[indent]`uname -a`[/indent]

and not single quotes ' 

[indent]NOT 'uname -a'[/indent]

---

### Post by Ash Velveteen on 2008-12-03
I think that helped a bit, the error message has now changed to:
> E: Couldn't find package virtualbox-ose-modules-2.6.24-22-generic

Can someone tell me what to do now?

---

### Post by bodhi.zazen on 2008-12-03
To be honest, many people, because of these issues, use the PUEL edition, the one you download from Sun, rather then the OSE.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

