---
title: "Repositories on Gusty Gibbon?"
date: 2007-09-10
forum: Repositories &amp; Backports
---

### Post by jauhari on 2007-09-10
Today I tried to Install and running Gusty Gibbon(7.10) and I have some problem, why my Repositories doesn't work?

What's wrong? and how to add Repositories on Gusty Gibbon?

Because I need to install some codec on it.

---

### Post by bapoumba on 2007-09-11
Could you please post your sources.list?
```
cat /etc/apt/sources.list
```

---

### Post by krystalsavage on 2007-09-28
I've just installed Gutsy on my Core2Duo system ... everything installed fine from my burned cd with beta version of gutsy. Unfortunately, trying to install any apps from Applications>Add/Remove or even from Synaptic Package Manager results in failed repository indexes. Below is my resources.list file i got from running "cat /etc/apt/sources.list":

<---------- resources.list ----------------->
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Beta i386 (20070925.2)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse

---

### Post by bapoumba on 2007-09-29
Can you please post the complete error output to:
```
sudo aptitude update
```
After removing the cdrom in the sources.list?

---

### Post by LongTooth on 2007-10-01
I too have the same problem. I've recently upgrade from 7.04 to 7.10 - without a hitch, by the way - and can't seem to install compizconfig-settings-manage although I have the proper repos listed. So what gives? 

I have the needed repositories but no luck when I try to install the compizconfig-settings-manager. 

It is because Gutsy is sill in beta? I would have thought since it's so close to the final release I would be able to install this program. 

Can some one let me know? 

Thanks.

---

### Post by 1337455 10534 on 2007-10-04
Can trevino or anyone do something like a comprehensive source.list for Gutsy?
On another note, on Feisty, I couldn't find a script that would fix the gpg errors using trevinos list. So I made my own. And it went a lot further, so it's completely replaced Automatix and Easy Ubuntu for me.. so.. if anyone wants to test it: [email]vminch@gmail.com[/email].

---

