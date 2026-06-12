---
title: "Gaphor 0.8"
date: 2006-02-02
forum: Requests
---

### Post by mariuss on 2006-02-02
Version 0.8 of the UML modeling tool was just released the other day:
[http://sourceforge.net/projects/gaphor](http://sourceforge.net/projects/gaphor)

Currently version 0.7 is available in Breezy.

Thanks,
Marius

---

### Post by derk.d on 2006-06-12
can somebody create a .deb for it??
because 0.7 doesn't work for me in dapper...

---

### Post by Adramelech on 2006-07-21
hummm
i made this to get it working:

deleted the line:

(diacanvas.CanvasGroup in bases) or \

on build/lib/gaphor/diagram/__init__.py

is not elegenat but oh well, it worked (so far)

---

### Post by Ba66e77 on 2007-01-06
I can't seem to install this in Edgy.  When I try to mark it for installation, I get a message that it depends on python-daicanvas2.  When I try to mark python-diacanvas2 for installation, I get the following message
> python-diacanvas2:
 Depends: python2.4-diacanvas2  but it is not installable

As far as Synaptic seems to know, there is no python2.4-diacanvas2.  Any one know the fix for this?

---

### Post by Golyadkin on 2007-08-17
I am trying to install Gaphor as well, version gaphor_0.8.1-5.1ubuntu1_all.deb, but it doesn't start. 

This is the error I get:
```

Traceback (most recent call last):
  File "/usr/bin/gaphor", line 13, in <module>
    gaphor.main(model)
  File "/usr/lib/python2.5/site-packages/gaphor-0.11.2-py2.4.egg/gaphor/__init__.py", line 36, in main
    from gaphor.application import Application
  File "/usr/lib/python2.5/site-packages/gaphor-0.11.2-py2.4.egg/gaphor/application.py", line 13, in <module>
    from zope import component
  File "/usr/lib/python2.5/site-packages/zope.component-3.4dev_r72749-py2.5.egg/zope/component/__init__.py", line 19, in <module>
    import zope.deferredimport
  File "/usr/lib/python2.5/site-packages/zope.deferredimport-3.4.0-py2.5.egg/zope/deferredimport/__init__.py", line 1, in <module>
    from zope.deferredimport.deferredmodule import initialize
  File "/usr/lib/python2.5/site-packages/zope.deferredimport-3.4.0-py2.5.egg/zope/deferredimport/deferredmodule.py", line 20, in <module>
    import zope.proxy
ImportError: No module named proxy

```

---

