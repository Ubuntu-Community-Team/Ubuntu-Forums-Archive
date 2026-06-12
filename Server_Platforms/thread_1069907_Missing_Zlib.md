---
title: "Missing Zlib"
date: 2009-02-14
forum: Server Platforms
---

### Post by EvanKroske on 2009-02-14
I have been attempting to install Django for the last couple of days, and every time I think I'm making progress, it turns out that I'm missing another piece of software. I needed flup, but when I attempted to install it, it failed to install setuptools. When I tried to install setuptools, I received this error:
```

Traceback (most recent call last):
  File "<string>", line 1, in <module>
zipimport.ZipImportError: can't decompress data; zlib not available

```
I used [this page]("http://python.org/download/releases/2.6.1/") to download setuptools and receive instructions. Of course, I then installed the newest version of zlib, but that didn't work at all. When I looked for some kind of Python-zlib bridge, I discovered that it was a default part of Python. Can somebody tell me why I can't install setuptools (to install flup to install Django)? Thanks.

---

### Post by cosine352 on 2009-02-14
google gives me this result

[http://www.jeffbaier.com/2007/07/26/installing-django-on-an-ubuntu-linux-server/](http://www.jeffbaier.com/2007/07/26/installing-django-on-an-ubuntu-linux-server/)

may be you can try that

---

### Post by EvanKroske on 2009-02-14
No luck. That tutorial covers how to install with mod_python; I'm using mod_fastcgi under Apache 2 point something web server. My question doesn't directly relate to Django installation, but to the python zlib module and Flup installation. Thanks for the link anyway; it's got some good info I'll need later.

---

### Post by dbarthel on 2009-12-22
I got the same error for 'setuptools' for Python 2.6 on Ubuntu 8.10 when running:

sh setuptools-0.6c11-py2.6.egg

I solved it by running:

apt-get install zlibc

Before recompiling Python:

./configure
make
make install

Now running sh setuptools-0.6c11-py2.6.egg works without error.

---

### Post by sssharanster on 2010-07-28
Hi 

I had encountered the same problem in 10.04 lucid . Had to apt-get zlibc and recompile python as dbarthel suggested. I could install setuptools without any error now.

Thanks for the suggestions.

---

