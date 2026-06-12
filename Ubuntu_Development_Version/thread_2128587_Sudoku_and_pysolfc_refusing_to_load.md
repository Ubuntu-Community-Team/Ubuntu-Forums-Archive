---
title: "Sudoku and pysolfc refusing to load"
date: 2013-03-23
forum: Ubuntu Development Version
---

### Post by henwyn on 2013-03-23
A couple of games that I sometimes use, sudoku and pysolfc, seem to install all right but will not load and execute. I am temporarily stumped and open to any suggestions. Thanks.

---

### Post by rburkartjo on 2013-03-23
same on my end. dont know what the problem is. but i am running xubuntu 13.04 beta so dont know if it is due to that or something else

---

### Post by chaat on 2013-03-24
I have installed Lubuntu 13.04 in a Virtual Box machine. I've installed the PYSOLFC game and its cardset. When I attempt to start it in a console window I get the following messages. 

spcwh2@lubuntu-1304:~$ pysolfc
Traceback (most recent call last):
  File "/usr/games/pysolfc", line 29, in <module>
    from pysollib.main import main
  File "/usr/share/games/pysolfc/pysollib/main.py", line 31, in <module>
    from util import DataLoader
  File "/usr/share/games/pysolfc/pysollib/util.py", line 53, in <module>
    from mfxutil import Image
  File "/usr/share/games/pysolfc/pysollib/mfxutil.py", line 51, in <module>
    import GifImagePlugin
ImportError: No module named GifImagePlugin
spcwh2@lubuntu-1304:~$ 


I'm pretty sure that this is a PYTHON game using version 2 of python.
can someone help me to resolve this issue ?  

I am a novice when it comes to linux but willing to learn.

                Thanks,

                  Chuck H

---

### Post by rburkartjo on 2013-03-24
there seems to be a problem with pysol and 13.04 it doesnt work. have to wait and see what happens. hopefully the daily updates will fix in time.

---

### Post by chaat on 2013-03-24
have you tried to start them from a terminal ? 

I'm having the same issue and here is what I get when starting pysolfc in a terminal.

spcwh2@lubuntu-1304:~$ pysolfc
Traceback (most recent call last):
  File "/usr/games/pysolfc", line 29, in <module>
    from pysollib.main import main
  File "/usr/share/games/pysolfc/pysollib/main.py", line 31, in <module>
    from util import DataLoader
  File "/usr/share/games/pysolfc/pysollib/util.py", line 53, in <module>
    from mfxutil import Image
  File "/usr/share/games/pysolfc/pysollib/mfxutil.py", line 51, in <module>
    import GifImagePlugin
ImportError: No module named GifImagePlugin
spcwh2@lubuntu-1304:~$ 


I did open a separate thread on it as i did not notice this one.  Perhaps something related to PYTHON 2 but I'm a novice on linux.

                         Thanks,

                            Chuck H.

---

### Post by cariboo on 2013-03-24
Merged two similar threads.

---

### Post by usulofarakis on 2013-03-26
I have the same issue.

I've submitted a bug report.

[https://bugs.launchpad.net/ubuntu/+source/pysolfc/+bug/1160571](https://bugs.launchpad.net/ubuntu/+source/pysolfc/+bug/1160571)

---

### Post by rburkartjo on 2013-03-26
usu good. i had to download a windows version ! for my wife she loves pysolfc

---

### Post by rburkartjo on 2013-03-28
last set of updates fixed pysolfc  on my end.

---

### Post by chaat on 2013-03-29
Yep,  mine is working now as well.

       Chuck H.

---

