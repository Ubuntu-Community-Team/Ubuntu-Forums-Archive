---
title: "pyvenv-3.3 seems to be misbehaving"
date: 2013-01-07
forum: Ubuntu Development Version
---

### Post by mruffalo on 2013-01-07
Hi all-

I use Python 3 exclusively, and for the past few Ubuntu releases I've created a virtualenv in my home directory that's automatically activated in my .bashrc.

I just did a fresh install of Kubuntu Raring on one of my machines, and decided to try the new pyvenv script that comes with 3.3. After creating the venv and installing a package into it, I'm unable to import it.

Steps to reproduce:

[LIST=1]
[*]Ensure that important packages are installed: gcc, python3-dev, maybe others.
[*]Create a new Python 3.3 virtualenv:
pyvenv-3.3 ~/.py3-venv
[*]Activate this virtualenv:
. ~/.py3-venv/bin/activate
[*]Ensure that you're now running the right Python:
which python
[*]Install a package  with "python setup.py build && python setup.py install". I used NumPy for this. I noted in the installation output that the library was installed to ~/.py3-venv/lib/python3.3/site-packages (this location now contains a "numpy" directory and a "numpy-1.7.0rc1.egg-info" file).
[*]Try to import the new package:
python -c "import numpy"
[/LIST]

Expected output: nothing (numpy should be imported)
Actual output:
```
Traceback (most recent call last):
  File "<string>", line 1, in <module>
ImportError: No module named 'numpy'
```I've attached a bzip2'd strace capture of 'python -c "import numpy"'. It starts to get interesting around line 628 -- it looks like the module loader is searching the "dist-packages" directories in various places and skips the "site-packages" directory where numpy is installed.

This seems like a bug, and I'm guessing that it's specific to the Ubuntu 13.04 Python 3.3 package. This didn't occur in Ubuntu Quantal after installing the optional python3.3 package, and it doesn't occur with a vanilla Python 3.3 source installation on other distributions like CentOS.

Has anyone else experienced this?

---

