---
title: "Clustering installation"
date: 2008-06-20
forum: Server Platforms
---

### Post by aikiko on 2008-06-20
Hello,

I am trying to make a Cluster out of 3 PC on ubuntu server 8.04
I have a fresh install on all the 3 PC, I install some new packages to have the dependencies of Kerrighed ( the clustering software ). When running ./configure I got some errors : 

[http://pastebin.com/m76393ac7](http://pastebin.com/m76393ac7)

Here are the things I installed on the server : 

```
#!/bin/bash  
apt-get update
apt-get dist-upgrade -y

apt-get install mc -y
apt-get install lynx -y
apt-get install openssh-server -y
/etc/init.d/ssh start

apt-get install make -y
apt-get install automake -y
apt-get install autoconf -y
apt-get install gcc -y
apt-get install lsb_release -y
apt-get install xmlto -y
apt-get install patchutils -y
apt-get install xutils-dev -y
apt-get install gawk -y
```

Any help would be greatly appreciated.

---

### Post by deadwait on 2008-07-05
hi which version of kerrighed are you using , i tried it too, though i was able to compile everything properly, i am using kerrighed 2.3.0. but  i am still not able to get the cluster up

---

### Post by ajt on 2009-01-12
Hello,

I've started a new discussion, to try and bring together threads in different forums about Ubuntu clustering at:

[http://ubuntuforums.org/showthread.php?p=6495259]("http://ubuntuforums.org/showthread.php?p=6495259")

    Tony.

---

### Post by robasc on 2009-03-10
Hello everyone I noticed there is a lot of discussion here about building a Beowulf cluster. 

I am wanting to build a cluster really bad but I am not that good in Linux yet. Looking for some help and learning material.

I have got plenty of goodies here to build a cluster. Any one care to help?

---

### Post by ajt on 2009-03-10
> **robasc said:**
> Hello everyone I noticed there is a lot of discussion here about building a Beowulf cluster. 

I am wanting to build a cluster really bad but I am not that good in Linux yet. Looking for some help and learning material.

I have got plenty of goodies here to build a cluster. Any one care to help?

Hello, robasc.

The last post in this thread, apart from mine, was over a year ago!

I've tried to bring together fragmented discussions about clustering Ubuntu in different places on the forums into a new discussion:
[http://ubuntuforums.org/showthread.php?p=6495259]("http://ubuntuforums.org/showthread.php?p=6495259")

Bye,

    Tony.

---

