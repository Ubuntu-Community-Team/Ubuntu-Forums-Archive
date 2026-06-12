---
title: "E: Type 'repository' is not known on line 38 i...."
date: 2007-03-16
forum: Repositories &amp; Backports
---

### Post by Dragon93 on 2007-03-16
I just suddenly got a problem when i started up Ubuntu:

E: Type 'repository' is not known on line 38 in source list /etc/apt/sources.list
E:The list of sources could not be read.

Here is my sources.list:

> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

## nVidia driver repository
repository

Please help.

---

### Post by dannyboy79 on 2007-03-16
well come on now, just look at line 38, it doesn't look like the rest does it. just erase it.

it's this line here:

repository

it's no good.

Im sorry for being so rude!!! It's just that sometimes the developers try so hard to program in stuff so that when something goes wrong, you'll kno how to fix it and I would say the developers did a great job here, they informed you what was wrong but you still couldn't understand that line 38 was no good. I guess all I am saying is just apply some logic sometimes and you'll figure it out.

---

### Post by Dragon93 on 2007-03-16
Yeh, i just had a look and figured that out already, but i can't edit it for some reason.

---

### Post by haricharan on 2007-03-16
type```
gksudo gedit /etc/apt/sources.list
```to edit the repositories

---

### Post by Dragon93 on 2007-03-16
I got my dad to help now he's home, thanks any way.

---

