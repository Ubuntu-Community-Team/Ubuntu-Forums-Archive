---
title: "installing apache from source &quot;on top of&quot; existing apache"
date: 2008-10-17
forum: Server Platforms
---

### Post by dev.null on 2008-10-17
apache2 binary is already installed and working on a ubuntu 8.4 box

I've apt-get'ed the latest apache source,

./config
make
make install

all works great.

Problem is, it doesn't overwrite the currently installed apache and modules.

I know I can fix that easily with --prefix, but I'm wondering if I wont run into other problems like apache2ctl that is installed in the binary.

So, what's the "official" way to upgrade binary apache with the latest source? I've searched around (here and google) but keep getting pages that aren't related exactly.

Thanks!

---

### Post by lykwydchykyn on 2008-10-17
Whenever possible I avoid using "make install" and try to make a deb.  It's a little more involved than "make install" but in the long run managing the software is easier.

Here's a good guide for it:

[http://www.linux.com/articles/60383](http://www.linux.com/articles/60383)

That said, it's hard to get all the versioning and so forth right to make it actually upgrade existing packages, so no matter how you do it I'd recommend purging (or at least removing) the repository version first.

---

### Post by cdenley on 2008-10-17
```

sudo apt-get install devscripts
cd /path/to/src
debuild -i -us -uc -b

```
I can never remember that command, so I always have to refer to "man debuild". I think the problem you have is the makefile doesn't use ubuntu's path by default. The correct path, along with version stuff, I think are stored in the debian rules, which is used by debuild. That should give you a package just like one from the repos. I use that command whenever I want to change the source code, which doesn't happen often.

Wouldn't the source from "apt-get source" be the same version as "apt-get install"? Why are you trying to install from source?

---

### Post by dev.null on 2008-10-17
> **cdenley said:**
> Wouldn't the source from "apt-get source" be the same version as "apt-get install"? Why are you trying to install from source?

I have to add a couple other non-standard apache modules and hand-edit some that exist to get the functionality I want (blackbox mysql logging).

Thanks for all the great advice guys!

---

