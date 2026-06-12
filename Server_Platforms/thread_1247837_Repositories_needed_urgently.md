---
title: "Repositories needed urgently"
date: 2009-08-23
forum: Server Platforms
---

### Post by janipewter on 2009-08-23
This may sound stupid, but is there a publicly available list of Ubuntu repositories? I was using the Virgin Media one (since they are my ISP) but both their Ubuntu and Debian repo's seem to have disappeared over the last couple of weeks. So I'm needing to find a new source for updates, thanks!

---

### Post by drs305 on 2009-08-23
If you are still using feisty fawn, those repositories are no longer supported and have been removed.

Your choices are to do a clean install of a more recent version of Ubuntu, do an online update, or use the archived repositories at [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)
(The EOL link will tell you how to change your repositories to the old.releases site).

A clean install would be easier and more reliable than trying to upgrade through several old versions, but here is the link anyway on how to do an End of Life (EOL) upgrade:
[https://help.ubuntu.com/community/EOLUpgrades]("https://help.ubuntu.com/community/EOLUpgrades")

Here is the Ubuntu release schedule:
[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

---

### Post by janipewter on 2009-08-23
Sorry for the confusion my profile is rather outdated, I'm actually on 9.04 (Jaunty Jackalope). I was using [http://ubuntu.virginmedia.com/](http://ubuntu.virginmedia.com/) but it seems to be offline - along with [http://debian.virginmedia.com/](http://debian.virginmedia.com/) which I was using on my Debian box.

---

### Post by drs305 on 2009-08-23
Here is a clean Jaunty sources.list:
> 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security restricted main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse



---

### Post by janipewter on 2009-08-23
Thank you very much :)

---

### Post by DougieFresh4U on 2009-08-23
You can always change repos via:
**System>Administration>Software Sources**
Under the **'Ubuntu Software'** choose **'Other' **and you shall see a whole list to choose from.

---

### Post by janipewter on 2009-08-23
> **DougieFresh4U said:**
> You can always change repos via:
**System>Administration>Software Sources**
Under the **'Ubuntu Software'** choose **'Other' **and you shall see a whole list to choose from.

[IMG]http://i27.tinypic.com/2przl11.png[/IMG]

:confused:

:P

---

### Post by Paul Weaver on 2009-08-24
> **janipewter said:**
> Thank you very much :)

As you're in the UK, if you change the "us" to "gb" you may get a better response, using a local mirror. E.G. 


deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty restricted main

---

### Post by janipewter on 2009-08-24
Yeah I did already change them all to uk :)

---

