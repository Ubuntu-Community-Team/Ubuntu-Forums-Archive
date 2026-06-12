---
title: "ZipImportError: Bad local file header"
date: 2012-06-18
forum: Server Platforms
---

### Post by theburningor on 2012-06-18
I am running 12.04 64 bit with Python 2.7 running inside of a virtualenv created by virtualenvwrapper.  Everything seems to be working fine except for a few libraries which keep giving me the following error when I try to install them with 'pip install'

```
zipimport.ZipImportError: bad local file header in /home/cupid/.virtualenvs/cc/local/lib/python2.7/site-packages/setuptools-0.6c11-py2.7.egg
```

I don't believe this is an error with the packages themselves because they install fine in my laptop.

My research online suggests this error occurs when the file in question has been previously referenced by a forked process and that a server reset should fix it, but this occurs even when the package in question ('loremipsum') is the only installed package after a fresh reboot.

---

