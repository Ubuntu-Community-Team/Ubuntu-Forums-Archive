---
title: "Ardour 2.8.2 &amp; JACK 0.116.1 for Hardy"
date: 2009-11-11
forum: Ubuntu Studio
---

### Post by Drunky on 2009-11-11
I built JACK 0.116.1 (with FFADO 2.0~rc1) and Ardour 2.8.2 for Hardy.  You can find the .debs in my ppa.

My ppa:
```
deb http://ppa.launchpad.net/slavender/ppa/ubuntu hardy main 
deb-src http://ppa.launchpad.net/slavender/ppa/ubuntu hardy main 
```

Signing key:
```
1024R/0020F80E
```

And if you don't know how to install software from ppa's:

[How do I use software from a PPA?]("https://launchpad.net/+help/soyuz/ppa-sources-list.html")


If you install it and everything works well be sure to add a comment to the appropriate bugs saying so:

[LP: 299287 - Please backport Ardour 2.8.2 to Hardy]("https://bugs.launchpad.net/hardy-backports/+bug/299287")
[LP: 312613 - Please backport JACK 0.116 to Hardy]("https://bugs.launchpad.net/hardy-backports/+bug/312613")

Adding comments to the appropriate bug let's the backporters know the .debs work and can push the fix into hardy-backports for everyone to update.


If you have trouble please post in this thread or contact me on Launchpad:
[https://launchpad.net/~slavender/+archive/ppa](https://launchpad.net/~slavender/+archive/ppa)

Thank you.

---

