---
title: "Yafaray problem"
date: 2009-07-20
forum: Ubuntu Studio
---

### Post by Regele IONESCU on 2009-07-20
Hi!

When I try to access Yafaray from within blender(via Render menu) I get the following error message:

[I]sudo blender
[sudo] password for : 
Compiled with Python version 2.5.4.
Checking for installed Python... got it!
could not change language to ro nor ro.UTF-8
YafaRay 0.1.0 (315)
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/home/admiral/.blender/scripts/blender/yafaray_ui.py", line 2080, in <module>
    TabMaterial = clTabMaterial()
  File "/home/admiral/.blender/scripts/blender/yafaray_ui.py", line 250, in __init__
    self.yRender = yaf_export.yafrayRender()
  File "/usr/share/yafaray/blender/yaf_export.py", line 113, in __init__
    self.yi.loadPlugins("")
  File "/usr/share/yafaray/blender/yafrayinterface.py", line 97, in loadPlugins
    def loadPlugins(*args): return _yafrayinterface.yafrayInterface_t_loadPlugins(*args)
TypeError: in method 'yafrayInterface_t_loadPlugins', argument 2 of type 'char const *'[/I]

What can I do???


God help us all!
Regele IONESCU

---

### Post by HydroTech on 2009-10-29
Same here. Been looking for the answer to that for a while now. 
For the obvious: Do you have blender 2.48 or 2.49? And do you have the proper version of Python and Yafaray? If so, then I think I'm in the same boat as you. :)

---

### Post by a2z on 2009-10-30
I'm afraid I too have problems, but not quiet like this.
Yafaray/Blender 2.49a may not be ready for ubuntu 9.10

dpkg: unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor
is the error message provided while installing.

I have python 2.6.2.... Where Yafaray deb package 64 bit for jaunty asks for python 2.6.  Could this be the problem with the installation?
Thanks a bunch for all your help. 

a2z

---

### Post by HydroTech on 2009-11-01
I am using linux Mint which is built on ubuntu structure so I can't say if what you're saying is true. We need some help don't we? LOL

---

