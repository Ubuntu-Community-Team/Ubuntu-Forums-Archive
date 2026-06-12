---
title: "insert dvd to install ssh"
date: 2013-12-20
forum: Server Platforms
---

### Post by sniper8752 on 2013-12-20
I am trying to install openssh-server on ubuntu server, and it told me to insert the dvd for the os.  how do i configure it so that it installs from the online repository instead of requiring the cd?  and I only have the cli.

---

### Post by tfrue on 2013-12-20
Did you do ```
sudo apt-get install openssh-sever
```

---

### Post by volkswagner on 2013-12-20
> **sniper8752 said:**
> I am trying to install openssh-server on ubuntu server, and it told me to insert the dvd for the os.  how do i configure it so that it installs from the online repository instead of requiring the cd?  and I only have the cli.


You need to comment out the cd reference in /etc/apt/sources.list

```
sudo nano /etc/apt/sources.list
```

Then put a # in front of the cd source like:

```
# deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release i386 (20100427)]/ lucid main restricted


```


Then run:

```
sudo apt-get update
```

---

### Post by sniper8752 on 2013-12-20
> **volkswagner said:**
> You need to comment out the cd reference in /etc/apt/sources.list

```
sudo nano /etc/apt/sources.list
```

Then put a # in front of the cd source like:

```
# deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release i386 (20100427)]/ lucid main restricted


```


Then run:

```
sudo apt-get update
```

Worked - thanks!

---

### Post by volkswagner on 2013-12-20
Glad it worked.

You can mark your thread solved using "thread tools" drop down menu.

---

### Post by sniper8752 on 2013-12-20
I do have something related - I noticed iptables is not installed.  When I attempt to install it, it tells me that it is unable to locate the package.

Edit: I just checked sources.list, and there was only that cdrom option.  how do I get the necessary ubuntu repositories?
I added the following:
```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta i386 (20120421)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

But this would include the desktop as well, right?  How would I only get the things I need for a server, and limit as to what gets installed?  Is there a repository specifically for servers?

---

### Post by cariboo on 2013-12-22
The packages for all the versions are in the same repositories, there aren't seperate ones for the different versions. When running updates, only the packages you have installed will update, and if you need a specific package you need to use apt-get to install it for example if you wanted to add a network connection monitoring package you would use the following command:

```
sudo apt-get install ntop
```

---

