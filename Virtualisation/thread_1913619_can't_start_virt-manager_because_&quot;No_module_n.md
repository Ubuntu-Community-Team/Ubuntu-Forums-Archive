---
title: "can't start virt-manager because &quot;No module named libvirt&quot;"
date: 2012-01-22
forum: Virtualisation
---

### Post by srkherad on 2012-01-22
I'm trying to start virt-manager but apparently libvirt is not installed and i can't seem to install it.  here are some snippets of what i have tried: 

```
arclight@hive-test1:~$ virt-manager
Traceback (most recent call last):
  File "/usr/share/virt-manager/virt-manager.py", line 26, in <module>
    import libvirt
ImportError: No module named libvirt
```

Below you will see that libvirt is not found while others are such as python-libvirt libvirt-dev and virt-manager
```
arclight@hive-test1:~$ sudo dpkg -l libvirt
No packages found matching libvirt.

arclight@hive-test1:~$ sudo dpkg -l virt-manager
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                Version             Description
+++-===================-===================-======================================================
ii  virt-manager        0.8.4-7ubuntu1.1    desktop application for managing virtual machines

arclight@hive-test1:~$ sudo dpkg -l python-libvirt
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                Version             Description
+++-===================-===================-======================================================
ii  python-libvirt      0.8.3-1ubuntu19.4   libvirt Python bindings

arclight@hive-test1:~$ sudo dpkg -l libvirt-dev
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                Version             Description
+++-===================-===================-======================================================
ii  libvirt-dev         0.8.3-1ubuntu19.4   development files for the libvirt library
```

When I try to install libvirt I get:
```
arclight@hive-test1:~$ sudo apt-get install libvirt
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libvirt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libvirt' has no installation candidate
```

I'm not really sure what to try here?

any help is greatly appreciated.  thanks

---

