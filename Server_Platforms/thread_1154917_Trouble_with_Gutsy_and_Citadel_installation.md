---
title: "Trouble with Gutsy and Citadel installation"
date: 2009-05-10
forum: Server Platforms
---

### Post by etali on 2009-05-10
I'm trying to install Citadel on a Gutsy server, but I'm having trouble with the repositories.

When I try to install citadel-suite I get this message:


  citadel-suite:
 Depends: citadel-server but it is not going to be installed
 Depends: citadel-mta but it is not going to be installed
 Depends: citadel-webcit but it is not going to be installed
 Depends: citadel-client but it is not going to be installed
E: Broken packages

This is the repository I'm using for citadel itself:

deb [http://ubuntu.citadel.org/ubuntu/](http://ubuntu.citadel.org/ubuntu/) gutsy main

If I try to install, say, citadel-server, I see that it has problems with dependencies on libdb4.3 - for example.  Which isn't in any of the standard ubuntu repositories I have in my sources.list.

Any advice anyone can offer would be much appreciated.


EDITED TO ADD:

I've been trying to install some other stuff, and I can't even find iotop in the repositiories.  I searched for some recommended repos in case mine are out of date - my sources.list now looks like this:



deb  [http://repository.debuntu.org/](http://repository.debuntu.org/) gutsy multiverse

deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy-backports main restricted uni$
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security


deb [http://ubuntu.citadel.org/ubuntu/](http://ubuntu.citadel.org/ubuntu/) gutsy main

## team.
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted unive$
 deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted u$

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


Any advice much appreciated.

---

### Post by ugm6hr on 2009-05-10
Gutsy is no longer supported, so the repositories won't work.

They are still available somewhere, but I'd recommend you reinstall Hardy or upgrade.

---

### Post by etali on 2009-05-10
Thanks for your response.

The server in question is a VPS that I don't have physical access to.  

I tried installing update-manager-core, to do the upgrade, but that's not in the repository either :(

Any suggestions for repositories that may work would be much appreciated!  If not, I'll ask the host if they'll update the server for me.

---

### Post by ugm6hr on 2009-05-10
Try adding the old-releases repo:

```
deb http://old-releases.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
```

Then try to install 
```
sudo aptitude install update-manager-core
```

---

