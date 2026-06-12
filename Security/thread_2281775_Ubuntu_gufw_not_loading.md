---
title: "Ubuntu gufw not loading"
date: 2015-06-09
forum: Security
---

### Post by petsoukos on 2015-06-09
[COLOR=#111111][FONT=Ubuntu]OS: Ubuntu 14.04 64bit
Python2 Version 2.7.10
Python3 Version 3.4.3
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I recently installed python from source and gufw stopped loading. When I try to launch it from terminal I get the following errors:
[/FONT][/COLOR]
Traceback (most recent call last):
  File "/usr/share/gufw/gufw/gufw.py", line 19, in <module>
    from controller import Controller 
  File "/usr/share/gufw/gufw/controller.py", line 18, in <module>
    from model.frontend import Frontend
  File "/usr/share/gufw/gufw/model/frontend.py", line 18, in <module>
    from firewall import Firewall
  File "/usr/share/gufw/gufw/model/firewall.py", line 20, in <module>
    from netifaces import interfaces, ifaddresses, AF_INET
ImportError: No module named netifaces


[COLOR=#111111][FONT=Ubuntu]Netifaces is installed but can't be loaded by Python2, Python3 loads it just fine.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Tried reinstalling netifaces, Pythons from repos, but nothing worked.
Manually added to PYTHONPATH the path to netifaces for python2, this makes Python2 load the module while testing with python -c "import netifaces", but gufw still doesn't load.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any ideas why gufw can't find that module ?[/FONT][/COLOR]

---

### Post by petsoukos on 2015-06-19
Still an ongoing issue on my ubuntu.

---

### Post by cariboo on 2015-06-19
It seems that the version of python you are using is the problem. Do you really change ufw rules often enough that you need a gui front end for ufw?

---

### Post by petsoukos on 2015-06-28
Yes, actually.

The python built from source messed other programs as well. Again the error was ImportError No module named... etc

---

