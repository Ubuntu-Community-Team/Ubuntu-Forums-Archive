---
title: "Source Based Package Management"
date: 2009-02-19
forum: The Cafe
---

### Post by fistfullofroses on 2009-02-19
I was wondering if anyone knew of a package manager that uses unmodified source tars. I am not thinking of something like pacom (close but not really it). Something more like pkgtool, dpkg, or rpm... but instead of using DEBs or RPMs it would use foo.tar.gz or foo.tar.bz2 If it doesn't exist, I will write it from scratch, but it would be awesome if it already existed. I guess from there I would go ahead and make it work with apt...

---

### Post by Brunellus on 2009-02-19
look at apt-build.

---

### Post by fistfullofroses on 2009-02-19
That is close to what I want, but is there something similar that does not build a deb?

---

### Post by Namtabmai on 2009-02-19
You mean something like Gentoo's ebuild system?

---

### Post by juanmoreno92 on 2009-02-19
Or better yet, LFS? (Linux From Scratch)

---

### Post by bsharp on 2009-02-19
I think I understand what he is saying, and I've wondered about the same thing myself. Say the package manager is-hypothetical here- source-get. So to install, you do:
```
source-get install whatever
```
And it downloads the source files from a repository, unpacks and builds them the same way as a manual user would if he/she were compiling themselves, but automated of course.

I'm no expert at these things, but I assume any advantages gained by having it compiled specifically for your system would be outweighed by the time it would take to install.

---

### Post by jpkotta on 2009-02-19
> **bsharp said:**
> I'm no expert at these things, but I assume any advantages gained by having it compiled specifically for your system would be outweighed by the time it would take to install.

You should try Gentoo.  You might change your mind.

Edit:  I completely took that the wrong way.  You're absolutely correct.  Also, in my experience, Gentoo packages were less reliable than Debian ones, though you could always have the latest and greatest.

---

### Post by spupy on 2009-02-20
It's called portage - the package manager of Gentoo.
I think it could be possible, although pretty hard, to install portage on Ubuntu. And it wouldn't be compatible with apt.

---

### Post by argail1980 on 2009-02-20
This is a nice idea as long as u don't have to update your system. I had a gentoo once and it took a solid week to update the system. afterwards, I had to check a lot of config files for changes. When you have a system that is isolated from the net and needs to be fast ans stable (i.e. one that you don't need to update), you might want gentoo. Otherwise, it's a pain (That was the reason I finally got to using ubuntu).

---

