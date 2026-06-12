---
title: "Original Ubuntu Server 9.04 sources.list?"
date: 2009-08-11
forum: Server Platforms
---

### Post by ayame on 2009-08-11
Short version: Can anyone please post a Server 9.04 x86 sources.list? :<

I have a server with OVH.co.uk.

I used their frontend to install Ubuntu Server 9.04 (x86). I ssh'd to the server, changed the root password, added a normal user and added that user to the sudoers file.

Now, I wanted to download the backup from the previous server. I tried launching lftp, but it wasn't preinstalled. Fair enough, I thought, I'd just get it.

```
$ sudo apt-get install lftp
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package lftp
```I thought that was strange, but figured I'd just compile it from source. I downloaded the source, and the configure script told me gcc was not present. Strange, but I figured I'd just get that too...
```
$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package gcc
```And then I checked, and the package is there! [http://packages.ubuntu.com/jaunty/gcc](http://packages.ubuntu.com/jaunty/gcc)

...and then I checked my /etc/apt/sources.list file... and it was using ovh repositories, apart for the security ones. Where can I find the original sources.list? (I assume my other issues, such as gcc being missing, are also caused by this being some OVH flavor of Ubuntu Server)

edit: Upon running apt-get update I was able to find the gcc package on their repositories, but then I get this error:
```
$ sudo apt-get install gcc
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  gcc: Depends: gcc-4.3 (>= 4.3.2-1) but it is not going to be installed
       Recommends: libc6-dev but it is not going to be installed or
                   libc-dev
E: Broken packages
```Getting one dependency requires more, and I'm really not keen on doing this manually :/

edit2: I also get errors like this:
```
Depends: libdbus-glib-1-2 (>= 0.71) but it is not going to be installed
```Shouldn't it automatically get dependencies for me? How can I make it automatically install dependencies?


After all that... it would probably be easier to just install a stock Ubuntu Server, without all the OVH stuff. Is there a way to control a server installation completely through SSH, from start to finish? (of course, it will be started from this current installation)

---

### Post by ayame on 2009-08-12
Anyone? Please just throw me a sources.list =/

---

### Post by Serangan on 2009-08-12
```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty main restricted
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty-updates main restricted
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty universe
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty universe
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty-updates universe
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty multiverse
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty multiverse
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty-updates multiverse
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty-security main restricted
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty-security main restricted
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty-security universe
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty-security universe
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty-security multiverse
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ jaunty-security multiverse


#Extras

#deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main 
#deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu jaunty main
```

Thats my sources.list change [http://mirror.internode.on.net/pub/ubuntu/ubuntu/](http://mirror.internode.on.net/pub/ubuntu/ubuntu/) to your local mirror.

---

### Post by dregin on 2009-08-17
Hey man. Did ya ever get this sorted? I'm having the same issue on my OVH box. Spent HOURS trying to install vanilla 9.04-server on it, but gave up after the vKVM kept crapping out mid-install.

---

