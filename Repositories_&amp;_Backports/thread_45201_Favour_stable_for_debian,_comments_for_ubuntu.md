---
title: "Favour stable for debian, comments for ubuntu?"
date: 2005-06-29
forum: Repositories &amp; Backports
---

### Post by jago25_98 on 2005-06-29
From  :
[http://hamsterrepublic.com/james/linux/index.php](http://hamsterrepublic.com/james/linux/index.php)

I found this howto regarding how to get debian to favour stable packages over the unstable, so you can use unstable packages yet not have to upgrade everything to unstable.

Comments for how you might adapt this to ubuntu?

> 
June 16 2005
Mixed stable/unstable debian installation

I can't believe I waited so long to learn how to do this. Often I want to run the stable version of Debian, but I want access to one or two packages from the unstable version. How do i do it? Previously my only choices were to (A) upgrade the whole system (B) manually install the particular package, and manually install its dependencies (C) Hope that a backport existed for it.

But none of those three options is what I really want to do. I want to have stable installed, but still have the option of asking for an unstable package, and having it just work. There are two things I had to do. First; I had to put both stable and testing in my /etc/apt/sources.list file.

deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) stable main
deb-src [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) stable main
deb [http://security.debian.org/](http://security.debian.org/) stable/updates main

deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) unstable main
deb-src [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) unstable main

This alone would cause my entire system to be upgraded to unstable, since the higher version numbers in unstable would always oveeride those from stable. What I needed to do next was to set stable to a higher priority. I did this by creating a /etc/apt/preferences file

Package: *
Pin: release a=stable
Pin-Priority: 500

Package: *
Pin: release a=unstable
Pin-Priority: 200

Because I have given a higher priority to stable packages, so given the choice, it will use he stable ones, but when I ask for a package that only exists in unstable, it will do the right thing

If my desire was to install an unstable package that also existed in stable, I would have to add an additional entry to my /etc/apt/preferences file, giving it a higher priority by name, but that iss not what I want to do. if you want to do that, I suggest reading man apt_preferences

Also, it is worth noting that running a mixed stable/unstable system is not always reliable. You may install packages that have mutually conflicting dependencies, so whenver a backport is available for the package you care about, you should always use that first. 


---

### Post by Akoluth of Nandus on 2005-06-29
This works exactly the same in Ubuntu. You only have to change a few strings ("stable"="hoary", other servers, etc.).

The standard priority of repositories is 500. Anything with a priority above that will be preferred and everything with a priority <500 will be held back. (This only covers part of the pinnig functionality, more can be found in the [apt howto](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html).)

My /etc/apt/preferences for example looks like this:
```

Package: *
Pin: origin ubuntu-backports.mirrormax.net
Pin-Priority: 400

Package: *
Pin: origin wine.sourceforge.net
Pin-Priority: 600

```

Packages from the backports repository are only installed when I explicitly say apt/synaptic to do so and the wine packages from sourceforge are preferred over the Ubuntu ones.

---

