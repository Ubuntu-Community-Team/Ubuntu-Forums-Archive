---
title: "help installing Mediatomb on Hardy"
date: 2008-10-04
forum: Server Platforms
---

### Post by mr.prozac on 2008-10-04
hi,

I'm trying to install MediaTomb to hook up my server on my ps3 and Archos.

When i try to install i get the following error(s):

```
Installing package(s) with command apt-get -y --force-yes -f install mediatomb-daemon ..

Reading package lists...
Building dependency tree...
Reading state information...
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mediatomb-common: Depends: libavcodec0d (>= 0.cvs20060823) but it is not installable
                    Depends: libavformat0d (>= 0.cvs20060823) but it is not installable
                    Depends: libexif12 but it is not going to be installed
                    Depends: libmozjs0d (>= 1.8.0.13~pre070720) but it is not going to be installed
                    Depends: libtag1c2a (>= 1.4) but it is not going to be installed
  mediatomb-daemon: Depends: mediatomb-common (>= 0.11.0-1ubuntu1) but 0.11.0-1etch1 is to be installed

.. install failed!
```


I'm using Webmin to manage my server.

Could anyone push me in the right direction. I'm kinda new to the Linux side of servers..



[EDIT]

I managed to solve the problem by performing a dist-upgrade for all my packages in Webmin. After that retry to install MediaTomb with succes. :)

---

