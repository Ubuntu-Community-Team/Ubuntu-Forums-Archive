---
title: "No Updates do to bad SIG?"
date: 2005-10-17
forum: Repositories &amp; Backports
---

### Post by nitricacid on 2005-10-17
Ever since I updated to Breezy Full I have been getting this error when ever I do a 'Sudo apt-get update' in a terminal ```

Fetched 379B in 1s (249B/s)
Reading package lists... Done
W: GPG error: http://us.archive.ubuntu.com breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://us.archive.ubuntu.com breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
```

Here is my sources.list:
```
## deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# deb http://security.ubuntu.com/ubuntu breezy-security universe
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://us.archive.ubuntu.com/ubuntu/ breezy multiverse universe main restricted
```

My question(s):
1. Has there been any updates since the full Breezy release?
If so could my BADSIG error being hindering my updates?
2. How do I fix this BADSIG error?

---

### Post by AndyAWS on 2005-10-17
Same problem here...

---

### Post by dustigroove on 2005-10-17
Per cytoplasm in the thread [here]("http://www.ubuntuforums.org/showthread.php?t=78033")...

[QUOTE=cytoplasm]Remove the "us" references in the URL within the sources.list file and then run update again.  It will then work correctly.[/QUOTE]

---

### Post by ecobuntu on 2005-10-17
This problem has happened to everyone who has posted today!

---

### Post by nitricacid on 2005-10-18
This is why I love using Ubuntu.
You have such a great community to come to for help.

Thanks again! :D

---

