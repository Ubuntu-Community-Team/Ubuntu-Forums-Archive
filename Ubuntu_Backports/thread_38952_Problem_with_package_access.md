---
title: "Problem with package access"
date: 2005-06-02
forum: Ubuntu Backports
---

### Post by elektronaut on 2005-06-02
Hi!

I'd like to install the Java SDK 1.5, but I always get error messages from synaptic stating that it can't access the list.

Here are the lines I've added alternatively to sources.list:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports-staging main universe multiverse restricted

deb [http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/) hoary-backports-staging main universe multiverse restricted

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted

deb [http://acm.cs.umn.edu/ubp/](http://acm.cs.umn.edu/ubp/) hoary-backports-staging main universe multiverse restricted

What's the problem?

---

### Post by jdong on 2005-06-02
Please perform a "sudo apt-get update" at a terminal, and paste any error messages here.

---

### Post by elektronaut on 2005-06-02
I now added all following lines, ignored the error message and did a reload in synaptic. Now it works. Thanks for your reply!

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports-staging main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras-staging main universe multiverse restricted

---

