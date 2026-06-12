---
title: "server updating and dependency issues abound."
date: 2013-04-19
forum: Server Platforms
---

### Post by thunder63cs on 2013-04-19
I am updating my server and it is telling me that "linux-server depends on linux-image-server (= 3.2.0.38.46); however: version of  linux-image-server on system is 3.2.0.40.48. "

I have tried apt-get -f install and still get the error.  plus when I go to update everything else it won't due to linux-server not updating correctly.  
any advice as how to correct this would be welcome please. 

log:

 ```
sudo apt-get -f install
[sudo] password for praetorian:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-37 linux-headers-3.2.0-37-generic libudev0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-server
The following packages will be upgraded:
  linux-server
1 upgraded, 0 newly installed, 0 to remove and 135 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,732 B of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.38.46); however:
  Version of linux-image-server on system is 3.2.0.40.48.
 linux-server depends on linux-headers-server (= 3.2.0.38.46); however:
  Version of linux-headers-server on system is 3.2.0.40.48.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
praetorian@praetorian:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
praetorian@praetorian:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-server : Depends: linux-image-server (= 3.2.0.38.46) but 3.2.0.40.48 is installed
                Depends: linux-headers-server (= 3.2.0.38.46) but 3.2.0.40.48 is installed
E: Unmet dependencies. Try using -f.
praetorian@praetorian:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-37 linux-headers-3.2.0-37-generic libudev0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-server
The following packages will be upgraded:
  linux-server
1 upgraded, 0 newly installed, 0 to remove and 135 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,732 B of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.38.46); however:
  Version of linux-image-server on system is 3.2.0.40.48.
 linux-server depends on linux-headers-server (= 3.2.0.38.46); however:
  Version of linux-headers-server on system is 3.2.0.40.48.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
praetorian@praetorian:~$
```

---

### Post by tgalati4 on 2013-04-19
linux-server is a meta-package.  Post your dependency chain:

tgalati4@Mint14-Extensa ~ $ apt-cache depends linux-server
linux-server
  Depends: linux-generic
  Conflicts: linux-server:i386
tgalati4@Mint14-Extensa ~ $ apt-cache depends linux-generic
linux-generic
  Depends: linux-image-generic
  Depends: linux-headers-generic
  Conflicts: linux-generic:i386
tgalati4@Mint14-Extensa ~ $ apt-cache depends linux-image-generic
linux-image-generic
  Depends: linux-image-3.5.0-27-generic
  Depends: linux-image-extra-3.5.0-27-generic
  Depends: linux-firmware
  Conflicts: linux-image-generic:i386

---

### Post by thunder63cs on 2013-04-19
I was finally able to get every thing else to update but Linux-server.  In the op I pasted the error I was getting which pretty much was it depends on an older version of Linux-image-server and Linux-headers-generic then what is installed.

I did a apt-get safe-upgrade and was able to upgrade everything but linux-server

I have tried to do apt-get install linux-headers-server and apt-get install linux-image-server and all i get it is at the newest version.  have tried it both with and with out 3.2.0-38 behind them and still no luck.

```
linux-server
  Depends: linux-image-server
  Depends: linux-headers-server
  Conflicts: linux-server:i386
praetorian@praetorian:~$ apt-cache depends linux-image-generic
linux-image-generic
  Depends: linux-image-3.2.0-40-generic
  Depends: linux-firmware
  Conflicts: linux-image-generic:i386
```

---

### Post by thunder63cs on 2013-04-23
so any extra help would be great

---

### Post by CharlesA on 2013-04-24
Try this:

[http://ubuntuforums.org/showthread.php?t=2138427&p=12616420&viewfull=1#post12616420](http://ubuntuforums.org/showthread.php?t=2138427&p=12616420&viewfull=1#post12616420)

---

### Post by thunder63cs on 2013-04-25
Thanks that seemed to have done it by using:
```
 sudo dpkg --remove linux-server

sudo apt-get install linux-server
```

thanks for the help CharlesA

---

