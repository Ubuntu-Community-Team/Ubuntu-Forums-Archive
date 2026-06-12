---
title: "Error Installing PHP5-GD"
date: 2007-03-12
forum: Server Platforms
---

### Post by eviltang on 2007-03-12
I am trying to add/install GD support to PHP5 on my Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1).

I run:

```
sudo apt-get install php5-gd
```

The result:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-gd: Depends: libfreetype6 (>= 2.2) but it is not installable
           Depends: libgd2-xpm (>= 2.0.33) but it is not installable
           Depends: libjpeg62 but it is not installable
           Depends: libt1-5 (>= 5.0.2) but it is not installable
           Depends: libx11-6 but it is not installable
           Depends: libxpm4 but it is not installable
E: Broken packages
```

Am I really doing an impossible situation, or is there a *fix*?

Thank you for your help in advance!

---

### Post by Nikron on 2007-03-12
sudo apt-get install -s php5-gd

on an Ubuntu Edgy Sever shows everything installing...  check your repos..

---

### Post by eviltang on 2007-03-12
No luck.  Same error.  I checked my repos (I am just using the default with the install)  I also tried enabling universe, etc. no help.

Any other ideas?

---

### Post by Nikron on 2007-03-12
Well...  You can try putting in an install cd, enable it as a repo and see if it works.  You can try enabling debian repos and try that., you can post your sources.list here and I can check it against mine if you want, or you can find dependencies and manually install them.

---

### Post by eviltang on 2007-03-12
Nikron,

Thank you so much for all of your help!  here is my sources.list:

```
#
# deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


# deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

#deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse universe

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
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
 deb http://security.ubuntu.com/ubuntu edgy-security universe
 deb-src http://security.ubuntu.com/ubuntu edgy-security universe
```

---

### Post by Nikron on 2007-03-12
double post

---

### Post by Nikron on 2007-03-12
Why do you have the top 2 repos disabled? try updating and installing after that..
Here's a cleaned up version if you want to use it

```

deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted


deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe


deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

Yup,  just went ahead and installed it on my server and it works fine.  It's probably because you don't have the top two restricted repos enabled.

---

### Post by eviltang on 2007-03-12
Thank you again.  I am going to do a little more searching.

I used your cleaned up version of sources.list.  No luck.  LOL!  Thanks again for your time and help!

---

