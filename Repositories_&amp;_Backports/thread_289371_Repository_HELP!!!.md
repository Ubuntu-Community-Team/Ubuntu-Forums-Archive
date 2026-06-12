---
title: "Repository HELP!!!"
date: 2006-10-30
forum: Repositories &amp; Backports
---

### Post by Blacktalon on 2006-10-30
Hello,

I seem to be having some trouble when i do my sudo apt-get update i keep getting this:  Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release](http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release)  Unable to find expected entry  universe-security/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


_____________________________________________________
here's my source.list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

Any help would be appreciated
Thanks,
~BT

---

### Post by flixer on 2006-10-31
This should help.
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

---

### Post by Blacktalon on 2006-10-31
nope, I still get these errors:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release](http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release)  Unable to find expected entry  universe-security/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release)  Unable to find expected entry  mutliverse/source/Sources in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Any other suggestions?

---

### Post by flixer on 2006-10-31
Which do you use, Edgy or Dapper?

---

### Post by Blacktalon on 2006-10-31
Edgy Eft

---

### Post by Bartender on 2006-11-01
I'm having trouble with dapper u.s. servers (on the west coast).  Yesterday at a friend's house on his Qwest DSL line we couldn't get anything out of the u.s. servers.  I tried at home this morning (0500 hours PST) on our horribly slow dial-up connection and was able to get some data at about 1 kbps.  Don't know what's up, I woulda expected more people asking questions!

---

### Post by flixer on 2006-11-02
Have you tried pinging us.archive.ubuntu.com?

---

