---
title: "libapache-dbi-perl"
date: 2007-06-05
forum: Server Platforms
---

### Post by jsaumer on 2007-06-05
Hello,

I am tyring to install libapache-dbi-perl so I can make a OCS inventory server on a fresh ubuntu box.  When I try the apt-get install libapache-dbi-perl, it says that it can't find the package.

Is this package depreciated and is it somehting else now?

I am just wondering how I can get this installed so I can finish up my sevrer.

Thanks!
jsaumer

---

### Post by turinglabs on 2007-06-05
libapache-dbi-perl is in the universe repository, so make sure you have that enabled.

```

doug@dev:~$ apt-cache show libapache-dbi-perl | grep Section
Section: universe/perl

```

---

### Post by jsaumer on 2007-06-05
I do have my universals uncommented in my sources.list and it is still not finding it.

*scratches head*

---

### Post by turinglabs on 2007-06-05
Can you post your sources.list, also the exact error message?

---

### Post by jsaumer on 2007-06-05
Here is the error message

```

# apt-get install libapache-dbi-perl
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libapache-dbi-perl

```

Here is the sources.list
```
# deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
```

---

### Post by turinglabs on 2007-06-05
Thanks, the only thing I can think of is that you did not run 'apt-get update' after enabling the universe repository.

---

### Post by jsaumer on 2007-06-05
htat did it.. it's funny how I forget such simple things.

Thanks for the guidance.

---

