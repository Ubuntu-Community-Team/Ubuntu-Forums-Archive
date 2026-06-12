---
title: "Problem installing Calibre (eBook creator)"
date: 2009-05-17
forum: Ubuntu Studio
---

### Post by MeKino on 2009-05-17
Hi,

I'm trying to install Calibre:

[http://calibre.kovidgoyal.net/download_linux](http://calibre.kovidgoyal.net/download_linux)

and get the following error message:

xxx@xxx-desktop:~/calibre-0.5.12$ python setup.py build && sudo python setup.py install
Setup calibre version: 0.5.12
Traceback (most recent call last):
  File "setup.py", line 49, in <module>
    from setuptools import setup, find_packages
ImportError: No module named setuptools


Any ideas?

The program does seem to have been installed... I tried converting an rtf file but it just hung up.

Thanks in advance.

---

### Post by psablo on 2009-08-04
I too am trying to install Calibre and having difficulty.

There seems to be some dependency issues that I am not experienced enough to deal with, particularly podofo 0.7.0.  Since it is not in Synaptic I don't know how to install it.

---

### Post by krgp on 2009-09-18
Ditto with the dependencies.

---

### Post by Stochastic on 2009-09-19
Did you guys read through the dependencies list on the download page?  I had no troubles installing Calibre on my machine.

Oh, I just found this PPA with calibre packages. [https://launchpad.net/~fabricesp/+archive/ppa](https://launchpad.net/~fabricesp/+archive/ppa)  It has lots of other things, so make sure you disable it as soon as calibre is installed.

Edit, hmm now that I recall, I may have used a PPA to install it, rather than from their website.  Are you guys installing the binary version from the website or the source version?

---

### Post by Eve23 on 2009-09-20
I am having the same problems and asked if someone could write a newbie guide to upgrading Calibre.

Has anyone tried that PP?

For example, for me when I look at the list of dependencies and do a sudo aptitude search (filename) for example the dependency libusb   0.1.12 
I get the following and don't see anything that I can tell is libusb   0.1.12 

 ~$ sudo aptitude search libusb
p   libusb++-0.1-4c2                - userspace C++ USB programming library     
p   libusb++-dev                    - userspace C++ USB programming library deve
i   libusb-0.1-4                    - userspace USB programming library         
p   libusb-1.0-0                    - userspace USB programming library         
p   libusb-1.0-0-dev                - userspace USB programming library developm
p   libusb-dev                      - userspace USB programming library developm
p   libusbprog-dev                  - Development files for libusbprog          
p   libusbprog0                     - Library for programming the USBprog hardware

Is this what some of the rest of you are experiencing regarding the dependencies installations?  How do we know what specific file we need?

Thank you! :)

---

### Post by Eve23 on 2009-09-20
oops sorry I lost link and it posted twice

---

