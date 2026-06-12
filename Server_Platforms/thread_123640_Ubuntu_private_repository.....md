---
title: "Ubuntu private repository...."
date: 2006-01-30
forum: Server Platforms
---

### Post by eviltwin on 2006-01-30
Hi, for my own pruposes on my home network I am hoping to create a small repository to help me manage some packages on various servers. To that end I was wondering if anyone can have some advice from someone who runs one of the ubuntu repositories, things like what software they use to manage them, generate the package lists... etc. I have found a few things on the net, but they don't go into very much detail about the finer points. I was wondering if someone could perhaps talk me through it on IM or if someone could point me in the direction of how the ubuntu repositories were set up.

Many thanks,
Graham

---

### Post by olddog55 on 2006-01-30
Ubuntu is Debian based, so you can check out:
[http://www.isotton.com/debian/docs/repository-howto/repository-howto.html](http://www.isotton.com/debian/docs/repository-howto/repository-howto.html)

Substituting ubuntu for debian wherever needed... :-)

---

### Post by ORiON2012 on 2006-01-31
[http://mirror.ubuntulinux.nl/](http://mirror.ubuntulinux.nl/)
Seveas has created the Falcon Repository System that is geared at precisely that; small scale custom repositories.

---

### Post by Soleil-Raid on 2006-01-31
apt-cacher (it's in apt-get).

If what you want is for all your computers to have cached local access to packages, this is a much simpler automagic solution.

---

### Post by olddog55 on 2006-02-01
Hey:-    Great pointer.

And it seems that apt-cacher can be used on both Ubuntu *and* Debian sources at the same time.   I've got my laptops on Ubuntu, but my servers are on a minimal core install of Debian.  I'm using the same apt-cacher for both and nothing has crashed yet.  :-)

---

