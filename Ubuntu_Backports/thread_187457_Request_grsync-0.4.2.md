---
title: "Request: grsync-0.4.2"
date: 2006-06-03
forum: Ubuntu Backports
---

### Post by btlee on 2006-06-03
Would you put it into the list of backport extras?
Before I installed ubuntu, I used grsync for backing up my data.
It is very useful tool for me.
But dapper only supports 0.1.2 version, which miss some features comparing to newer version.
Especially, the current version doesn't support the function of keeping symbolic link, which makes me annoyed a little.
Thanks for your reading this.

---

### Post by makhand on 2006-07-31
One more vote. A newer one just came out too. 0.4.3. Thanks!

---

### Post by mlind on 2006-08-01
I think you should ask this on [launchpad.net]("https://launchpad.net/projects/ubp") instead

In the meantime, try if attached build works for you.

---

### Post by makhand on 2006-08-01
Thanks! seems to work well.

---

### Post by btlee on 2006-08-02
wow, it's great.
However, still I have no package for ppc ubuntu. :(
anyway, many thanks for it.

---

### Post by mlind on 2006-08-02
> **btlee said:**
> wow, it's great.
However, still I have no package for ppc ubuntu. :(
anyway, many thanks for it.

That .tar.gz includes sources, you can rebuild it on your ppc box.
If you need to extract the source package, use *dpkg-source -x <filename>.dsc*.

---

### Post by btlee on 2006-08-03
> **mlind said:**
> That .tar.gz includes sources, you can rebuild it on your ppc box.
If you need to extract the source package, use *dpkg-source -x <filename>.dsc*.

I know, but it's going to install a bunch of packages.
The problem is that my ibook is slow and has small capacity for storage.

---

