---
title: "Update Issue 13.04"
date: 2013-04-20
forum: Ubuntu Development Version
---

### Post by TheMixtureMedia on 2013-04-20
Hi there when I try to upgrade I get this issue

dpkg: warning: files list file for package 'linux-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'media-player-info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-3.8.0-19-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libyelp0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmono-system-componentmodel-composition4.0-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mono-gac' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gtk2-engines-murrine:i386' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 files list file for package `libdaemon0' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

I am running Ubuntu 13.04 32 bit and I am not sure why I have this is happening or how to fix it.

---

### Post by grahammechanical on 2013-04-20
Here are some commands to try

```
sudo dpkg --configure -a
``````
sudo apt-get -f install
``````
sudo rm /var/lib/apt/lists/* -rf
```

That last command removes/deletes the file/scripts in the lists directory. These lists are use to compare with similar lists in repositories. In this way Update Manager knows which packages can be updated.

To replace the scripts run```
sudo apt-get update
```

See if any of those commands fixes things. Another suggestion comes to mind. Use Synaptic Package Manager (not installed by default) to track down each of those packages or libraries and install or re-install if necessary.

Regards.

---

### Post by TheMixtureMedia on 2013-04-20
Hi there I tried to install Synaptic Package Manager and it gives me this error

installArchives() failed: Selecting previously unselected package sgml-data.
(Reading database ... 
dpkg: warning: files list file for package 'linux-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'media-player-info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-headers-3.8.0-19-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libyelp0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmono-system-componentmodel-composition4.0-cil' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mono-gac' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gtk2-engines-murrine:i386' missing; assuming package has no files currently installed
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
dpkg: unrecoverable fatal error, aborting:
 files list file for package `libdaemon0' contains empty filename


I also tried the commands that you told me to try and it did not work either

---

### Post by cariboo on 2013-04-20
Have you tried using a different mirror? Go to System Settings->Software & Updates and select a different server in Download from:

---

### Post by TheMixtureMedia on 2013-04-20
Yes I have and just tried again and still having issues. I also under Other Software have everything unchecked.

---

### Post by TheMixtureMedia on 2013-04-20
[http://askubuntu.com/questions/195950/package-system-broken-e-sub-process-usr-bin-dpkg-returned-an-error-code-1](http://askubuntu.com/questions/195950/package-system-broken-e-sub-process-usr-bin-dpkg-returned-an-error-code-1) helped me fix this issue.

---

