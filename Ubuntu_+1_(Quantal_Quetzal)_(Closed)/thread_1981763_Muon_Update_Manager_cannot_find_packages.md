---
title: "Muon Update Manager cannot find packages"
date: 2012-05-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mparillo on 2012-05-17
I have tried twice:
 1. A clean install of today's (2012-05-17) Daily Kubuntu desktop-i386 Build
 2. A formerly up-to-date version of the 2012-05-11 Daily Kubuntu desktop-i386 Build

In both cases, I get the notification that updates are available. I click on the notification, and the Muon Update Manager comes up listing the packages to be updated, I click the checkbox to Install Updates and I get:

The package system could not be initialized, your configuration may be broken.

Any ideas?

---

### Post by dino99 on 2012-05-17
Never used it since it badly wiped my install some time ago, now im pleased with synaptic

---

### Post by Rog131 on 2012-05-18
Developers comment kubuntu-devel ( [http://irclogs.ubuntu.com/2012/05/17/%23kubuntu-devel.html](http://irclogs.ubuntu.com/2012/05/17/%23kubuntu-devel.html) ) :

> Basically, muon is broke in quantal. Can't do commits or update checks)

Blog:
- [http://jontheechidna.wordpress.com/](http://jontheechidna.wordpress.com/)

The ususal pre-release caveats and tips ( [http://www.kubuntuforums.net/showthread.php?58444-The-ususal-pre-release-caveats-and-tips](http://www.kubuntuforums.net/showthread.php?58444-The-ususal-pre-release-caveats-and-tips) ) :
> I recommend using the command line for updating and upgrading, especially in the alpha stage, and pretty much up to the rc stage. 

---

### Post by mparillo on 2012-05-21
My [bug report]("https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/1000939") is a duplicate of [this]("https://bugs.launchpad.net/ubuntu/+source/gcc-4.7/+bug/1000508").
**[B][SIZE=2]PendingMessages member variable of APT's GlobalError class initializes as "true" with -std=c++11[/SIZE]**
[/B]

---

### Post by mparillo on 2012-05-21
The command line was not completely successful for me either.

mparillo@ubuntu:~$ sudo apt-get update
...
E: Some index files failed to download. They have been ignored, or old ones used instead.

mparillo@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

---

### Post by arpanaut on 2012-05-21
> E: Some index files failed to download. They have been ignored, or old ones used instead.It would be good to know which indexes have failed to download. That would be just above this error message.

To get new packages especially kernels, often it is necesary to run:
```
sudo apt-get dist-upgrade
```Pay attention to the results of the command if it says things are going to be removed, "Just say NO". Then investigate what and why this is happening.

First it would be good to know why you are getting index errors. 
Something funky in your sources.list?

---

### Post by mparillo on 2012-05-22
Thank you arpanaut
sudo apt-get update
sudo apt-get dist-upgrade
did the trick.

No updates are pending.

---

