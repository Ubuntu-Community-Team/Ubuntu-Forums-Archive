---
title: "request: update gnome-ppp &amp; firestarter programs"
date: 2005-04-20
forum: Ubuntu Backports
---

### Post by Turin Turambar on 2005-04-20
Both programs have newer versions:

Gnome-ppp - 0.3.21 (in apt-get is 0.3.17 !)
Firestarter - 1.0.3 (in apt-get 1.0.1)

Thanks.

---

### Post by Turin Turambar on 2005-04-24
Everyone - both of listed packages are available on debian site and can be easily installed.

---

### Post by jdong on 2005-04-26
Sure, I'll package backports for these.

 
 
BTW, installing binaries from Debian Sid is **NOT** a smart thing to do, and the library dependency differences will eventually bring you hell.

---

### Post by jdong on 2005-04-26
gnome-ppp is packaged and uploaded

firestarter is currently waiting to be backported.

---

### Post by Turin Turambar on 2005-04-26
[QUOTE=jdong]Sure, I'll package backports for these.
 
BTW, installing binaries from Debian Sid is **NOT** a smart thing to do, and the library dependency differences will eventually bring you hell.[/QUOTE]

Uh I didn't know that.  :-?  Everything is working okay for now....
Thanks for backporting these! :)

---

### Post by Turin Turambar on 2005-04-26
Gnome-ppp is working ok, just tested it! :)

---

### Post by TravisNewman on 2005-04-26
It won't ALWAYS screw things up, but be careful, be very careful-- especially if it wants to upgrade system libraries.

---

### Post by Turin Turambar on 2005-04-29
[QUOTE=jdong]gnome-ppp is packaged and uploaded

firestarter is currently waiting to be backported.[/QUOTE]

Is everything going ok? You can safely move gnome-ppp to "backports", it is working great! :)

---

### Post by jodef on 2005-04-30
Saw this thread on gnome-ppp anf firestarter thought it might be a good place to ask: In firestarter to enable protection on my interface all I need to do is use ppp0 as network interface and select protect on dial out? 

Is this assumption correct?

---

### Post by Turin Turambar on 2005-04-30
[QUOTE=jodef]Saw this thread on gnome-ppp anf firestarter thought it might be a good place to ask: In firestarter to enable protection on my interface all I need to do is use ppp0 as network interface and select protect on dial out? 

Is this assumption correct?[/QUOTE]

Basically, yes. You can also enable ICMP filtering, to protect your PC from ping & similar attacks.
However, 1.0.1 is a little buggy, so, for example, dictionary won't work with firewall enabled, even with policies allowed.
All is fixed in 1.0.3, that's why I'm eagerly waiting for that ver. to be backported. :)

For everything else, you can check Online user's manual.

---

### Post by jdong on 2005-04-30
Alright, I'll pull a Firestarter 1.0.3 from Debian Sid.

---

### Post by Turin Turambar on 2005-05-06
Just to let you know that firestarter 1.03 is working great. :)

---

### Post by jdong on 2005-05-06
Firestarter 1.0.3 is already backported, in the Staging tree going through testing.

It's pretty stable, and I plan on moving it to the stable tree on Sunday.

---

### Post by donar73 on 2005-05-06
> Just to let you know that firestarter 1.03 is working great. 

Totally agree! No problems here as well!  :)

---

