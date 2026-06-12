---
title: "Apt-get don't update package database"
date: 2006-11-10
forum: Repositories &amp; Backports
---

### Post by peter07 on 2006-11-10
I'm trying to install the newest nvidia drivers from:

[http://albertomilone.com/index.html](http://albertomilone.com/index.html)

I have correct source.list:

> deb [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
deb-src [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports universe main multiverse restricted


## NVIDIA TESTING

deb [http://albertomilone.com/drivers/edgy/nonlegacy/64bit](http://albertomilone.com/drivers/edgy/nonlegacy/64bit) binary/

After update: ( my translation ) 
> sudo aptitude update
Reading package list... Ready
Bulding depending tree ... Ready
Reading state information... Ready
Initialization packages state... Ready
Building tag base... Ready
Downloading:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ignoring: [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-pl
Downloading::2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [189B]
Ignoring [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-pl
Downloading::3 [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) edgy Release.gpg [191B]
Old [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) edgy/universe Translation-pl
Oldhttp://pl.archive.ubuntu.com edgy/main Translation-pl
Old [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) edgy/multiverse Translation-pl
Old [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) edgy/restricted Translation-pl
Ignoringhttp://security.ubuntu.com edgy-security/main Translation-pl
Ignoring [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-pl
Ignoring [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-pl
Old [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ignoring [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-pl
Ignoring [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-pl
Ignoring [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-pl
Downloading:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release.gpg [191B]
Ignoring [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Translation-pl
Ignoring [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Translation-pl
Old [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) edgy Release
Old [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Ignoring [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Translation-pl
Ignoringhttp://archive.ubuntu.com edgy-proposed/restricted Translation-pl
Downloading:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [189B]
Ignoring [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-pl
Old [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) edgy/universe Packages
Ignoring [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-pl
Ignoring [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-pl
Old [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Oldhttp://security.ubuntu.com edgy-security/multiverse Packages
Old [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Ignoring [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-pl
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed Release
Old [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) edgy/main Packages
Oldhttp://pl.archive.ubuntu.com edgy/multiverse Packages
Old [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) edgy/restricted Packages
Old [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) edgy/universe Sources
Old [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) edgy/main Sources
Old [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) edgy/multiverse Sources
Old [http://pl.archive.ubuntu.com](http://pl.archive.ubuntu.com) edgy/restricted Sources
Old [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Old [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Old [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Old [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Sources
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Sources
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Packages
Oldhttp://archive.ubuntu.com edgy-proposed/main Packages
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Packages
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Packages
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/universe Sources
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/main Sources
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/multiverse Sources
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-proposed/restricted Sources
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Oldhttp://archive.ubuntu.com edgy-backports/restricted Packages
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources
Old [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources
Ignoring [http://albertomilone.com](http://albertomilone.com) binary/ Release.gpg
Ignoring [http://albertomilone.com](http://albertomilone.com) binary/ Translation-pl
Ignoring [http://albertomilone.com](http://albertomilone.com) binary/ Release
Oldhttp://albertomilone.com binary/ Packages
Downloaded 5B in 3s (2B/s)
Reading packages list... Ready

And upgrade:
> sudo aptitude upgrade
Reading package list... Ready
Bulding depending tree ... Ready
Reading state information... Ready
Initialization packages state... Ready
Building tag base... Ready
Fallowing packages were stoped:
kile-i18n
0 pakietów updated, 0 installed, 0 for delete and 1 didn't change.
Download 0B.

New driver is not available for me. I've spoken with tseliot:
[http://ubuntuforums.org/showthread.php?t=255929&page=52](http://ubuntuforums.org/showthread.php?t=255929&page=52) and I've tried his source.list with no effect. 

[B]Why some repositions are ignored?
PLZ HELP[/B]

---

