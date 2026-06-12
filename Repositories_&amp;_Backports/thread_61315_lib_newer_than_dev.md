---
title: "lib newer than dev"
date: 2005-08-31
forum: Repositories &amp; Backports
---

### Post by pisi on 2005-08-31
Hello,

I tried to compile sylpheed-2.0.1, because my Sylpheed-gtk often dies while getting mail.
I discovered, that many libs in my system are newer than the corresponding -dev package.
So I am unable to install these dev packages, because of unsatisfied dependencies. e.g.
```

libatk1.0-dev: Depends: libatk1.0-0 (= 1.9.1-0ubuntu1) but 1.10.1-2 is to be installed
libglib2.0-0 version 2.7, but devel is 2.6

```

my sources.list:
```
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted 

deb http://archive.ubuntu.com/ubuntu/ hoary universe 
deb-src http://archive.ubuntu.com/ubuntu/ hoary universe 

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted 

deb http://archive.ubuntu.com/ubuntu/ hoary multiverse 

``` 

Where do these differences come from?
Does anybody has an idea, how to resolve it?
(could updating to breezy help?)

---

### Post by pisi on 2005-08-31
ist it possible, that the libs are updated via security update, but the devel-packages still depend on th unpatched version? if so, how can i keep a working development system while using security updates?

---

### Post by pisi on 2005-09-01
unpatient, as ai am, id downgraded these complaining libs to a hoary-version.
still wondering, where they came from.

---

