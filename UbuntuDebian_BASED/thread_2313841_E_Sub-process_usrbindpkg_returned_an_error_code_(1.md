---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2016-02-16
forum: Ubuntu/Debian BASED
---

### Post by nescafe1216 on 2016-02-16
[B]Im using ubuntu 15.10
and im getting an error[/B]

sudo apt-get update && sudo apt-get upgrade
[sudo] password for user-a: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily InRelease
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) wily/universe Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up update-notifier-common (3.163) ...
/var/lib/dpkg/info/update-notifier-common.postinst: 25: /var/lib/dpkg/info/update-notifier-common.postinst: /usr/lib/update-notifier/package-data-downloader: not found
dpkg: error processing package update-notifier-common (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-notifier-common (= 3.163); however:
  Package update-notifier-common is not configured yet.

dpkg: error processing package update-notifier (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 update-notifier-common
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)

**using synaptic or software center causes same error**

---

### Post by ian-weisser on 2016-02-16
Try:
```
sudo apt-get clean update-notifier update-notifier-common
sudo apt-get install --reinstall update-notifier update-notifier-common
```

---

### Post by nescafe1216 on 2016-02-18
got fixed with 
sudo mv /var/lib/dpkg/info/update-notifier-common.postinst{,.bak}
ty for help anyway

---

