---
title: "How to force an app update"
date: 2013-08-20
forum: Server Platforms
---

### Post by vcbranco on 2013-08-20
Hi all,

In Ubuntu desktop I can force the update of an aplication from the backport repository with synaptic

How can I do the same thing in Ubuntu server?

Many thanks in advance

---

### Post by cartaysm on 2013-08-21
I could be wrong but wouldn't a simple -f on the command work?

apt-get -f install

---

### Post by zealibib slaughter on 2013-08-21
apt-get -f install fixes broken packages

you need to add the backports repositories manually by editing /etc/apt/sources.list and adding 
```
deb http://archive.ubuntu.com/ubuntu *yourreleasecodename*-backports main restricted universe multiverse
```

use apt-get *packagename*/[I]releasename-backports

[/I]so on a system with ubuntu 13.04 while installing the guake backport for example you would type sudo nano /etc/apt/sources.list

add a line that reads
```
 deb http://archive.ubuntu.com/ubuntu *raring*-backports main restricted universe multiverse
```
update the repos 
```
sudo apt-get update
```
then  install the backport of guake
```
 sudo apt-get install guake/raring-backports
```

---

### Post by vcbranco on 2013-08-21
This worked

> **zealibib slaughter said:**
> 
```
 sudo apt-get install guake/raring-backports
```

In my case

```
 sudo apt-get install boinc-client/precise-backports
```

Thanks for your support

---

