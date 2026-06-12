---
title: "mod_python problem"
date: 2006-11-18
forum: Repositories &amp; Backports
---

### Post by Mark Sibly on 2006-11-18
Hi,

I have installed the apache2 mod_python package using...

sudo apt-get install apache2-mod-python

...and it 'sort of' works.

I'm trying to use it to run a python script to authenticate a certain directory, and the mod_python docs reckon your python script needs this...

from mod_python import apache

...but this causes the script to fail.

Looking at mod_python, apache.py code attempts to import _apache, but I can't find this anywhere. Hence the failure.

I worked around it by copying the bits out of apache.py into my own code that I needed - fortunately, just some HTTP_ constants.

But where is _apache.py? Have I installed mod_python incorrectly? Do I need to install more?

Bye!
Mark

---

