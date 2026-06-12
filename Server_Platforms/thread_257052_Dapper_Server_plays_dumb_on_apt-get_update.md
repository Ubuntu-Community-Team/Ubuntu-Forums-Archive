---
title: "Dapper Server plays dumb on apt-get update"
date: 2006-09-14
forum: Server Platforms
---

### Post by Frank-Hamersley on 2006-09-14
Hmmmm...here was me thinkin' my frequent "apt-get update" event were downloading all the hot patches and keeping my firewall looking spicko!

Wrong!  As I was cruising the forums I noticed the advisory for bind9 (build 1.1) and having only just installed the base package I knew it had not been autopatched.

When apt-get runs it seems to list all the right urls (I am using the au. set of servers) but it doesn't collect any updated packages!  At this early stage I can't think of where the problem might lie...anyone got any hot tips on what to look for in the .conf?  How do I give it a shake to ensure I really am patched to the gills?

Cheers, Frank.

---

### Post by Frank-Hamersley on 2006-09-14
Here is my /etc/apt/sources.list - looks ok to me - what am I missing here? Cheers Frank

# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#EOF

---

### Post by lamego on 2006-09-14
Some mirrors do take 2 to 3 days to get updated, if yoor apt-get upgrade doesn't install new packages its because they are not yet available on the repositories you have setup.

Btw, I am assuming you know that you need to sudo apt-get upgrade after apt-get update.

---

### Post by Frank-Hamersley on 2006-09-14
Doh - how embarrassing - missed the "update" - aarrgh!

As a feeble defence, I would consider it a far more useful if "upgrade" commented (on completion) on the number of packages that are now downlevel - to ensure the sysadmin is appraised of the situation.  IMO there is no value in "update" remaining silent on the subject when there are packages known to be out of date.

Thanks for that.  Cheers Frank.

---

