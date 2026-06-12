---
title: "ubuntu server repositories question"
date: 2008-08-19
forum: Server Platforms
---

### Post by fouadk on 2008-08-19
hi everyone...

when i installed my ubuntu server , i set up the country to be my country which is different from the united states...so in /etc/apt/sources.list it uses location related to my country....

when i run sudo apt-get update i get some Hash mismatch error so i was advised to use the main server for updating the repositories...i also faced this problem on my desktop installation but it was easy to fix, all i did was this:

System> Administration> Software Sources> Download from.(i changed this field to main servers ...)

how to achieve the same effect on server installations ????

please help

thanks in advance

---

### Post by tamoneya on 2008-08-19
just go in and edit /etc/apt/sources.list manually.  It is best to make a backup first just incase:```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```
Then you can edit like this:```
sudo nano /etc/apt/sources.list
```

---

### Post by fouadk on 2008-08-19
i know i have to change /etc/apt/sources.list but what i don't know is change it to what ???? :)

the ubuntu desktop edition has a built-in gui what does that according to the location you specify... how would i achieve that in the server edition if i want to get my repositories from the main server not from the server associated to my country????

thanks

---

### Post by MJN on 2008-08-19
Post what you've currently got then it will make things a lot clearer.
 
Mathew

---

### Post by fouadk on 2008-08-19
my current /etc/apt/sources.list file currently contain the following:

```

# 
# deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release amd64 (20080423.2)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release amd64 (20080423.2)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://lb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://lb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://lb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://lb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://lb.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://lb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://lb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://lb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://lb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://lb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://lb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://lb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://lb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://lb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse


```

what i need to do is change the default repositories download location the the main server instead of lebanon's server

thanks in advance

---

### Post by MJN on 2008-08-19
Just change every instance of 'lb' to 'main'. You could use sed for this but manually trawling through will be a good lesson of not only what's in there, but also why you next want to learn sed for doing this sort of thing... ;)
 
Mathew

---

### Post by AndyCee on 2008-08-19
> ...manually trawling through will be a good lesson...

:lolflag:
At the very least fouadk could use nano and ^w to each individual occurance.

---

### Post by fouadk on 2008-08-19
thanks a lot :lolflag:

---

