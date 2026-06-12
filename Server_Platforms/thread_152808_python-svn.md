---
title: "python-svn"
date: 2006-03-30
forum: Server Platforms
---

### Post by gmclachl on 2006-03-30
I am trying to set up trac, and keep getting the error message 

 Failed to initialize environment. No module named svn

 I have installed python-svn already and python2.4-svn 

 when I try 

  python 
  
  >>>from svn import fs 

 I get 

 Traceback (most recent call last):
  File "<stdin>", line 1, in ?
ImportError: No module named svn

 George

---

### Post by chwong on 2008-03-13
Had the same issue, if anyone else is wondering you need python-subversion to solve this error message.

---

