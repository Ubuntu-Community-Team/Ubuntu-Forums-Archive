---
title: "awstats install location in ubuntu is different than generic linux?"
date: 2016-09-15
forum: Server Platforms
---

### Post by farokh.bts on 2016-09-15
Hi all.

I'm running 16.04.1 and I installed awstats using apt-get.

However, there's a new version (7.5) of awstats out and I'd like to install it, but it appears that awstats for generic linux is installed in a different directory than the ubuntu version.

Is there a reason for the difference? Can I simply install awstats in the default linux directory and simply maintain it myself instead of using apt?

Thanks!

---

### Post by SeijiSensei on 2016-09-15
If you are downloading the source code and compiling it yourself, then "sudo make install" will usually place everything under /usr/local.  The standard is to place binaries from packages installed with the package manager in /usr, but locally-complied software usually resides under /usr/local/bin for programs for ordinary users, and /usr/local/sbin for programs used by the system administrator.  If it's installed to /usr/local/bin, you should be able simply to type "awstats" to run the program since /usr/local/bin is in the default PATH.

Some programs create a subdirectory of their own in /usr/local, so make sure there isn't a /usr/local/awstats or /usr/local/awstats/bin.  If the latter directory has the program itself, you can create a symbolic link to it from /usr/local/bin like this:
```
cd /usr/local/bin
ln -s ../awstats/bin/awstats

```

---

