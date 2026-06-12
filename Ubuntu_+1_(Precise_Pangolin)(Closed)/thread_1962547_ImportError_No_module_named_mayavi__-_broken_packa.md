---
title: "ImportError: No module named mayavi  - broken package?"
date: 2012-04-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by miobrad on 2012-04-21
i have a python script that stopped working after the upgrade to 12.04, here is the error message:

------------------------------------------------------------
Traceback (most recent call last):
  File "./myscript.py", line 6, in <module>
    from enthought.mayavi import mlab
ImportError: No module named mayavi
------------------------------------------------------------

when i look for enthought i found and tried installing python-envisagecore but i get this message:

------------------------------------------------------------
Setting up python-envisagecore (3.2.0-2build1) ...
Error processing line 2 of /usr/lib/python2.7/dist-packages/EnvisageCore-3.2.0-nspkg.pth:

  Traceback (most recent call last):
    File "/usr/lib/python2.7/site.py", line 157, in addpackage
      exec line
    File "<string>", line 1, in <module>
  KeyError: 'enthought'

Remainder of file ignored
Error processing line 2 of /usr/lib/python2.7/dist-packages/EnvisagePlugins-3.2.0-nspkg.pth:

  Traceback (most recent call last):
    File "/usr/lib/python2.7/site.py", line 157, in addpackage
      exec line
    File "<string>", line 1, in <module>
  KeyError: 'enthought'

Remainder of file ignored
Setting up python-envisageplugins (3.2.0-2build1) ...
Error processing line 3 of /usr/lib/python2.7/dist-packages/EnvisagePlugins-3.2.0-nspkg.pth:

  Traceback (most recent call last):
    File "/usr/lib/python2.7/site.py", line 157, in addpackage
      exec line
    File "<string>", line 1, in <module>
  KeyError: 'enthought'

Remainder of file ignored
------------------------------------------------------------

so, i believe some packages are broken - thanks for any insight! i will post if i found a solution.

---

### Post by MadCow108 on 2012-04-21
do you have mayavi2 installed for the first problem?

the second problem can be solved by reinstalling it
apt-get install --reinstall python-envisagecore

though I don't know what causes it

---

