---
title: "Problem with &quot;Traceback&quot; while running theHarvester"
date: 2019-11-07
forum: Security
---

### Post by knolof on 2019-11-07
I'm running KDE Neon v5.17 with Python 3.7

My problem is that theHarvester simply wont work. This is the error I get.

```
Traceback (most recent call last):
  File "theHarvester.py", line 9, in <module>
    from theHarvester import __main__
  File "/home/justin/theHarvester/theHarvester/__init__.py", line 1, in <module>
    from gevent import monkey as curious_george
ModuleNotFoundError: No module named 'gevent'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 63, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python3/dist-packages/apport/__init__.py", line 5, in <module>
    from apport.report import Report
  File "/usr/lib/python3/dist-packages/apport/report.py", line 30, in <module>
    import apport.fileutils
  File "/usr/lib/python3/dist-packages/apport/fileutils.py", line 23, in <module>
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python3/dist-packages/apport/packaging_impl.py", line 24, in <module>
    import apt
  File "/usr/lib/python3/dist-packages/apt/__init__.py", line 23, in <module>
    import apt_pkg
ModuleNotFoundError: No module named 'apt_pkg'

Original exception was:
Traceback (most recent call last):
  File "theHarvester.py", line 9, in <module>
    from theHarvester import __main__
  File "/home/justin/theHarvester/theHarvester/__init__.py", line 1, in <module>
    from gevent import monkey as curious_george
ModuleNotFoundError: No module named 'gevent'


```

Now I'm in the early process of learning Python so I really have no clue whats going on here or if this problem can even be fixed.

Any help will be greatly appreciated. Thank you.

---

### Post by uRock on 2019-11-07
Per our CoC, we do not offer support with penetration tools. 

Thread Closed.

---

