---
title: "Problems with ufw"
date: 2013-11-05
forum: Security
---

### Post by alexander.suter.ch on 2013-11-05
hello all!

I'm using ubuntu 12.04 LTS . I installed ufw. And when i call for example:

```
ufw enable
```

Then i see the following output: Illegal instruction

Can anyone help me?
Thx

---

### Post by deadflowr on 2013-11-05
Are you running as root?
```
sudo ufw enable
```
By default, Ubuntu doesn't have root enabled.
The initial user gets admin rights(sudo),which allow root access.

If you haven't used sudo before, when used in a terminal, it'll prompt for password.
The password field will be blank when typing, so enter the password you set at install as best you remember it and hit enter.

FYI, on Ubuntu ufw is already installed, it just is not enabled.

---

### Post by alexander.suter.ch on 2013-11-05
Thank you for your reply!

I'm logged in with root. When I type the following with root or as an other user:

```
sudo ufw enable
```

there happens nothing - no message nothing ... ?!

I wanted to check with

```
ufw status
```

but there is also no message return?!=?

---

### Post by deadflowr on 2013-11-05
Copy and post the output, please.

Added: you can also post the output for

```
apt-cache policy ufw
```

---

### Post by alexander.suter.ch on 2013-11-05
There is no output for

```
sudo ufw status
```

and there is "illegal instruction" for

```
ufw status
```

and there is the following output 

ufw:
  Installed: 0.31.1-1
  Candidate: 0.31.1-1
  Version table:
 *** 0.31.1-1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main amd64 Packages
        100 /var/lib/dpkg/status


for your command

---

### Post by deadflowr on 2013-11-05
Try purging and then run update and then reinstall it
```
sudo apt-get purge ufw
```
Which will remove the package.
Then 
```
sudo apt-get clean
```
Which will clear the package lists
Then
```
sudo apt-get update
```
Which will refresh the package list
Then
```
sudo apt-get install ufw
```

Do you have some specific reason to login as root?
If not, then don't.

Added: If any thing seems out of place, post it.

---

### Post by alexander.suter.ch on 2013-11-05
Thank you very much.

No i don't have a specific reason - just to solve this problem. 

I can't belive it. I did all with success and the problem is still not solved:


```
root@rohkost:/etc/apache2/sites-available# apt-get purge ufw
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  ufw*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 694 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 24329 files and directories currently installed.)
Removing ufw ...
Purging configuration files for ufw ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
root@rohkost:/etc/apache2/sites-available# apt-get clean
root@rohkost:/etc/apache2/sites-available# apt-get update
Ign http://security.ubuntu.com precise-security InRelease
Ign http://archive.ubuntu.com precise InRelease
Ign http://archive.ubuntu.com precise-updates InRelease
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:2 http://archive.ubuntu.com precise Release.gpg [198 B]
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]
Get:4 http://archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:5 http://archive.ubuntu.com precise Release [49.6 kB]
Get:6 http://security.ubuntu.com precise-security/main amd64 Packages [334 kB]
Get:7 http://archive.ubuntu.com precise-updates Release [49.6 kB]
Get:8 http://security.ubuntu.com precise-security/main i386 Packages [353 kB]
Get:9 http://archive.ubuntu.com precise/main amd64 Packages [1,273 kB]
Get:10 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:11 http://security.ubuntu.com precise-security/main Translation-en [158 kB]
Get:12 http://archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]
Get:13 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]
Get:14 http://archive.ubuntu.com precise/universe i386 Packages [4,796 kB]
Get:15 http://archive.ubuntu.com precise/main TranslationIndex [3,706 B]
Get:16 http://archive.ubuntu.com precise/universe TranslationIndex [2,922 B]
Get:17 http://archive.ubuntu.com precise-updates/main amd64 Packages [701 kB]
Get:18 http://archive.ubuntu.com precise-updates/universe amd64 Packages [220 kB]
Get:19 http://archive.ubuntu.com precise-updates/main i386 Packages [722 kB]
Get:20 http://archive.ubuntu.com precise-updates/universe i386 Packages [225 kB]
Get:21 http://archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:22 http://archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://archive.ubuntu.com precise/main Translation-en
Hit http://archive.ubuntu.com precise/universe Translation-en
Get:23 http://archive.ubuntu.com precise-updates/main Translation-en [317 kB]
Get:24 http://archive.ubuntu.com precise-updates/universe Translation-en [129 kB]
Fetched 15.4 MB in 36s (427 kB/s)
Reading package lists... Done
root@rohkost:/etc/apache2/sites-available# apt-get install ufw
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  ufw
0 upgraded, 1 newly installed, 0 to remove and 158 not upgraded.
Need to get 153 kB of archives.
After this operation, 694 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ precise/main ufw all 0.31.1-1 [153 kB]
Fetched 153 kB in 0s (795 kB/s)
Preconfiguring packages ...
Selecting previously unselected package ufw.
(Reading database ... 24234 files and directories currently installed.)
Unpacking ufw (from .../archives/ufw_0.31.1-1_all.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up ufw (0.31.1-1) ...


Creating config file /etc/ufw/before.rules with new version
Creating config file /etc/ufw/before6.rules with new version
Creating config file /etc/ufw/after.rules with new version
Creating config file /etc/ufw/after6.rules with new version

root@rohkost:/etc/apache2/sites-available# ufw status
Illegal instruction

root@rohkost:/etc/apache2/sites-available#

```

---

### Post by steeldriver on 2013-11-05
Is there perhaps some other executable called 'ufw' (either a different version than the one installed using apt-get, or a different program entirely) that occurs earlier on roots PATH? what are the results of

```

echo $PATH

type ufw

ufw --version

```

---

### Post by alexander.suter.ch on 2013-11-06
echo $PATH

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

type ufw
ufw is /usr/sbin/ufw

ufw --version
Illegal instruction

---

### Post by steeldriver on 2013-11-06
Well I guess that's a python error (ufw is a python script) - what version of python are you running?

```
python --version
```

---

### Post by alexander.suter.ch on 2013-11-06
its Python 2.7.3

---

### Post by alexander.suter.ch on 2013-11-06
no more ideas?

---

### Post by steeldriver on 2013-11-06
well I'm clutching at straws here but I guess you could run ufw from an interactive python session with verbosity turned on, and see what is happening right around the point it fails - something like

```
sudo python -vv $(which ufw) status 2>&1 | less
```

(I suggest piping it through 'less' because there will be a LOT of stuff)

---

### Post by alexander.suter.ch on 2013-11-06
Here you see the output: I dont think that anyone cant find a mistake?!

```
# installing zipimport hookimport zipimport # builtin
# installed zipimport hook
# trying /usr/lib/python2.7/site.so
# trying /usr/lib/python2.7/sitemodule.so
# trying /usr/lib/python2.7/site.py
# /usr/lib/python2.7/site.pyc matches /usr/lib/python2.7/site.py
import site # precompiled from /usr/lib/python2.7/site.pyc
# trying /usr/lib/python2.7/os.so
# trying /usr/lib/python2.7/osmodule.so
# trying /usr/lib/python2.7/os.py
# /usr/lib/python2.7/os.pyc matches /usr/lib/python2.7/os.py
import os # precompiled from /usr/lib/python2.7/os.pyc
import errno # builtin
import posix # builtin
# trying /usr/lib/python2.7/posixpath.so
# trying /usr/lib/python2.7/posixpathmodule.so
# trying /usr/lib/python2.7/posixpath.py
# /usr/lib/python2.7/posixpath.pyc matches /usr/lib/python2.7/posixpath.py
import posixpath # precompiled from /usr/lib/python2.7/posixpath.pyc
# trying /usr/lib/python2.7/stat.so
# trying /usr/lib/python2.7/statmodule.so
# trying /usr/lib/python2.7/stat.py
# /usr/lib/python2.7/stat.pyc matches /usr/lib/python2.7/stat.py
import stat # precompiled from /usr/lib/python2.7/stat.pyc
# trying /usr/lib/python2.7/genericpath.so
# trying /usr/lib/python2.7/genericpathmodule.so
# trying /usr/lib/python2.7/genericpath.py
# /usr/lib/python2.7/genericpath.pyc matches /usr/lib/python2.7/genericpath.py
import genericpath # precompiled from /usr/lib/python2.7/genericpath.pyc
# trying /usr/lib/python2.7/warnings.so
# trying /usr/lib/python2.7/warningsmodule.so
# trying /usr/lib/python2.7/warnings.py
# /usr/lib/python2.7/warnings.pyc matches /usr/lib/python2.7/warnings.py
import warnings # precompiled from /usr/lib/python2.7/warnings.pyc
# trying /usr/lib/python2.7/linecache.so
# trying /usr/lib/python2.7/linecachemodule.so
# trying /usr/lib/python2.7/linecache.py
# /usr/lib/python2.7/linecache.pyc matches /usr/lib/python2.7/linecache.py
import linecache # precompiled from /usr/lib/python2.7/linecache.pyc
# trying /usr/lib/python2.7/types.so
# trying /usr/lib/python2.7/typesmodule.so
# trying /usr/lib/python2.7/types.py
# /usr/lib/python2.7/types.pyc matches /usr/lib/python2.7/types.py
import types # precompiled from /usr/lib/python2.7/types.pyc
# trying /usr/lib/python2.7/UserDict.so
# trying /usr/lib/python2.7/UserDictmodule.so
# trying /usr/lib/python2.7/UserDict.py
# /usr/lib/python2.7/UserDict.pyc matches /usr/lib/python2.7/UserDict.py
import UserDict # precompiled from /usr/lib/python2.7/UserDict.pyc
# trying /usr/lib/python2.7/_abcoll.so
# trying /usr/lib/python2.7/_abcollmodule.so
# trying /usr/lib/python2.7/_abcoll.py
# /usr/lib/python2.7/_abcoll.pyc matches /usr/lib/python2.7/_abcoll.py
import _abcoll # precompiled from /usr/lib/python2.7/_abcoll.pyc
# trying /usr/lib/python2.7/abc.so
# trying /usr/lib/python2.7/abcmodule.so
# trying /usr/lib/python2.7/abc.py
# /usr/lib/python2.7/abc.pyc matches /usr/lib/python2.7/abc.py
import abc # precompiled from /usr/lib/python2.7/abc.pyc
# trying /usr/lib/python2.7/_weakrefset.so
# trying /usr/lib/python2.7/_weakrefsetmodule.so
# trying /usr/lib/python2.7/_weakrefset.py
# /usr/lib/python2.7/_weakrefset.pyc matches /usr/lib/python2.7/_weakrefset.py
import _weakrefset # precompiled from /usr/lib/python2.7/_weakrefset.pyc
import _weakref # builtin
# trying /usr/lib/python2.7/copy_reg.so
# trying /usr/lib/python2.7/copy_regmodule.so
# trying /usr/lib/python2.7/copy_reg.py
# /usr/lib/python2.7/copy_reg.pyc matches /usr/lib/python2.7/copy_reg.py
import copy_reg # precompiled from /usr/lib/python2.7/copy_reg.pyc
# trying /usr/lib/python2.7/traceback.so
# trying /usr/lib/python2.7/tracebackmodule.so
# trying /usr/lib/python2.7/traceback.py
# /usr/lib/python2.7/traceback.pyc matches /usr/lib/python2.7/traceback.py
import traceback # precompiled from /usr/lib/python2.7/traceback.pyc
# trying /usr/lib/python2.7/sysconfig.so
# trying /usr/lib/python2.7/sysconfigmodule.so
# trying /usr/lib/python2.7/sysconfig.py
# /usr/lib/python2.7/sysconfig.pyc matches /usr/lib/python2.7/sysconfig.py
import sysconfig # precompiled from /usr/lib/python2.7/sysconfig.pyc
# trying /usr/lib/python2.7/re.so
# trying /usr/lib/python2.7/remodule.so
# trying /usr/lib/python2.7/re.py
# /usr/lib/python2.7/re.pyc matches /usr/lib/python2.7/re.py
import re # precompiled from /usr/lib/python2.7/re.pyc
# trying /usr/lib/python2.7/sre_compile.so
# trying /usr/lib/python2.7/sre_compilemodule.so
# trying /usr/lib/python2.7/sre_compile.py
# /usr/lib/python2.7/sre_compile.pyc matches /usr/lib/python2.7/sre_compile.py
import sre_compile # precompiled from /usr/lib/python2.7/sre_compile.pyc
import _sre # builtin
# trying /usr/lib/python2.7/sre_parse.so
# trying /usr/lib/python2.7/sre_parsemodule.so
# trying /usr/lib/python2.7/sre_parse.py
# /usr/lib/python2.7/sre_parse.pyc matches /usr/lib/python2.7/sre_parse.py
import sre_parse # precompiled from /usr/lib/python2.7/sre_parse.pyc
# trying /usr/lib/python2.7/sre_constants.so
# trying /usr/lib/python2.7/sre_constantsmodule.so
# trying /usr/lib/python2.7/sre_constants.py
# /usr/lib/python2.7/sre_constants.pyc matches /usr/lib/python2.7/sre_constants.py
import sre_constants # precompiled from /usr/lib/python2.7/sre_constants.pyc
# trying /usr/lib/python2.7/sitecustomize.so
# trying /usr/lib/python2.7/sitecustomizemodule.so
# trying /usr/lib/python2.7/sitecustomize.py
# /usr/lib/python2.7/sitecustomize.pyc matches /usr/lib/python2.7/sitecustomize.py
import sitecustomize # precompiled from /usr/lib/python2.7/sitecustomize.pyc
# trying /usr/lib/python2.7/apport_python_hook.so
# trying /usr/lib/python2.7/apport_python_hookmodule.so
# trying /usr/lib/python2.7/apport_python_hook.py
# trying /usr/lib/python2.7/apport_python_hook.pyc
# trying /usr/lib/python2.7/plat-linux2/apport_python_hook.so
# trying /usr/lib/python2.7/plat-linux2/apport_python_hookmodule.so
# trying /usr/lib/python2.7/plat-linux2/apport_python_hook.py
# trying /usr/lib/python2.7/plat-linux2/apport_python_hook.pyc
# trying /usr/lib/python2.7/lib-tk/apport_python_hook.so
# trying /usr/lib/python2.7/lib-tk/apport_python_hookmodule.so
# trying /usr/lib/python2.7/lib-tk/apport_python_hook.py
# trying /usr/lib/python2.7/lib-tk/apport_python_hook.pyc
# trying /usr/lib/python2.7/lib-dynload/apport_python_hook.so
# trying /usr/lib/python2.7/lib-dynload/apport_python_hookmodule.so
# trying /usr/lib/python2.7/lib-dynload/apport_python_hook.py
# trying /usr/lib/python2.7/lib-dynload/apport_python_hook.pyc
# trying /usr/local/lib/python2.7/dist-packages/apport_python_hook.so
# trying /usr/local/lib/python2.7/dist-packages/apport_python_hookmodule.so
# trying /usr/local/lib/python2.7/dist-packages/apport_python_hook.py
# trying /usr/local/lib/python2.7/dist-packages/apport_python_hook.pyc
# trying /usr/lib/python2.7/dist-packages/apport_python_hook.so
# trying /usr/lib/python2.7/dist-packages/apport_python_hookmodule.so
# trying /usr/lib/python2.7/dist-packages/apport_python_hook.py
# trying /usr/lib/python2.7/dist-packages/apport_python_hook.pyc
# trying /usr/lib/python2.7/usercustomize.so
# trying /usr/lib/python2.7/usercustomizemodule.so
# trying /usr/lib/python2.7/usercustomize.py
# trying /usr/lib/python2.7/usercustomize.pyc
# trying /usr/lib/python2.7/plat-linux2/usercustomize.so
# trying /usr/lib/python2.7/plat-linux2/usercustomizemodule.so
# trying /usr/lib/python2.7/plat-linux2/usercustomize.py
# trying /usr/lib/python2.7/plat-linux2/usercustomize.pyc
# trying /usr/lib/python2.7/lib-tk/usercustomize.so
# trying /usr/lib/python2.7/lib-tk/usercustomizemodule.so
# trying /usr/lib/python2.7/lib-tk/usercustomize.py
# trying /usr/lib/python2.7/lib-tk/usercustomize.pyc
# trying /usr/lib/python2.7/lib-dynload/usercustomize.so
# trying /usr/lib/python2.7/lib-dynload/usercustomizemodule.so
# trying /usr/lib/python2.7/lib-dynload/usercustomize.py
# trying /usr/lib/python2.7/lib-dynload/usercustomize.pyc
# trying /usr/local/lib/python2.7/dist-packages/usercustomize.so
# trying /usr/local/lib/python2.7/dist-packages/usercustomizemodule.so
# trying /usr/local/lib/python2.7/dist-packages/usercustomize.py
# trying /usr/local/lib/python2.7/dist-packages/usercustomize.pyc
# trying /usr/lib/python2.7/dist-packages/usercustomize.so
# trying /usr/lib/python2.7/dist-packages/usercustomizemodule.so
# trying /usr/lib/python2.7/dist-packages/usercustomize.py
# trying /usr/lib/python2.7/dist-packages/usercustomize.pyc
import encodings # directory /usr/lib/python2.7/encodings
# trying /usr/lib/python2.7/encodings/__init__.so
# trying /usr/lib/python2.7/encodings/__init__module.so
# trying /usr/lib/python2.7/encodings/__init__.py
# /usr/lib/python2.7/encodings/__init__.pyc matches /usr/lib/python2.7/encodings/__init__.py
import encodings # precompiled from /usr/lib/python2.7/encodings/__init__.pyc
# trying /usr/lib/python2.7/encodings/codecs.so
# trying /usr/lib/python2.7/encodings/codecsmodule.so
# trying /usr/lib/python2.7/encodings/codecs.py
# trying /usr/lib/python2.7/encodings/codecs.pyc
# trying /usr/lib/python2.7/codecs.so
# trying /usr/lib/python2.7/codecsmodule.so
# trying /usr/lib/python2.7/codecs.py
# /usr/lib/python2.7/codecs.pyc matches /usr/lib/python2.7/codecs.py
import codecs # precompiled from /usr/lib/python2.7/codecs.pyc
import _codecs # builtin
# trying /usr/lib/python2.7/encodings/encodings.so
# trying /usr/lib/python2.7/encodings/encodingsmodule.so
# trying /usr/lib/python2.7/encodings/encodings.py
# trying /usr/lib/python2.7/encodings/encodings.pyc
# trying /usr/lib/python2.7/encodings/aliases.so
# trying /usr/lib/python2.7/encodings/aliasesmodule.so
# trying /usr/lib/python2.7/encodings/aliases.py
# /usr/lib/python2.7/encodings/aliases.pyc matches /usr/lib/python2.7/encodings/aliases.py
import encodings.aliases # precompiled from /usr/lib/python2.7/encodings/aliases.pyc
# trying /usr/lib/python2.7/encodings/__builtin__.so
# trying /usr/lib/python2.7/encodings/__builtin__module.so
# trying /usr/lib/python2.7/encodings/__builtin__.py
# trying /usr/lib/python2.7/encodings/__builtin__.pyc
# trying /usr/lib/python2.7/encodings/utf_8.so
# trying /usr/lib/python2.7/encodings/utf_8module.so
# trying /usr/lib/python2.7/encodings/utf_8.py
# /usr/lib/python2.7/encodings/utf_8.pyc matches /usr/lib/python2.7/encodings/utf_8.py
import encodings.utf_8 # precompiled from /usr/lib/python2.7/encodings/utf_8.pyc
Python 2.7.3 (default, Apr 20 2012, 22:39:59) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
# trying /usr/sbin/ufw.so
# trying /usr/sbin/ufwmodule.so
# trying /usr/sbin/ufw.py
# trying /usr/sbin/ufw.pyc
# trying /usr/lib/python2.7/ufw.so
# trying /usr/lib/python2.7/ufwmodule.so
# trying /usr/lib/python2.7/ufw.py
# trying /usr/lib/python2.7/ufw.pyc
# trying /usr/lib/python2.7/plat-linux2/ufw.so
# trying /usr/lib/python2.7/plat-linux2/ufwmodule.so
# trying /usr/lib/python2.7/plat-linux2/ufw.py
# trying /usr/lib/python2.7/plat-linux2/ufw.pyc
# trying /usr/lib/python2.7/lib-tk/ufw.so
# trying /usr/lib/python2.7/lib-tk/ufwmodule.so
# trying /usr/lib/python2.7/lib-tk/ufw.py
# trying /usr/lib/python2.7/lib-tk/ufw.pyc
# trying /usr/lib/python2.7/lib-dynload/ufw.so
# trying /usr/lib/python2.7/lib-dynload/ufwmodule.so
# trying /usr/lib/python2.7/lib-dynload/ufw.py
# trying /usr/lib/python2.7/lib-dynload/ufw.pyc
# trying /usr/local/lib/python2.7/dist-packages/ufw.so
# trying /usr/local/lib/python2.7/dist-packages/ufwmodule.so
# trying /usr/local/lib/python2.7/dist-packages/ufw.py
# trying /usr/local/lib/python2.7/dist-packages/ufw.pyc
import ufw # directory /usr/lib/python2.7/dist-packages/ufw
# trying /usr/lib/python2.7/dist-packages/ufw/__init__.so
# trying /usr/lib/python2.7/dist-packages/ufw/__init__module.so
# trying /usr/lib/python2.7/dist-packages/ufw/__init__.py
# /usr/lib/python2.7/dist-packages/ufw/__init__.pyc matches /usr/lib/python2.7/dist-packages/ufw/__init__.py
import ufw # precompiled from /usr/lib/python2.7/dist-packages/ufw/__init__.pyc
# trying /usr/lib/python2.7/dist-packages/ufw/frontend.so
# trying /usr/lib/python2.7/dist-packages/ufw/frontendmodule.so
# trying /usr/lib/python2.7/dist-packages/ufw/frontend.py
# /usr/lib/python2.7/dist-packages/ufw/frontend.pyc matches /usr/lib/python2.7/dist-packages/ufw/frontend.py
import ufw.frontend # precompiled from /usr/lib/python2.7/dist-packages/ufw/frontend.pyc
# trying /usr/lib/python2.7/dist-packages/ufw/os.so
# trying /usr/lib/python2.7/dist-packages/ufw/osmodule.so
# trying /usr/lib/python2.7/dist-packages/ufw/os.py
# trying /usr/lib/python2.7/dist-packages/ufw/os.pyc
# trying /usr/lib/python2.7/dist-packages/ufw/sys.so
# trying /usr/lib/python2.7/dist-packages/ufw/sysmodule.so
# trying /usr/lib/python2.7/dist-packages/ufw/sys.py
# trying /usr/lib/python2.7/dist-packages/ufw/sys.pyc
# trying /usr/lib/python2.7/dist-packages/ufw/warnings.so
# trying /usr/lib/python2.7/dist-packages/ufw/warningsmodule.so
# trying /usr/lib/python2.7/dist-packages/ufw/warnings.py
# trying /usr/lib/python2.7/dist-packages/ufw/warnings.pyc
# trying /usr/lib/python2.7/dist-packages/ufw/ufw.so
# trying /usr/lib/python2.7/dist-packages/ufw/ufwmodule.so
# trying /usr/lib/python2.7/dist-packages/ufw/ufw.py
# trying /usr/lib/python2.7/dist-packages/ufw/ufw.pyc
# trying /usr/lib/python2.7/dist-packages/ufw/common.so
# trying /usr/lib/python2.7/dist-packages/ufw/commonmodule.so
# trying /usr/lib/python2.7/dist-packages/ufw/common.py
# /usr/lib/python2.7/dist-packages/ufw/common.pyc matches /usr/lib/python2.7/dist-packages/ufw/common.py
import ufw.common # precompiled from /usr/lib/python2.7/dist-packages/ufw/common.pyc
# trying /usr/lib/python2.7/dist-packages/ufw/re.so
# trying /usr/lib/python2.7/dist-packages/ufw/remodule.so
# trying /usr/lib/python2.7/dist-packages/ufw/re.py
# trying /usr/lib/python2.7/dist-packages/ufw/re.pyc
# trying /usr/lib/python2.7/dist-packages/ufw/socket.so
# trying /usr/lib/python2.7/dist-packages/ufw/socketmodule.so
# trying /usr/lib/python2.7/dist-packages/ufw/socket.py
# trying /usr/lib/python2.7/dist-packages/ufw/socket.pyc
# trying /usr/sbin/socket.so
# trying /usr/sbin/socketmodule.so
# trying /usr/sbin/socket.py
# trying /usr/sbin/socket.pyc
# trying /usr/lib/python2.7/socket.so
# trying /usr/lib/python2.7/socketmodule.so
# trying /usr/lib/python2.7/socket.py
# /usr/lib/python2.7/socket.pyc matches /usr/lib/python2.7/socket.py
import socket # precompiled from /usr/lib/python2.7/socket.pyc
import _socket # builtin
# trying /usr/sbin/functools.so
# trying /usr/sbin/functoolsmodule.so
# trying /usr/sbin/functools.py
# trying /usr/sbin/functools.pyc
# trying /usr/lib/python2.7/functools.so
# trying /usr/lib/python2.7/functoolsmodule.so
# trying /usr/lib/python2.7/functools.py
# /usr/lib/python2.7/functools.pyc matches /usr/lib/python2.7/functools.py
import functools # precompiled from /usr/lib/python2.7/functools.pyc
import _functools # builtin
import _ssl # builtin
import cStringIO # builtin
# trying /usr/lib/python2.7/dist-packages/ufw/util.so
# trying /usr/lib/python2.7/dist-packages/ufw/utilmodule.so
# trying /usr/lib/python2.7/dist-packages/ufw/util.py
# /usr/lib/python2.7/dist-packages/ufw/util.pyc matches /usr/lib/python2.7/dist-packages/ufw/util.py
import ufw.util # precompiled from /usr/lib/python2.7/dist-packages/ufw/util.pyc
# trying /usr/lib/python2.7/dist-packages/ufw/errno.so
# trying /usr/lib/python2.7/dist-packages/ufw/errnomodule.so
# trying /usr/lib/python2.7/dist-packages/ufw/errno.py
# trying /usr/lib/python2.7/dist-packages/ufw/errno.pyc
# trying /usr/lib/python2.7/dist-packages/ufw/fcntl.so
# trying /usr/lib/python2.7/dist-packages/ufw/fcntlmodule.so
# trying /usr/lib/python2.7/dist-packages/ufw/fcntl.py
# trying /usr/lib/python2.7/dist-packages/ufw/fcntl.pyc
import fcntl # builtin
# trying /usr/lib/python2.7/dist-packages/ufw/shutil.so
# trying /usr/lib/python2.7/dist-packages/ufw/shutilmodule.so
# trying /usr/lib/python2.7/dist-packages/ufw/shutil.py
# trying /usr/lib/python2.7/dist-packages/ufw/shutil.pyc
# trying /usr/sbin/shutil.so
# trying /usr/sbin/shutilmodule.so
# trying /usr/sbin/shutil.py
# trying /usr/sbin/shutil.pyc
# trying /usr/lib/python2.7/shutil.so
# trying /usr/lib/python2.7/shutilmodule.so
# trying /usr/lib/python2.7/shutil.py
# /usr/lib/python2.7/shutil.pyc matches /usr/lib/python2.7/shutil.py
import shutil # precompiled from /usr/lib/python2.7/shutil.pyc
# trying /usr/sbin/fnmatch.so
# trying /usr/sbin/fnmatchmodule.so
# trying /usr/sbin/fnmatch.py
# trying /usr/sbin/fnmatch.pyc
# trying /usr/lib/python2.7/fnmatch.so
# trying /usr/lib/python2.7/fnmatchmodule.so
# trying /usr/lib/python2.7/fnmatch.py
# /usr/lib/python2.7/fnmatch.pyc matches /usr/lib/python2.7/fnmatch.py
import fnmatch # precompiled from /usr/lib/python2.7/fnmatch.pyc
# trying /usr/sbin/collections.so
# trying /usr/sbin/collectionsmodule.so
# trying /usr/sbin/collections.py
# trying /usr/sbin/collections.pyc
# trying /usr/lib/python2.7/collections.so
# trying /usr/lib/python2.7/collectionsmodule.so
# trying /usr/lib/python2.7/collections.py
# /usr/lib/python2.7/collections.pyc matches /usr/lib/python2.7/collections.py
import collections # precompiled from /usr/lib/python2.7/collections.pyc
import _collections # builtin
import operator # builtin
# trying /usr/sbin/keyword.so
# trying /usr/sbin/keywordmodule.so
# trying /usr/sbin/keyword.py
# trying /usr/sbin/keyword.pyc
# trying /usr/lib/python2.7/keyword.so
# trying /usr/lib/python2.7/keywordmodule.so
# trying /usr/lib/python2.7/keyword.py
# /usr/lib/python2.7/keyword.pyc matches /usr/lib/python2.7/keyword.py
import keyword # precompiled from /usr/lib/python2.7/keyword.pyc
# trying /usr/sbin/heapq.so
# trying /usr/sbin/heapqmodule.so
# trying /usr/sbin/heapq.py
# trying /usr/sbin/heapq.pyc
# trying /usr/lib/python2.7/heapq.so
# trying /usr/lib/python2.7/heapqmodule.so
# trying /usr/lib/python2.7/heapq.py
# /usr/lib/python2.7/heapq.pyc matches /usr/lib/python2.7/heapq.py
import heapq # precompiled from /usr/lib/python2.7/heapq.pyc
import itertools # builtin
# trying /usr/sbin/bisect.so
# trying /usr/sbin/bisectmodule.so
# trying /usr/sbin/bisect.py
# trying /usr/sbin/bisect.pyc
# trying /usr/lib/python2.7/bisect.so
# trying /usr/lib/python2.7/bisectmodule.so
# trying /usr/lib/python2.7/bisect.py
# /usr/lib/python2.7/bisect.pyc matches /usr/lib/python2.7/bisect.py
import bisect # precompiled from /usr/lib/python2.7/bisect.pyc
import _bisect # builtin
# trying /usr/sbin/_heapq.so
# trying /usr/sbin/_heapqmodule.so
# trying /usr/sbin/_heapq.py
# trying /usr/sbin/_heapq.pyc
# trying /usr/lib/python2.7/_heapq.so
# trying /usr/lib/python2.7/_heapqmodule.so
# trying /usr/lib/python2.7/_heapq.py
# trying /usr/lib/python2.7/_heapq.pyc
# trying /usr/lib/python2.7/plat-linux2/_heapq.so
# trying /usr/lib/python2.7/plat-linux2/_heapqmodule.so
# trying /usr/lib/python2.7/plat-linux2/_heapq.py
# trying /usr/lib/python2.7/plat-linux2/_heapq.pyc
# trying /usr/lib/python2.7/lib-tk/_heapq.so
# trying /usr/lib/python2.7/lib-tk/_heapqmodule.so
# trying /usr/lib/python2.7/lib-tk/_heapq.py
# trying /usr/lib/python2.7/lib-tk/_heapq.pyc
# trying /usr/lib/python2.7/lib-dynload/_heapq.so
dlopen("/usr/lib/python2.7/lib-dynload/_heapq.so", 2);
import _heapq # dynamically loaded from /usr/lib/python2.7/lib-dynload/_heapq.so
import thread # builtin
import pwd # builtin
import grp # builtin
# trying /usr/lib/python2.7/dist-packages/ufw/struct.so
# trying /usr/lib/python2.7/dist-packages/ufw/structmodule.so
# trying /usr/lib/python2.7/dist-packages/ufw/struct.py
# trying /usr/lib/python2.7/dist-packages/ufw/struct.pyc
# trying /usr/sbin/struct.so
# trying /usr/sbin/structmodule.so
# trying /usr/sbin/struct.py
# trying /usr/sbin/struct.pyc
# trying /usr/lib/python2.7/struct.so
# trying /usr/lib/python2.7/structmodule.so
# trying /usr/lib/python2.7/struct.py
# /usr/lib/python2.7/struct.pyc matches /usr/lib/python2.7/struct.py
import struct # precompiled from /usr/lib/python2.7/struct.pyc
import _struct # builtin
# trying /usr/lib/python2.7/dist-packages/ufw/subprocess.so
# trying /usr/lib/python2.7/dist-packages/ufw/subprocessmodule.so
# trying /usr/lib/python2.7/dist-packages/ufw/subprocess.py
# trying /usr/lib/python2.7/dist-packages/ufw/subprocess.pyc
# trying /usr/sbin/subprocess.so
# trying /usr/sbin/subprocessmodule.so
# trying /usr/sbin/subprocess.py
# trying /usr/sbin/subprocess.pyc
# trying /usr/lib/python2.7/subprocess.so
# trying /usr/lib/python2.7/subprocessmodule.so
# trying /usr/lib/python2.7/subprocess.py
# /usr/lib/python2.7/subprocess.pyc matches /usr/lib/python2.7/subprocess.py
import subprocess # precompiled from /usr/lib/python2.7/subprocess.pyc
import gc # builtin
import time # builtin
import select # builtin
# trying /usr/sbin/pickle.so
# trying /usr/sbin/picklemodule.so
# trying /usr/sbin/pickle.py
# trying /usr/sbin/pickle.pyc
# trying /usr/lib/python2.7/pickle.so
# trying /usr/lib/python2.7/picklemodule.so
# trying /usr/lib/python2.7/pickle.py
# /usr/lib/python2.7/pickle.pyc matches /usr/lib/python2.7/pickle.py
import pickle # precompiled from /usr/lib/python2.7/pickle.pyc
import marshal # builtin
# trying /usr/sbin/org.so
# trying /usr/sbin/orgmodule.so
# trying /usr/sbin/org.py
# trying /usr/sbin/org.pyc
# trying /usr/lib/python2.7/org.so
# trying /usr/lib/python2.7/orgmodule.so
# trying /usr/lib/python2.7/org.py
# trying /usr/lib/python2.7/org.pyc
# trying /usr/lib/python2.7/plat-linux2/org.so
# trying /usr/lib/python2.7/plat-linux2/orgmodule.so
# trying /usr/lib/python2.7/plat-linux2/org.py
# trying /usr/lib/python2.7/plat-linux2/org.pyc
# trying /usr/lib/python2.7/lib-tk/org.so
# trying /usr/lib/python2.7/lib-tk/orgmodule.so
# trying /usr/lib/python2.7/lib-tk/org.py
# trying /usr/lib/python2.7/lib-tk/org.pyc
# trying /usr/lib/python2.7/lib-dynload/org.so
# trying /usr/lib/python2.7/lib-dynload/orgmodule.so
# trying /usr/lib/python2.7/lib-dynload/org.py
# trying /usr/lib/python2.7/lib-dynload/org.pyc
# trying /usr/local/lib/python2.7/dist-packages/org.so
# trying /usr/local/lib/python2.7/dist-packages/orgmodule.so
# trying /usr/local/lib/python2.7/dist-packages/org.py
# trying /usr/local/lib/python2.7/dist-packages/org.pyc
# trying /usr/lib/python2.7/dist-packages/org.so
# trying /usr/lib/python2.7/dist-packages/orgmodule.so
# trying /usr/lib/python2.7/dist-packages/org.py
# trying /usr/lib/python2.7/dist-packages/org.pyc
import binascii # builtin
# trying /usr/lib/python2.7/dist-packages/ufw/tempfile.so
# trying /usr/lib/python2.7/dist-packages/ufw/tempfilemodule.so
# trying /usr/lib/python2.7/dist-packages/ufw/tempfile.py
# trying /usr/lib/python2.7/dist-packages/ufw/tempfile.pyc
# trying /usr/sbin/tempfile.so
# trying /usr/sbin/tempfilemodule.so
# trying /usr/sbin/tempfile.py
# trying /usr/sbin/tempfile.pyc
# trying /usr/lib/python2.7/tempfile.so
# trying /usr/lib/python2.7/tempfilemodule.so
# trying /usr/lib/python2.7/tempfile.py
# /usr/lib/python2.7/tempfile.pyc matches /usr/lib/python2.7/tempfile.py
import tempfile # precompiled from /usr/lib/python2.7/tempfile.pyc
# trying /usr/sbin/random.so
# trying /usr/sbin/randommodule.so
# trying /usr/sbin/random.py
# trying /usr/sbin/random.pyc
# trying /usr/lib/python2.7/random.so
# trying /usr/lib/python2.7/randommodule.so
# trying /usr/lib/python2.7/random.py
# /usr/lib/python2.7/random.pyc matches /usr/lib/python2.7/random.py
import random # precompiled from /usr/lib/python2.7/random.pyc
# trying /usr/sbin/__future__.so
# trying /usr/sbin/__future__module.so
# trying /usr/sbin/__future__.py
# trying /usr/sbin/__future__.pyc
# trying /usr/lib/python2.7/__future__.so
# trying /usr/lib/python2.7/__future__module.so
# trying /usr/lib/python2.7/__future__.py
# /usr/lib/python2.7/__future__.pyc matches /usr/lib/python2.7/__future__.py
import __future__ # precompiled from /usr/lib/python2.7/__future__.pyc
import math # builtin
# trying /usr/sbin/hashlib.so
# trying /usr/sbin/hashlibmodule.so
# trying /usr/sbin/hashlib.py
# trying /usr/sbin/hashlib.pyc
# trying /usr/lib/python2.7/hashlib.so
# trying /usr/lib/python2.7/hashlibmodule.so
# trying /usr/lib/python2.7/hashlib.py
# /usr/lib/python2.7/hashlib.pyc matches /usr/lib/python2.7/hashlib.py
import hashlib # precompiled from /usr/lib/python2.7/hashlib.pyc
import _hashlib # builtin



```

---

### Post by alexander.suter.ch on 2013-11-07
Some other ideas? I really need a firewall!!!

Reinstall python? Install an other version ufw? Install an other version of python? What can I do?

---

### Post by alexander.suter.ch on 2013-11-07
in kernel.log i found something:

Nov  7 08:59:17 rohkost kernel: [1217167.627499] ufw[10350] trap invalid opcode ip:XXXXXXXXX sp:XXXXXXXXXX error:0 in libm-2.15.so[7f2460cf0000+f9000]


I REPLACED THE IP AND SP WITH XXXXXXXXXXXXX

What is the invalid opcode? in libm?

---

### Post by prshah on 2013-11-07
This is a known bug on some AMD architectures. Please make sure your precise is updated, else see [https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/956051](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/956051) for fixes/workarounds.

---

### Post by alexander.suter.ch on 2013-11-07
YEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEES! Thanks -> apt-get upgrade!!

Thank you very much!

---

