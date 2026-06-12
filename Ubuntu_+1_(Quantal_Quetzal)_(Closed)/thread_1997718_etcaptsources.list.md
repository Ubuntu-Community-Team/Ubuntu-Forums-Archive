---
title: "/etc/apt/sources.list"
date: 2012-06-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Gregory Lee on 2012-06-05
I'm using a version of quantal derived by upgrading precise, using aptitude.  I wonder whether the file /etc/apt/sources.list that I'm using is correct.  I got it by editing the one from precise and substituting "quantal" for "precise", as suggested in the above Release sticky.  And I also commented out two "extras" lines which gave errors.

But maybe I'm missing references for some archives, or maybe I made mistakes.  Is there a reference copy for quantal around some place on the web that I could use to check my version against?

---

### Post by Harry33 on 2012-06-05
> **Gregory Lee said:**
> I'm using a version of quantal derived by upgrading precise, using aptitude.  I wonder whether the file /etc/apt/sources.list that I'm using is correct.  I got it by editing the one from precise and substituting "quantal" for "precise", as suggested in the above Release sticky.  And I also commented out two "extras" lines which gave errors.

But maybe I'm missing references for some archives, or maybe I made mistakes.  Is there a reference copy for quantal around some place on the web that I could use to check my version against?

Perhaps there is, but the easiest way is to print your sources.list file here and let us see and check it out.

---

### Post by Gregory Lee on 2012-06-05
> **Harry33 said:**
> Perhaps there is, but the easiest way is to print your sources.list file here and let us see and check it out.
Okay.  TIA.

```

# s/precise/quantal/g
#deb cdrom:[Ubuntu 12.04 LTS _quantal Pangolin_ - Alpha amd64 (20120201.2)]/ dists/quantal/main/binary-i386/

#deb cdrom:[Ubuntu 12.04 LTS _quantal Pangolin_ - Alpha amd64 (20120201.2)]/ dists/quantal/restricted/binary-i386/
#deb cdrom:[Ubuntu 12.04 LTS _quantal Pangolin_ - Alpha amd64 (20120201.2)]/ quantal main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ quantal main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ quantal universe
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal universe
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ quantal multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal multiverse
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
deb http://security.ubuntu.com/ubuntu quantal-security universe
deb-src http://security.ubuntu.com/ubuntu quantal-security universe
deb http://security.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
### --gl uncommented the next two lines
deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
### --gl the next two lines gave errors for quantal, so I'm commenting them.
## deb http://extras.ubuntu.com/ubuntu quantal main
## deb-src http://extras.ubuntu.com/ubuntu quantal main

```

---

### Post by sammiev on 2012-06-05
[This]("http://ubuntuforums.org/showthread.php?t=1994822") may have been the post that you read. Post your source list please. :)

---

### Post by Harry33 on 2012-06-05
Well the sources list seems to be technically fine.
However the quantal-updates are not yet needed, it is empty (until release time).
And of course, if you want to play with proposed updates then you may want to enable the proposed repository too.

---

### Post by Gregory Lee on 2012-06-05
> **Harry33 said:**
> Well the sources list seems to be technically fine.
However the quantal-updates are not yet needed, it is empty (until release time).
And of course, if you want to play with proposed updates then you may want to enable the proposed repository too.
Thanks.

---

