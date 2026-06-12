---
title: "Problems with apt-get in Ubuntu LAMP 8.04 server"
date: 2008-06-08
forum: Server Platforms
---

### Post by Elsven on 2008-06-08
First of all I am relatively new to linux so if I say something that my not be accurate or confusing please forgive me.  I am still learning a lot of the terminology that most of you Linux guru's use.  Now on to my problem, I have just installed the latest version if Ubuntu LAMP 8.04 I am trying to use the atp-get to install some programs that I am wanting however when I do an update I get this. 

> 
rebenal@Athena:~$ sudo apt-get update
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Sources
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Sources
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Sources
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Sources
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Sources
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Sources
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Sources
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Sources
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Packages
  404 Not Found
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Sources
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
rebenal@Athena:~$ 


After I tried the update I tried to install ebox and this is what happened.

> 
rebenal@Athena:~$ sudo apt-get ebox
E: Invalid operation ebox
rebenal@Athena:~$


As I said, I am relatively new to this all of these instructions were in the official Ubuntu documentation.  This makes me wonder if I may have done something wrong during installation.  Any help on the matter would be greatly appreciated. 

Regards,

Richard Ebenal

---

### Post by quelx on 2008-06-08
> **Elsven said:**
> First of all I am relatively new to linux so if I say something that my not be accurate or confusing please forgive me.  I am still learning a lot of the terminology that most of you Linux guru's use.  Now on to my problem, I have just installed the latest version if Ubuntu LAMP 8.04 I am trying to use the atp-get to install some programs that I am wanting however when I do an update I get this. 

can you post the output of this command?
```
cat /etc/apt/sources.list
```

> After I tried the update I tried to install ebox and this is what happened.

the command should be ```
sudo apt-get [COLOR="Red"]install[/COLOR] ebox
``` check out ```
man apt-get
```

---

### Post by Elsven on 2008-06-08
Sorry yes you are correct and that is the command I have been using lol dunno why I never did it correctly that time.

```

rebenal@Athena:~$
rebenal@Athena:~$
rebenal@Athena:~$ cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hardy main restricted

#deb cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

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
rebenal@Athena:~$

```

This Is what I get when i try the install.

```

rebenal@Athena:~$ sudo apt-get install ebox
[sudo] password for rebenal:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ebox
rebenal@Athena:~$

```

---

### Post by Ptero-4 on 2008-06-08
change the repositories to the main ones (remove the "ca." between http:// and archive.ubuntu.com in every line it appears) and type ```
sudo aptitude update
```

---

### Post by Elsven on 2008-06-09
Your last reply worked, thank you for you help.

Regards,

Richard

---

