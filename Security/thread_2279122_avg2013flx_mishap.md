---
title: "avg2013flx mishap"
date: 2015-05-21
forum: Security
---

### Post by trailblder on 2015-05-21
Hello everyone, new user/new poster.  I haven't seen too many people post about AVG, and I seem to have horked mine up during install such that I can't uninstall/reinstall it, whether using apt or dpkg.  The avgd recovers out of /etc/init.d/, and according to sudo sysv-rc-conf, the service is there and enabled....Thanks for your time!!


REMOVAL ATTEMPT:```

:~$ sudo dpkg-query -l '*avg*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                  Version                 Architecture            Description
+++-=====================================-=======================-=======================-===============================================================================
ii  avg2013flx                            2013.3118               all                     AVG Anti-Virus for Linux/FreeBSD
un  avg71                                 <none>                  <none>                  (no description available)
un  avg75                                 <none>                  <none>                  (no description available)
un  avg85                                 <none>                  <none>                  (no description available)

:~$ sudo dpkg -r avg2013flx
(Reading database ... 257652 files and directories currently installed.)
Removing avg2013flx (2013.3118) ...
Failed to stop avgd.service: Unit avgd.service not loaded.
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: error processing package avg2013flx (--remove):
 subprocess installed pre-removal script returned error exit status 5
Errors were encountered while processing:
 avg2013flx
:~$ sudo apt-get purge avg2013flx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gambas3-gb-desktop:i386 gambas3-gb-desktop-x11:i386 gambas3-gb-image:i386
  gambas3-gb-qt4:i386 gambas3-runtime:i386 libqt4-svg:i386 libxtst6:i386
  python-configobj
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  avg2013flx*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 176 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 257652 files and directories currently installed.)
Removing avg2013flx (2013.3118) ...
Failed to stop avgd.service: Unit avgd.service not loaded.
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: error processing package avg2013flx (--purge):
 subprocess installed pre-removal script returned error exit status 5
Errors were encountered while processing:
 avg2013flx
E: Sub-process /usr/bin/dpkg returned an error code (1)
:~$ sudo apt-get autoremove avg2013flx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  avg2013flx gambas3-gb-desktop:i386 gambas3-gb-desktop-x11:i386
  gambas3-gb-image:i386 gambas3-gb-qt4:i386 gambas3-runtime:i386
  libqt4-svg:i386 libxtst6:i386 python-configobj
0 upgraded, 0 newly installed, 9 to remove and 0 not upgraded.
After this operation, 179 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 257652 files and directories currently installed.)
Removing avg2013flx (2013.3118) ...
Failed to stop avgd.service: Unit avgd.service not loaded.
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: error processing package avg2013flx (--remove):
 subprocess installed pre-removal script returned error exit status 5
Removing gambas3-gb-qt4 (3.7.1-1.34~ubuntu15.04.1) ...
Removing libqt4-svg:i386 (4:4.8.6+git64-g5dc8b2b+dfsg-3~ubuntu6) ...
Removing python-configobj (5.0.6-1) ...
Removing gambas3-gb-desktop (3.7.1-1.34~ubuntu15.04.1) ...
Removing gambas3-gb-desktop-x11 (3.7.1-1.34~ubuntu15.04.1) ...
Removing gambas3-gb-image (3.7.1-1.34~ubuntu15.04.1) ...
Removing gambas3-runtime (3.7.1-1.34~ubuntu15.04.1) ...
Removing libxtst6:i386 (2:1.2.2-1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Processing triggers for hicolor-icon-theme (0.14-0ubuntu1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for shared-mime-info (1.3-1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Errors were encountered while processing:
 avg2013flx
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
REINSTALL ATTEMPT:```

:~$ sudo gdebi avg2013flx-r3118-a6926.i386.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Building data structures... Done 

AVG Anti-Virus for Linux/FreeBSD
Do you want to install the software package? [y/N]:y
(Reading database ... 257653 files and directories currently installed.)
Preparing to unpack avg2013flx-r3118-a6926.i386.deb ...
Failed to stop avgd.service: Unit avgd.service not loaded.     (according to sudo sysv-rc-conf, this was enabled)
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 5
dpkg: trying script from the new package instead ...
Failed to stop avgd.service: Unit avgd.service not loaded.
invoke-rc.d: initscript avgd, action "stop" failed.
dpkg: error processing archive avg2013flx-r3118-a6926.i386.deb (--install):
 subprocess new pre-removal script returned error exit status 5
Errors were encountered while processing:
 avg2013flx-r3118-a6926.i386.deb
:~$ sudo /etc/init.d/./avgd start
 * Starting avgd ... (recovering)                                                                                                                                     [ ok ]
```

---

### Post by gamergotmail on 2015-05-27
I am having the exact same error as you are . I can't seem to find a way to fix it except for one forum is edit the pre-removal script. Which i am going try now . I am using Ubuntu 15.04 .

---

### Post by tospig2 on 2015-05-30
Exact same issue here, any joy with it?

---

