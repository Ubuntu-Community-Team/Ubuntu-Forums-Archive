---
title: "How to set up PyQt4 for python 3.2 in Ubuntu 11.04"
date: 2011-06-07
forum: Tutorials
---

### Post by neurobot on 2011-06-07
1) Open the synaptic package manager and install python 3.2
2) Open a terminal emulator and type ```
sudo apt-get install libqt4-dev
```3) Download the program SIP from [http://www.riverbankcomputing.co.uk/static/Downloads/sip4/sip-4.12.3.tar.gz](http://www.riverbankcomputing.co.uk/static/Downloads/sip4/sip-4.12.3.tar.gz)
4) extract the folder using tar -xzf sip-4.12.3.tar.gz, cd into folder
5) in terminal emultator, type ```
python3.2 configure.py
make
sudo make install
```now sip is installed
6) install pyqt4 with the command ```
sudo apt-get install python-qt4 qt4-dev-tools python-qt4-dev pyqt4-dev-tools
``` If that didn't work for you, download pyqt4 from [http://www.riverbankcomputing.co.uk/static/Downloads/PyQt4/PyQt-x11-gpl-4.8.4.tar.gz](http://www.riverbankcomputing.co.uk/static/Downloads/PyQt4/PyQt-x11-gpl-4.8.4.tar.gz)
 Untar and install pyqt4 the same way you installed SIP

you should be able to type in terminal ```
python3.2
>>import sys
>>from PyQt4 import QtGui
```If you didn't get any errors, you installed everything correctly

---

### Post by amartinis on 2011-06-08
Thank you very much. Your clear instructions worked perfectly.

---

### Post by ikt on 2011-07-12
Just bumping this because it's really great!

---

### Post by charlie42 on 2011-07-29
Hello everyone,

 I try to install PyQt for Python3 on Debian6 (I know that here is Ubuntu, but Ubuntu and Debian are pretty close, I hope to find a solution here).

 The installation is complicated (currently) at the make command to sip install.

 Here is an excerpt of the error message I get in the terminal

> siplib.c: In function ‘sip_api_convert_from_sequence_index’:
siplib.c:5279: error: ‘PyExc_IndexError’ undeclared (first use in this function)
siplib.c: At top level:
siplib.c:5291: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
siplib.c:5317: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
...
...
...
...
siplib.c:10457: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
siplib.c:10468: error: expected ‘)’ before ‘*’ token
siplib.c:10496: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
siplib.c:10506: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
siplib.c:10534: error: expected ‘)’ before ‘*’ token
siplib.c:10557: error: expected ‘)’ before ‘*’ token
siplib.c:10582: error: expected ‘)’ before ‘*’ token
siplib.c:10816: error: expected ‘)’ before ‘*’ token
siplib.c:10827: error: expected ‘)’ before ‘*’ token
siplib.c: In function ‘raiseNoWChar’:
siplib.c:10840: error: ‘PyExc_SystemError’ undeclared (first use in this function)
siplib.c: At top level:
siplib.c:10849: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
siplib.c:10882: error: expected ‘)’ before ‘*’ token
make[1]: *** [siplib.o] Erreur 1
make[1]: quittant le répertoire « /home/charlie/Téléchargements/sip-4.12.3/siplib »
make: *** [all] Erreur 2If anyone has an idea, I'm interested greatly.

 In advance thank you.

---

### Post by benson444 on 2011-07-29
I think you need to install the Python 3 development package. i.e. python3-dev, python3.2-dev or something like that.

---

### Post by charlie42 on 2011-07-29
Thank you very much, it is this that I was missing

---

### Post by mguillech on 2011-09-05
Hi, very useful post! Although I couldn't manage to install the library with 2.x and 3.x coexisting in the same setup. Has anyone of you managed to do so?

---

### Post by gnudun on 2012-03-12
Hi thank you a lot for this guide! I had to recompile everything on my 11.10 but now everything's working;)

---

### Post by prismctg on 2012-03-17
Thanx a lot for this tutorial , i m searching this kind of tutorial for a while ..... :)

---

### Post by Robin H on 2012-05-21
Thanks for the help.
However I have to do a *few* extra steps like installing python3.2-dev and g++

I'm running Ubuntu 12.04

1) Install python3.2 using the software centre
2) Open terminal and type ```
sudo apt-get install python3.2-dev libqt4-dev g++ python-qt4 qt4-dev-tools python-qt4-dev pyqt4-dev-tools
```
3) Download SIP [http://www.riverbankcomputing.co.uk/software/sip/download](http://www.riverbankcomputing.co.uk/software/sip/download)
4) Download PyQt [http://www.riverbankcomputing.co.uk/software/pyqt/download](http://www.riverbankcomputing.co.uk/software/pyqt/download)
5) Untar both downloads
6) cd into sip folder
7) run ```
python3.2 configure.py;make;sudo make install
```
8] cd into pyqt folder
9) run ```
python3.2 configure.py;make;sudo make install
```
10) test if it works like neurobot says in first post.

---

### Post by idom on 2012-12-11
> **Robin H said:**
> Thanks for the help.
However I have to do a *few* extra steps like installing python3.2-dev and g++

I'm running Ubuntu 12.04

1) Install python3.2 using the software centre
2) Open terminal and type ```
sudo apt-get install python3.2-dev libqt4-dev g++ python-qt4 qt4-dev-tools python-qt4-dev pyqt4-dev-tools
```
3) Download SIP [http://www.riverbankcomputing.co.uk/software/sip/download](http://www.riverbankcomputing.co.uk/software/sip/download)
4) Download PyQt [http://www.riverbankcomputing.co.uk/software/pyqt/download](http://www.riverbankcomputing.co.uk/software/pyqt/download)
5) Untar both downloads
6) cd into sip folder
7) run ```
python3.2 configure.py;make;sudo make install
```
8] cd into pyqt folder
9) run ```
python3.2 configure.py;make;sudo make install
```
10) test if it works like neurobot says in first post.

It works perfectly with ubntun12.04 
thanks for all the trouble. 
Instructions were very precise and clear.

---

