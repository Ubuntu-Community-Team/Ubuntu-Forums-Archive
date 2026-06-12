---
title: "apt-get update error? (Solved)"
date: 2005-10-28
forum: Repositories &amp; Backports
---

### Post by wargames on 2005-10-28
Just installed Breezy and uncommented the first 4 repositories which are:
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

After I "sudo apt-get update" it goes and downloads the repositories data but at the end it gives an error about:
gzip: stdin: not in gzip format
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)

then something about it returning a code (1).

It fails to load the above repository and gives an error. I've tried for 2 days at different times and it always gives this error. I only uncommented the first 4 repositories and didn't change them or add anything extra, so this it a stock sources.list file. Any idea why I keep getting this error and how to correct it?

---

### Post by Beggar on 2005-10-28
try to replace the [http://us.archive.*](http://us.archive.*) with [http://archive.*](http://archive.*). this is a shot in the dark based on me knowing the regular servs all work.

just in case my sources.list file: 

```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse

```

---

### Post by wargames on 2005-10-28
Does this mean that the US archives don't work anymore?

---

### Post by wargames on 2005-10-29
I got it working without changing the us.archive in the sources.list.

I did some searching at other linux forums, and someone was having a similar problem. They used "sudo apt-get clean" and then did the apt-get update and it worked. I tried this and it fixed the problem. I guess I just needed to clean out the apt-get cache before doing my first apt-get update.

Hope this helps someone else that might run into this problem.

---

