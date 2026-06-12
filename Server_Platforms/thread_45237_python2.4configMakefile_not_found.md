---
title: "python2.4/config/Makefile not found?"
date: 2005-06-29
forum: Server Platforms
---

### Post by python_guy on 2005-06-29
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)

Today I get this error when I am trying to install zope with source on my ubuntu box. So I fetch it from repository instead. However, I get the same error when I install moinmoin, anyone know how to solve it?

---

### Post by Juergen on 2005-06-29
Install the package 'python2.4-dev'

---

### Post by python_guy on 2005-06-30
thanks a lot, the moinmoin wiki is running without problems

---

### Post by codemonkeylp on 2006-03-16
I had the same problem with updating trac on my server...  Thank you Juergen

---

### Post by krokodil on 2006-03-24
Thanks, was struggling to install [Universal Feed Parser]("http://sourceforge.net/projects/feedparser/").

Also needed a sudo.

```
# sudo python setup.py install
```

---

