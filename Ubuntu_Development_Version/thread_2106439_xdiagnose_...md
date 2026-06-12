---
title: "xdiagnose .."
date: 2013-01-19
forum: Ubuntu Development Version
---

### Post by zika on 2013-01-19
```
Resolving dependencies...                
The following partially installed packages will be configured:
  xdiagnose 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up xdiagnose (3.4) ...           
SyntaxError: ('invalid syntax', ('/usr/lib/python2.7/dist-packages/xdiagnose/welcome.py', 219, 32, '                 "--height=480")\n'))

dpkg: error processing xdiagnose (--configure):
 subprocess installed post-installation script returned error exit status 101
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 xdiagnose
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up xdiagnose (3.4) ...
SyntaxError: ('invalid syntax', ('/usr/lib/python2.7/dist-packages/xdiagnose/welcome.py', 219, 32, '                 "--height=480")\n'))

dpkg: error processing xdiagnose (--configure):
 subprocess installed post-installation script returned error exit status 101
Errors were encountered while processing:
 xdiagnose
```

---

### Post by anca-emanuel on 2013-01-19
[https://bugs.launchpad.net/ubuntu/+source/xdiagnose/+bug/1101678](https://bugs.launchpad.net/ubuntu/+source/xdiagnose/+bug/1101678)

---

### Post by jppr on 2013-01-19
Just upgrades new version...

[https://lists.ubuntu.com/archives/raring-changes/2013-January/004567.html](https://lists.ubuntu.com/archives/raring-changes/2013-January/004567.html)

---

