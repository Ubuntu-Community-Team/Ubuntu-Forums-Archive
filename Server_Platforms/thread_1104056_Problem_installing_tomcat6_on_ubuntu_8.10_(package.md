---
title: "Problem installing tomcat6 on ubuntu 8.10 (package corrupted?)"
date: 2009-03-23
forum: Server Platforms
---

### Post by tamiii on 2009-03-23
Hi folks,

Instead of big speech, here is my problem:

```

root@ubuntu:/# apt-get install tomcat6 tomcat6-user tomcat6-docs tomcat6-admin tomcat6-examples
Reading package lists... Done
Building dependency tree
Reading state information... Done
tomcat6-user is already the newest version.
The following extra packages will be installed:
  jsvc libcommons-daemon-java
The following NEW packages will be installed
  jsvc libcommons-daemon-java tomcat6 tomcat6-admin tomcat6-docs tomcat6-examples
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1256kB of archives.
After this operation, 7623kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libcommons-daemon-java.
(Reading database ... 46890 files and directories currently installed.)
Unpacking libcommons-daemon-java (from .../libcommons-daemon-java_1.0.2~svn20061127-9ubuntu2_all.deb) ...
Selecting previously deselected package jsvc.
Unpacking jsvc (from .../jsvc_1.0.2~svn20061127-9ubuntu2_i386.deb) ...
Selecting previously deselected package tomcat6.
Unpacking tomcat6 (from .../tomcat6_6.0.18-0ubuntu3.1_all.deb) ...
Selecting previously deselected package tomcat6-admin.
Unpacking tomcat6-admin (from .../tomcat6-admin_6.0.18-0ubuntu3.1_all.deb) ...
Selecting previously deselected package tomcat6-docs.
Unpacking tomcat6-docs (from .../tomcat6-docs_6.0.18-0ubuntu3.1_all.deb) ...
Selecting previously deselected package tomcat6-examples.
Unpacking tomcat6-examples (from .../tomcat6-examples_6.0.18-0ubuntu3.1_all.deb) ...
Processing triggers for man-db ...
Setting up libcommons-daemon-java (1.0.2~svn20061127-9ubuntu2) ...

Setting up jsvc (1.0.2~svn20061127-9ubuntu2) ...
Setting up tomcat6 (6.0.18-0ubuntu3.1) ...
chgrp: cannot access `/etc/tomcat6/tomcat-users.xml': No such file or directory
dpkg: error processing tomcat6 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of tomcat6-admin:
 tomcat6-admin depends on tomcat6 (>= 6.0.18-0ubuntu3.1); however:
  Package tomcat6 is not configured yet.
dpkg: error processing tomcat6-admin (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of tomcat6-docs:
 tomcat6-docs depends on tomcat6 (>= 6.0.18-0ubuntu3.1); however:
  Package tomcat6 is not configured yet.
dpkg: error processing tomcat6-docs (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of tomcat6-examples:
 tomcat6-examples depends on tomcat6 (>= 6.0.18-0ubuntu3.1); however:
  Package tomcat6 is not configured yet.
dpkg: error processing tomcat6-examples (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 tomcat6
 tomcat6-admin
 tomcat6-docs
 tomcat6-examples
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas ? :(

Thanks and have a nice day!

---

### Post by primaxx on 2009-03-23
I think there is a bug with the TomCat in the repositories. The workaround I think can be found here:
[http://ubuntuforums.org/showthread.php?t=977276](http://ubuntuforums.org/showthread.php?t=977276)

Good luck! :-)

---

