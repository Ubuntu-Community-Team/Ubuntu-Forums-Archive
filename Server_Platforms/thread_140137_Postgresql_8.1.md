---
title: "Postgresql 8.1"
date: 2006-03-05
forum: Server Platforms
---

### Post by cmay4 on 2006-03-05
I am a longtime Gentoo user making the switch over to Ubuntu.  I am still struggling with understanding apt vs portage.  When I search apt-cache, I see that default (7.4) and 8.0 versions of Postgresql are there.  I don't see 8.1, which is odd since it was released a while ago.  

Is there something I'm missing?  Thanks for the help,

Chuck

---

### Post by noigeaR on 2006-03-05
once a stable ubuntu version is released, no updates to new versions of programs are made. there are only security and stability patches, so postgresql 8.1 will never officially be in the breezy badger (ubuntu 5.10) repositories.
new versions are added and tested in the unstable development branch (currently ubuntu 6.04 dapper drake). dapper drake will be released this april as the new stable release of ubuntu and you can easily update your whole distribution from breezy to badger with a simple apt-get command (and thus get postgresql 8.1, firefox 1.5 and many other new versions of all the programs in the repository).
since new ubuntu versions are released at regular intervals of 6 months you have to wait at most 6 months for new program versions. the upside is, that the new versions are heavily tested in the development branch and you can always upgrade from one stable release to the next.

if you really need the newest version of some program and don't want to wait for the next stable release, you have 3 options available.
1) you can request a backport for a packet. a backport is a new version from the development branch that is made available for the current stable release. see the backports forum for more info [http://www.ubuntuforums.org/forumdisplay.php?f=47](http://www.ubuntuforums.org/forumdisplay.php?f=47)
2) upgrade to the unstable version. you will have lots of updates to the newest versions of all the packets available (and probably also some instability and breakage)
3) download and install the new program version directly from the developer and not from the official ubuntu repository.

---

### Post by cmay4 on 2006-03-05
That makes sense.  I was pretty sure it worked that way.  Thanks for clearing things up.

---

