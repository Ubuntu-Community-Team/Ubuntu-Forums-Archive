---
title: "apt-get update connection failed"
date: 2011-03-22
forum: Server Platforms
---

### Post by sunil0683 on 2011-03-22
I am using Ubuntu Server 10.10 64bit. While executing apt-get update i am getting error Connection failed. I have checked other post also some where i found to change the country name 'us' to other present in repository url inside /etc/apt/sources.list file. I tryied with country 'de' and 'in' but then also got the same error..
 
I am getting following error 
 
```

Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
  Connection failed
Err [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg
  Connection failed
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg
  Connection failed

```
 
 
/etc/apt/sources.list file
 
```

#
# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
#deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
#deb [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu) maverick main
#deb-src [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu) maverick main
# deb [http://archive.canonical.com/pool/partner/s/sun-java6](http://archive.canonical.com/pool/partner/s/sun-java6)
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner


```

---

### Post by falko on 2011-03-22
Maybe this is just a temporary problem, so I'd try again. If it still doesn't work, make sure you have valid nameservers in /etc/resolv.conf.

---

### Post by Rakesh055 on 2011-03-22
Can i know how are you trying to update?

whether using LAN or Some wireless device?

If LAN, Who is the ISP Provider?

---

### Post by volkswagner on 2011-03-22
There are a couple people, including myself that have seen [this]("http://ubuntuforums.org/showthread.php?t=1691491") issue.  For myself there was no reference to gateway in /etc/network/interfaces.

---

### Post by Rakesh055 on 2011-03-22
you can change the gateway in /etc/resolv.conf

can you checkout what is there in cat /etc/resolv.conf

---

### Post by falko on 2011-03-22
> **Rakesh055 said:**
> you can change the gateway in /etc/resolv.confresolv.conf is for setting nameservers. The gateway has to be set in /etc/network/interfaces.

---

### Post by Rakesh055 on 2011-03-22
ya when you connect to a LAN for internet, we need to change first DNS address to get connected to internet, i think.


I have tried only this way. 

in the /etc/network/interfaces we can change the network settings. which i have seen. i'm not exactly sure.

---

### Post by sunil0683 on 2011-03-23
Problem is resolved it's because of websense. We removed websense and tryied it working fine.

---

### Post by Rakesh055 on 2011-03-23
oh thats good to listen.


can i know what is websense? what to be changed and other details of it?

---

