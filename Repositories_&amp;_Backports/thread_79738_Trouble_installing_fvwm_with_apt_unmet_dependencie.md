---
title: "Trouble installing fvwm with apt: unmet dependencies"
date: 2005-10-20
forum: Repositories &amp; Backports
---

### Post by dkaplowitz on 2005-10-20
Hello,

New Ubuntu user cheking out Ubuntu as an alternative to Gentoo which I've been using for a couple years now. I see others on this board having similar problems, but nothing I've found with the search has helped. 

I want to change my WM to fvwm and I'd prefer, if possible, to install it (and its dependencies) with some type of package management system instead of installing with source. 

When I do a sudo apt-get install fvwm, I get:
```

The following packages have unmet dependencies:
  fvwm: Depends: gdk-imlib1 but it is not installable
        Depends: libglib1.2 (>= 1.2.0) but it is not installable
        Depends: libgtk1.2 (>= 1.2.10-4) but it is not installable
        Depends: libstroke0 (>= 0.5.1) but it is not going to be installed
E: Broken packages

```

I've tried individually installing each of these dependencies, but I get similar errors. 

Here's my /etc/apt/sources.list:
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release Candidate i386 (20051005)]/ breezy main restricted 

 deb http://us.archive.ubuntu.com/ubuntu breezy universe
 deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

```

I'm sure this has more to do with the fact that I'm a newbie with apt-get, but I can't figure out how to get past this hurdle.

Thanks for any help.

Dave

---

