---
title: "gufw issues after upgrading to python3.5 - ubuntu 16"
date: 2016-06-18
forum: Security
---

### Post by scojopa on 2016-06-18
When I try to run gufw I get

[HTML]Traceback (most recent call last):  File "/usr/share/gufw/gufw/gufw.py", line 19, in <module>    from controller import Controller   File "/usr/share/gufw/gufw/controller.py", line 18, in <module>    from model.frontend import Frontend  File "/usr/share/gufw/gufw/model/frontend.py", line 18, in <module>    from firewall import FirewallImportError: No module named 'firewall'[/HTML]
when I try to repair, uninstall or purge
[HTML]dpkg: error processing package gufw (--configure): package is in a very bad inconsistent state; you should reinstall it before attempting configuration[/HTML]
[HTML]Do you want to continue? [Y/n] Ydpkg: error processing package gufw (--remove): package is in a very bad inconsistent state; you should reinstall it before attempting a removalErrors were encountered while processing: gufw[/HTML]
Preparing to unpack .../gufw_16.04.1-0ubuntu1.1_all.deb ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
  File "/usr/bin/pyclean", line 63
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error processing archive /var/cache/apt/archives/gufw_16.04.1-0ubuntu1.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 38, in <module>
    from debpython.namespace import add_namespace_files
  File "/usr/share/python/debpython/namespace.py", line 120
    except (IOError, OSError), e:
                             ^
SyntaxError: invalid syntax
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/gufw_16.04.1-0ubuntu1.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by steeldriver on 2016-06-18
What exactly did you upgrade, and how? 16.04 should have come with python3 v 3.5.1 out of the box

---

### Post by scojopa on 2016-06-18
sorry you are right - did not upgrade
Just changed the system to default to python3.5

---

