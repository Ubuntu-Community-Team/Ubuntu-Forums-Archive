---
title: "Unable to download new updates including security"
date: 2008-07-08
forum: Security
---

### Post by Neo_The_User on 2008-07-08
Please help. This is the error I get when I go to System > Administration > Software Sources.

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  security/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release)  Unable to find expected entry  security/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release)  Unable to find expected entry  security/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release)  Unable to find expected entry  security/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  security/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

So in the Terminal I type this in there and see my sources.list:
cd /
cd etc
cd apt
sudo gedit sources.list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy security #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-proposed restricted security main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-proposed restricted security main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports restricted security main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports restricted security main multiverse universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy security
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted security main multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted security main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted security main multiverse universe

If you are new to Linux and want to help me, the sources.list file  is in etc/apt/sources.list but I am not sure this problem has anything to do with the sources.list file. Perhaps I could get an exact copy of somebody else's sources.list file that would be great. Please help! Thank you in advance!

---

### Post by Neo_The_User on 2008-07-08
I was wondering if somebody could give me a copy of their sources.list file and some dumbed-down instructions to fix my problem. Thank you so much! I really love updating my system every 5 minutes and now I can't.

---

### Post by Neo_The_User on 2008-07-08
Wow! My computer is really messed up. I just selected a different server entirely and I still got errors! What does malformed release file even mean?

Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy/Release](http://archive.linux.duke.edu/ubuntu/dists/hardy/Release)  Unable to find expected entry  security/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/Release](http://archive.linux.duke.edu/ubuntu/dists/hardy-updates/Release)  Unable to find expected entry  security/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-proposed/Release](http://archive.linux.duke.edu/ubuntu/dists/hardy-proposed/Release)  Unable to find expected entry  security/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  Unable to find expected entry  security/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.linux.duke.edu/ubuntu/dists/hardy-backports/Release](http://archive.linux.duke.edu/ubuntu/dists/hardy-backports/Release)  Unable to find expected entry  security/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Neo_The_User on 2008-07-08
Nevermind

[http://ubuntuforums.org/showthread.php?t=852947](http://ubuntuforums.org/showthread.php?t=852947) was what I meant.

---

