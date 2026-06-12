---
title: "Installing xvfb - E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2016-02-11
forum: Server Platforms
---

### Post by toni12 on 2016-02-11
When I try to install xvfb, I get this error: E: Sub-process /usr/bin/dpkg returned an error code (1)

I googled for solution but no luck, maybe someone here can help me.

Best Regards

```

root@TheBasix:~# apt-get install xvfb
Reading package lists... Done
Building dependency tree
Reading state information... Done
xvfb is already the newest version.
Suggested packages:
  python-apt-dbg python-gtk2 python-vte python-apt-doc
The following packages will be upgraded:
  python-apt
1 upgraded, 0 newly installed, 0 to remove and 74 not upgraded.
107 not fully installed or removed.
Need to get 0 B/141 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 155208 files and directories currently installed.)
Preparing to unpack .../python-apt_0.9.3.5ubuntu2_amd64.deb ...
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
dpkg: error processing archive /var/cache/apt/archives/python-apt_0.9.3.5ubuntu2                        _amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-apt_0.9.3.5ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by v3.xx on 2016-02-11
Try cleaning the cache

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

Then update you sources after.

---

### Post by steeldriver on 2016-02-11
It looks to me like it might be a python2/python3 syntax issue: have you messed with the default version of python?

---

