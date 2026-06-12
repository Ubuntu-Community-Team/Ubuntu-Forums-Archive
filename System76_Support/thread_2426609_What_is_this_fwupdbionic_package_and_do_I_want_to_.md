---
title: "What is this fwupd/bionic package and do I want to upgrade it?"
date: 2019-09-11
forum: System76 Support
---

### Post by psylem on 2019-09-11
I'm assuming it's a firmware update? For some reason I'm only notified of the available updates when I run apt, which is new to me. This is on my 2014 model Bonobo Extreme, any advice?...

```
root@bonobo:~# apt update
Hit:1 http://archive.canonical.com/ubuntu bionic InRelease
Ign:2 https://packages.atlassian.com/debian/atlassian-sdk-deb stable InRelease
Hit:3 https://packages.atlassian.com/debian/atlassian-sdk-deb stable Release
Ign:5 http://dl.google.com/linux/chrome/deb stable InRelease                                 
Hit:6 http://ppa.launchpad.net/system76-dev/stable/ubuntu bionic InRelease                   
Ign:7 http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/Ubuntu_18.04  InRelease
Hit:8 http://au.archive.ubuntu.com/ubuntu bionic InRelease                                   
Hit:9 http://au.archive.ubuntu.com/ubuntu bionic-updates InRelease                           
Hit:10 http://dl.google.com/linux/chrome/deb stable Release                                  
Hit:11 http://au.archive.ubuntu.com/ubuntu bionic-backports InRelease                        
Ign:12 http://repo.vivaldi.com/stable/deb stable InRelease                                   
Hit:13 http://au.archive.ubuntu.com/ubuntu bionic-security InRelease     
Hit:14 http://repo.vivaldi.com/stable/deb stable Release                 
Hit:16 http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/Ubuntu_18.04  Release
Reading package lists... Done                       
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
root@bonobo:~# apt list --upgradable
Listing... Done
fwupd/bionic 1.2.9-1pop1~1565908160~18.04~fab1c8a~dev amd64 [upgradable from: 1.0.9-0ubuntu2]
N: There are 2 additional versions. Please use the '-a' switch to see them.
root@bonobo:~# apt -a list --upgradable
Listing... Done
fwupd/bionic 1.2.9-1pop1~1565908160~18.04~fab1c8a~dev amd64 [upgradable from: 1.0.9-0ubuntu2]
fwupd/bionic-updates,now 1.0.9-0ubuntu2 amd64 [installed,upgradable to: 1.2.9-1pop1~1565908160~18.04~fab1c8a~dev]
fwupd/bionic 1.0.6-2 amd64

```

---

