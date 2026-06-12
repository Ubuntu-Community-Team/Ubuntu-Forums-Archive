---
title: "Request: electricsheep"
date: 2005-06-23
forum: Ubuntu Backports
---

### Post by diwakergupta on 2005-06-23
[http://electricsheep.org](http://electricsheep.org)

Electric sheep is the collective dream of sleeping computers
 from all over the internet. Less poetically, it is an Internet server and
 xscreensaver module that displays MPEG video of an animated fractal flame.
 In the background, it contributes render cycles to the next animation.
 Periodically, it uploads completed frames to the server, where they are
 compressed for distribution to all clients.

The hoary version (2.5.2) is incompatible with the server (it requires the latest version, 2.6.2)

---

### Post by jdong on 2005-06-23
will do :)

---

### Post by Technoviking on 2005-06-23
Getting the following error 
Unpacking electricsheep (from .../electricsheep_2.6.2-1~5.04ubp1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/electricsheep_2.6.2-1~5.04ubp1_i386.deb (--unpack):
 trying to overwrite `/usr/share/xscreensaver/config/electricsheep.xml', which is also in package xscreensaver
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/electricsheep_2.6.2-1~5.04ubp1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by virgule on 2005-06-23
Can we get the 2.6.2 version for powerpc please? 8)
The site does not have 2.6.2 powerpc port..

---

### Post by Slo Mo Snail on 2005-06-24
doesn't compile on ppc :(

---

### Post by lukeweb on 2005-06-26
Would love any help getting the latest version working under (k)ubuntu. I got the same error as above and am getting somewhat desperate to see this in action :)

---

### Post by jdong on 2005-06-26
do a **dpkg --install --force-overwrite /var/cache/apt/archives/name_of_deb.deb**

---

