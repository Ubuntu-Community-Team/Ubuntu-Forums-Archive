---
title: "Inkscape can't save PLT files : can't find sk1libs.utils.fs"
date: 2016-12-17
forum: Ubuntu Studio
---

### Post by nickTaylor1181 on 2016-12-17
Hi all.


I have a new install of Ubuntu Studio (16.04) XFCE: 4.12

with Inkscape : 0.91


Which I am very dependent on for my laser-cutter/business. My laser-cutters work best with PLT files - and inkscape has been fine with these for the last 6 years over multiple laptops. Now however, it is saying:

```
UniConvertor failed:

Traceback (most recent call last):
  File "/usr/bin/uniconvertor", line 13, in <module>
    uniconv_run()
  File "/usr/lib/python2.7/dist-packages/uniconvertor/__init__.py", line 83, in uniconv_run
    from app.io import load
  File "/usr/lib/python2.7/dist-packages/uniconvertor/app/__init__.py", line 69, in <module>
    from conf.configurator import Configurator
  File "/usr/lib/python2.7/dist-packages/uniconvertor/app/conf/configurator.py", line 11, in <module>
    from app.events import connector
  File "/usr/lib/python2.7/dist-packages/uniconvertor/app/__init__.py", line 69, in <module>
    from conf.configurator import Configurator
  File "/usr/lib/python2.7/dist-packages/uniconvertor/app/conf/configurator.py", line 13, in <module>
    from sk1libs.utils.fs import gethome
ImportError: No module named sk1libs.utils.fs



```

And won't save.



Any ideas?





Nick

---

### Post by Pascal_Humbert on 2017-01-19
Same error... 

I installed Mint 18 2 weeks ago. When i tried to export drawing in PLT from inkscape, i get the same warning:
> [h=1][FONT=arial]*[Inkscape can't save PLT files : [...] can't find sk1libs.utils.fs]("https://ubuntuforums.org/showthread.php?t=2346725&")*[/FONT][/h]

When i used this function for the last time (ca. 3 months ago), it works well.

I reinstalled Inkscape and uniconvertor for the standard source --> no improvement.

still seeking for an answer.


humbp

---

### Post by ian-weisser on 2017-01-19
It's a bug: [https://bugs.debian.org/820748](https://bugs.debian.org/820748)
Anyone wanting to take a swing at fixing is welcome....

---

