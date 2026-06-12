---
title: "Security update problem"
date: 2008-07-04
forum: Security
---

### Post by gatos on 2008-07-04
Hi
I am a fairly newbie so please mind my daft question. :)
I am using Ubuntu Hardy and have just realized that the Important security updates (hardy security) box in Software sources is unticked. I tried ticking it, but no luck. I tried unticking and ticking the rest and they are fine. I googled this problem but no luck. Here is a screenshot of what I mean.


Any help is welcome

---

### Post by Sef on 2008-07-05
It looks like a bug.  Here is a [ launchpad report]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/245721") on it.

---

### Post by hyper_ch on 2008-07-05
you can manually add them to your sources.list if you want to do that.

---

### Post by gatos on 2008-07-05
Thanks for both your answers. I checked in Launchpad but I could not find this particular bug. Thanks anyway.

> **hyper_ch said:**
> you can manually add them to your sources.list if you want to do that.

I did  sudo gedit /etc/apt/sources.list and this is what is included:
```
## a &#8220;general&#8221; sources.list for Hardy Heron; all sources are uncommented.

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in

## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe

deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse

deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the &#8216;backports&#8217;
## repository.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical&#8217;s
## &#8216;partner&#8217; repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://ppa.launchpad.net/compiz/ubuntu hardy main
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe
deb-src http://ppa.launchpad.net/compiz/ubuntu hardy main
```

I searched around and found the following:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy-backports restricted main multiverse universe

Do I need to add all of them or do I excluded the last two ones?
Thanks for the help guys

---

### Post by hyper_ch on 2008-07-05
first step for a solution to every problem is trying to reasearch it first

[http://ubuntuforums.org/showthread.php?t=849497](http://ubuntuforums.org/showthread.php?t=849497)

---

### Post by gatos on 2008-07-05
> **hyper_ch said:**
> first step for a solution to every problem is trying to reasearch it first

[http://ubuntuforums.org/showthread.php?t=849497](http://ubuntuforums.org/showthread.php?t=849497)

Sorry for that. I changed my post since. I have only been around the block for about two months and it is a big step from the wolrd of windowzz. So please be kind and bare with me for a tiny bit longer.:(
I did not find that particular link earlier, so thanks for pointing it out to me.

---

