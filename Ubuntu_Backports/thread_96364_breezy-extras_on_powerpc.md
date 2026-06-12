---
title: "breezy-extras on powerpc"
date: 2005-11-28
forum: Ubuntu Backports
---

### Post by eladamri on 2005-11-28
Hello, I have always been scared to post on these forums so if this question proves to be silly please don't thrash me to badly. I looked everywhere for an answer.

I am trying to access the breezy-extras repos on an old mac laptop. I added the lines in sources.list as per jdong's sticky.

here is my sources.list
```
## main
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

## security
deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
#deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

## updates
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
#deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

## backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## extras
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse
```

Every repository is working fine (including the backports) except for the extras. This is the error message that I am getting.
```
http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/binary-powerpc/Packages.gz: 404 Not Found
http://ubuntu-backports.mirrormax.net/dists/breezy-extras/restricted/binary-powerpc/Packages.gz: 404 Not Found
http://ubuntu-backports.mirrormax.net/dists/breezy-extras/universe/binary-powerpc/Packages.gz: 404 Not Found
http://ubuntu-backports.mirrormax.net/dists/breezy-extras/multiverse/binary-powerpc/Packages.gz: 404 Not Found
```

The error message seems to indicate that it is trying to connect to
[http://ubuntu-backports.mirrormax.net/dists/breezy-extras/multiverse/](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/multiverse/)**binary-powerpc/**
but I think it should be looking for
[http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/](http://ubuntu-backports.mirrormax.net/dists/breezy-extras/main/)**binary-ppc/**
This is really just a hunch.

Can anyone let me know what the problem is?

Thank you in advance.

---

### Post by jdong on 2005-11-29
Well either way Extras hasn't really been underway for Breezy... I'm trying to switch over to supporting current efforts rather than being the Ubuntu rebel Backports used to be in the Warty days :)

Currently, direct new package requests to the MOTU's, and direct new "restricted/legal" stuff to Ubuntu PLF.

---

### Post by eladamri on 2005-11-29
Ahh, I see.

Thank you, jdong.

---

### Post by Rxke on 2005-11-29
Yes, Coincidentally I checked it out, too, and the 'folders' are empty. They do exist though, but do not contain a 'table of contents' file, which probably throws the error... One day, tuff will trickle in, and the 'error' will go away. It's more a warning-style problem  than a real error, in that regard.

(Sorry for using non-official terms, I'm Dutch-speaking, and currently too tired to remember the right terms...)

---

