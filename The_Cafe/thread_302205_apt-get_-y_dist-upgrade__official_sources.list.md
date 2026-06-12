---
title: "apt-get -y dist-upgrade / official sources.list"
date: 2006-11-18
forum: The Cafe
---

### Post by patrick295767 on 2006-11-18
Hi; 

Usually to pass from the previous ubuntu release to the newer one, we have several possibilities. 

Concerning the apt-get dist-upgrade, is there a way to make it more automatic ?
To avoid taking care about finding a right and withotu much troubles, hte new sources.list.

For instance, in Fedora, it is possible to update the list of debs/packages automomatically.

Could we have somethgin like fully automatic apt-get -y dist-upgrade with a tool that would make sure we have the official /etc/apt/sources.list for dist-upgrading ?


(That's for me, lazy)


**The idea is that NEW USERS can be sure to refrehs easily their wrong sources.list if they messed it up;**

Thanks for information

===
Most of the packages for minimum installation can be there:
[QUOTE]##### OFFICIAL REPOS #####

## Ubuntu
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Updates
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Backports
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse


##### UNOFFICAL REPOS #####

---

