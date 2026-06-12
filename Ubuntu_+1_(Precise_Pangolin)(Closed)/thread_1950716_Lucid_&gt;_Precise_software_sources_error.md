---
title: "Lucid &gt; Precise software sources error"
date: 2012-04-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2012-04-01
I need to borrow a fresh pair of eyes :)

I keep getting this error when updating the package list in a Precise that was upgraded from Lucid:

> W: Duplicate sources.list entry [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages)

Here's a copy of the sources.list:

> # deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

# deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main # disabled on upgrade to precise
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed restricted main multiverse universe

And /var/lib/apt/lists:

> lance@lance-desktop:~$ ls /var/lib/apt/lists
archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages
archive.canonical.com_ubuntu_dists_precise_partner_source_Sources
archive.canonical.com_ubuntu_dists_precise_Release
archive.canonical.com_ubuntu_dists_precise_Release.gpg
archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages
archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Index
archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en
archive.ubuntu.com_ubuntu_dists_precise-updates_Release
archive.ubuntu.com_ubuntu_dists_precise-updates_Release.gpg
lock
partial
security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Index
security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_precise-security_main_source_Sources
security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Index
security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_precise-security_multiverse_source_Sources
security.ubuntu.com_ubuntu_dists_precise-security_Release
security.ubuntu.com_ubuntu_dists_precise-security_Release.gpg
security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Index
security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_precise-security_restricted_source_Sources
security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages
security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Index
security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en
security.ubuntu.com_ubuntu_dists_precise-security_universe_source_Sources
us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Index
us.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Index
us.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_precise-backports_Release
us.archive.ubuntu.com_ubuntu_dists_precise-backports_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Index
us.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Index
us.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Index
us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources
us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Index
us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_precise_multiverse_source_Sources
us.archive.ubuntu.com_ubuntu_dists_precise-proposed_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_precise-proposed_main_i18n_Index
us.archive.ubuntu.com_ubuntu_dists_precise-proposed_main_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_precise-proposed_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_precise-proposed_multiverse_i18n_Index
us.archive.ubuntu.com_ubuntu_dists_precise-proposed_multiverse_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_precise-proposed_Release
us.archive.ubuntu.com_ubuntu_dists_precise-proposed_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_precise-proposed_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_precise-proposed_restricted_i18n_Index
us.archive.ubuntu.com_ubuntu_dists_precise-proposed_restricted_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_precise-proposed_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_precise-proposed_universe_i18n_Index
us.archive.ubuntu.com_ubuntu_dists_precise-proposed_universe_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_precise_Release
us.archive.ubuntu.com_ubuntu_dists_precise_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Index
us.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_precise_restricted_source_Sources
us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Index
us.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources
us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Index
us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Index
us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_precise-updates_Release
us.archive.ubuntu.com_ubuntu_dists_precise-updates_Release.gpg
us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Index
us.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en
us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages
us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Index
us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en

And all of etc/apt:

```
lance@lance-desktop:~$ ls /etc/apt
apt.conf.d     sources.list    sources.list.distUpgrade  trustdb.gpg  trusted.gpg~
preferences.d  sources.list.d  sources.list.save         trusted.gpg  trusted.gpg.d

```

What am I overlooking?

I've considered just copying a sources.list from a known good Precise, good or bad idea?

I could also just reinstall but how much fun is that ;)

---

### Post by ajgreeny on 2012-04-01
I would back up what you have now and then try to make a new software sources list with this site:-
[Sources List Generator]("http://repogen.simplylinux.ch/") 
If it works OK, great; if not you can just restore the old list and look for other means of overcoming the problem.

---

### Post by philinux on 2012-04-01
Here's my sources list if you want to use it.

```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha amd64 (20120131.2)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Alpha amd64 (20120131.2)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise universe
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

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
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by subhadip_sky on 2012-04-01
Yes, go to the Source Generator site mentioned above and generate your own sources according to your need. I did something and messed it up too. But rather than finding out what went wrong, it's generally easier to generate new list and replace.

---

### Post by jerrrys on 2012-04-01
A trick I found.  Make a backup of sources.list and then delete everything in the original sources.list.  then

sudo apt-get update

and your sources should regenerate

---

