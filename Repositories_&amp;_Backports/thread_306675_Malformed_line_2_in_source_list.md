---
title: "Malformed line 2 in source list"
date: 2006-11-25
forum: Repositories &amp; Backports
---

### Post by trax84lux on 2006-11-25
Hi :)

I'm having a problem with the source list
If I remember well, the only thing I did in the 'Software Sources' was to remove a third party source

Now I'm getting the following error:

> E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

here my edgy-universe.list

> # automatically added by gnome-app-install on 2006-11-12 17:48:36.636823
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) edgy
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) edgy-updates universe


and my sources.list

> # 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy restricted main #Added by software-properties


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy restricted

deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) edgy restricted main universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) edgy-updates restricted main universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse #Added by software-properties


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe #Added by software-properties


already tried to use the edgy-universe.list.save

thanks for your help :)

---

### Post by xopher on 2006-11-25
> here my edgy-universe.list

Quote:
# automatically added by gnome-app-install on 2006-11-12 17:48:36.636823
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) edgy
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security
deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) edgy-updates universe

the line "deb [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) edgy" is incomplete, try adding eg. main universe after edgy, should do the trick.

---

### Post by trax84lux on 2006-11-26
tried to add:

'main universe' and 'universe' but 

then I'm getting the same error for line 3 :???: 

I also tried to set up a new sources.list, but that doesn't seem to help in any way...

Finally I removed the line, so that

> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security

becomes the second line, and I'm getting the same error again (for 2. line)

EDIT: ok... had to add twice 'universe' 2. and 3. line... now I'm getting a duplicate error... I'll have a look then :) but thanks for your help so far :)
EDIT2: Working again :) had to add 'main universe' to the 2. line, and 'universe' to the 3. line :)

---

