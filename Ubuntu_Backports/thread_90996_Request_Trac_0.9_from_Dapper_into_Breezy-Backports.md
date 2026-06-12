---
title: "Request: Trac 0.9 from Dapper into Breezy-Backports"
date: 2005-11-16
forum: Ubuntu Backports
---

### Post by DanyX on 2005-11-16
Hi all, 

I don't really know if this is the correct spot to post this, but Trac 0.9-1ubuntu1 is in drapper a few days now and I'd like to use it in breezy. Could someone maybe backport this package? If I don't miss anything crutial, it should not be too hard as the dependencies haven't really changed (some alternatives have been added as fas as i can see). This would be real great as the new trac version has a few pretty cool features I'd like to use. 

If it is not necessary to backport trac because there is some magical way to do this that remains nicely upgradeble via apt-get upgrade please tell me how to do so!

Thanks in advance,
Daniel

---

### Post by shadowfox on 2005-11-22
I second this request since Dapper is a couple of months away.
A lot of us needed Trac 0.9.

The strangest thing is, I can get 0.9 from debian unstable, but they somehow package it with Python 2.3 (what gives?) why not 2.4 ??

I emailed the maintainer about this, but hasn't got any respond from him yet.
I don't know what's the one in Dapper packaged with, hopefully it's Python 2.4.

Thanks!
Will


[QUOTE=DanyX]Hi all, 

I don't really know if this is the correct spot to post this, but Trac 0.9-1ubuntu1 is in drapper a few days now and I'd like to use it in breezy. Could someone maybe backport this package? If I don't miss anything crutial, it should not be too hard as the dependencies haven't really changed (some alternatives have been added as fas as i can see). This would be real great as the new trac version has a few pretty cool features I'd like to use. 

If it is not necessary to backport trac because there is some magical way to do this that remains nicely upgradeble via apt-get upgrade please tell me how to do so!

Thanks in advance,
Daniel[/QUOTE]

---

### Post by paulbaranowski on 2005-12-01
I also would like to see trac 0.9 for breezy!  Has anyone tried using the package from dapper to see if it just works?

---

### Post by strikeforce on 2005-12-01
marc@ubuntu:~/ubp-compile-temp$ apt-cache show trac | grep Version
Version: 0.9-1ubuntu1~breezy1
Version: 0.8.4-1ubuntu1
marc@ubuntu:~/ubp-compile-temp$

From my understanding its there.

---

