---
title: "Trac Python Problem"
date: 2008-06-21
forum: Server Platforms
---

### Post by janskey on 2008-06-21
Has anyone experience this problem:

Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/trac/web/main.py", line 406, in dispatch_request
    dispatcher.dispatch(req)
  File "/var/lib/python-support/python2.5/trac/web/main.py", line 206, in dispatch
    req.hdf = HDFWrapper(loadpaths=chrome.get_all_templates_dirs())
  File "/var/lib/python-support/python2.5/trac/web/clearsilver.py", line 135, in __init__
    raise TracError, "ClearSilver not installed (%s)" % e
TracError: ClearSilver not installed (/usr/lib/python2.5/site-packages/neo_cgi.so: undefined symbol: Py_InitModule4)

# ls -al /usr/lib/python2.5/site-packages/neo_cgi.so
-rw-r--r-- 1 root root 208960 Apr  8 15:52 /usr/lib/python2.5/site-packages/neo_cgi.so

# uname -a
Linux bo.test.com 2.6.18-xen #1 SMP Tue Feb 12 06:40:50 UTC 2008 x86_64 GNU/Linux

# dpkg -l | grep clearsilver
ii  python-clearsilver                0.10.4-1ubuntu1             python bindings for clearsilver

---

### Post by Tinjaw on 2009-05-15
update: nevermind. I was mistaken.

---

