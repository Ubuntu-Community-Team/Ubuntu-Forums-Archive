---
title: "Documentation on linux architecture"
date: 2006-06-22
forum: The Cafe
---

### Post by forrestcupp on 2006-06-22
I'm fairly new to Linux.  I can get around gnome pretty well, and I'm learning a lot about the terminal, but there's something I want to learn.

I want to learn what all the different directories are for, and when I install software, where do all the different parts of it go (libraries, bins, docs, etc.)?  When I build an app from source, where do all the different parts of it go?  Why do some things go to /usr/bin, and others /usr/bin/local?  What is the difference between /bin and /usr/bin?  I know there are differences in the way distros handle these things, and I just want to understand this better.

Also, I want to know if there is a way to build something from source in such a way that my system keeps track of it, like in apt.  I heard something about apt-build.

I'm not asking people to explain all of this on this forum, just to point me toward some good documentation about these things.

---

### Post by Jucato on 2006-06-22
About the Linux Filesystem Heirarchy, here are some links you might find intersesting:
[http://help.ubuntu.com/community/LinuxFilesystemTreeOverview](http://help.ubuntu.com/community/LinuxFilesystemTreeOverview)
[http://en.wikipedia.org/wiki/FHS](http://en.wikipedia.org/wiki/FHS)
[http://www.pathname.com/fhs/](http://www.pathname.com/fhs/) (specifically [http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html))

As for the question, there's a package called checkinstall, which basically creates a .deb from the makefile that you just made (through ./configure and make) so that you could install it like any other .deb file. But I'm not sure if that works with apt. I'm not entirely familiar with this, so I'm pretty interested as well.

---

### Post by Tatey on 2006-06-22
EDIT: Please disregard this post, I completely misread your post.

---

### Post by forrestcupp on 2006-06-22
Thank you, Fenyx.  Those sites are very helpful.

Can anyone tell me what apt-build is, though?

---

