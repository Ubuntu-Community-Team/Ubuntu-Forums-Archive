---
title: "Duplicate sources.list entries"
date: 2015-05-11
forum: Ubuntu/Debian BASED
---

### Post by brunobuescher on 2015-05-11
I get this error:                                          
```
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/multiverse amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/restricted amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/multiverse i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/restricted i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_universe_binary-i386_Packages)
```

The files are very long so I will only post them if you need them. I looked online for solutions but I don't understand which lines to comment out. 
Thanks for help! 
I am on El OS 0.3 64 bit

---

### Post by slickymaster on 2015-05-11
Hi brunobuescher, welcome to the forums.

I've edit your post, by adding code tags, because output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The use of [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

Please provide us your complete sources list output```
cat /etc/apt/sources.list
```

---

### Post by brunobuescher on 2015-05-13
Lol, I must look like a 14 year old... 

Here ist the sources.list: 
```
# deb cdrom:[elementary OS 0.3 _Freya_ - Stable amd64 (20150411)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://de.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ trusty-updates restricted main
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty universe
deb http://de.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://de.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner
## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu trusty main
# deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://security.ubuntu.com/ubuntu/ trusty-security multiverse restricted main universe


```

---

### Post by slickymaster on 2015-05-13
With your favorite text editor delete the duplicate entries.

You have:
```
deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
```

And also have:
```
deb http://security.ubuntu.com/ubuntu/ trusty-security universe restricted multiverse main
```

---

