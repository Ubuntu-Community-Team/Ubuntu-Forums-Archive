---
title: "Quick and painless way to replace Apache module?"
date: 2009-01-23
forum: Server Platforms
---

### Post by whir on 2009-01-23
Hi all,
So I'm working with Ubuntu 8.10 and Apache 2.2 on a test box and want to replace mod_suexec with a slightly modified version from within my company.  The problem is that I'm not that experienced with Apache administration and am not sure how...  If anyone could help me out, I would appreciate it.

I'm pretty sure that if worse came to worse I could just rebuild all of Apache, but I'd prefer a simple drop-in fix as I like how the default installation of Apache on Ubuntu sets itself up.

I need to:
-Compile mod_suexec from source
-Drop it in to replace the current version.

My installed packages:
apache2.2-common
apache2
apache2-suexec
apache2-mpm-worker
apache2-utils

Thanks!

---

### Post by cdenley on 2009-01-23
You should get the source from the repo
```

apt-get source apache2-suexec

```
change the source code as needed, install build dependencies, build the package(s), then install the package
```

sudo apt-get build-dep apache2-suexec
cd apache2-*
debuild -i -us -uc -b
sudo dpkg -i ../apache2-suexec_*.deb

```

---

### Post by whir on 2009-01-27
Thanks for you reply.

Unfortunately, this is the way I was already trying to do it that would completely reinstall Apache.  I would like a way that would let me build **just** mod_suexec.so

Thanks.

---

### Post by cdenley on 2009-01-27
> **whir said:**
> Thanks for you reply.

Unfortunately, this is the way I was already trying to do it that would completely reinstall Apache.  I would like a way that would let me build **just** mod_suexec.so

Thanks.

It would build all of apache, but it would only install whatever package you choose to install. That debuild command shouldn't install anything.

---

### Post by whir on 2009-01-27
Hmm... Thanks for your response.  I actually discovered the apxs way though, and that worked for me.

---

