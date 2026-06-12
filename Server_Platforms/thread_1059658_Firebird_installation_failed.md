---
title: "Firebird installation failed"
date: 2009-02-04
forum: Server Platforms
---

### Post by thesilverline on 2009-02-04
I have Intrepid Ibex installed. I'm trying to install firebird 2.1 on it but I get this error:
```

The following NEW packages will be installed:
  firebird2.1-common firebird2.1-server-common firebird2.1-super libfbclient2
0 upgraded, 4 newly installed, 0 to remove and 235 not upgraded.
Need to get 0B/5820kB of archives.
After this operation, 14.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package firebird2.1-common.
(Reading database ... 116358 files and directories currently installed.)
Unpacking firebird2.1-common (from .../firebird2.1-common_2.1.0.17798-0.ds2-1_i386.deb) ...
Selecting previously deselected package firebird2.1-server-common.
Unpacking firebird2.1-server-common (from .../firebird2.1-server-common_2.1.0.17798-0.ds2-1_i386.deb) ...
Selecting previously deselected package libfbclient2.
Unpacking libfbclient2 (from .../libfbclient2_2.1.0.17798-0.ds2-1_i386.deb) ...
Selecting previously deselected package firebird2.1-super.
Unpacking firebird2.1-super (from .../firebird2.1-super_2.1.0.17798-0.ds2-1_i386.deb) ...
Processing triggers for man-db ...
Setting up firebird2.1-common (2.1.0.17798-0.ds2-1) ...
Setting up firebird2.1-server-common (2.1.0.17798-0.ds2-1) ...
dpkg: error processing firebird2.1-server-common (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libfbclient2 (2.1.0.17798-0.ds2-1) ...

dpkg: dependency problems prevent configuration of firebird2.1-super:
 firebird2.1-super depends on firebird2.1-server-common (= 2.1.0.17798-0.ds2-1); however:
  Package firebird2.1-server-common is not configured yet.
dpkg: error processing firebird2.1-super (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          ldconfig deferred processing now taking place
Errors were encountered while processing:
 firebird2.1-server-common
 firebird2.1-super
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any suggestions to install fb successfully?

---

### Post by mariuz on 2009-03-05
Is fixed in 2.1.1 in debian please use this ppa like is explained in tutorial

[https://help.ubuntu.com/community/Firebird2.1](https://help.ubuntu.com/community/Firebird2.1)

I will try do an SRU process when i have time

---

