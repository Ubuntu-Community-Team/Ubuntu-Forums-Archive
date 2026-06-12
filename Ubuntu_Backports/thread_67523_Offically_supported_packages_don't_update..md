---
title: "Offically supported packages don't update."
date: 2005-09-20
forum: Ubuntu Backports
---

### Post by Samout on 2005-09-20
Hey!
I have a slight problem. I have the backport adresses on my repositories and it's working fine, exept on those packages that are offically supported (have the ubuntu logo on them). Amarok, mozilla, firefox... i had to download those packages by hand (and do the dpkg) because those weren't automatically updated by synaptic (or any other program for that matter). It doesn't have any mention of backports when looking at versions on properties of each packages, even though i can clearly see that those packages are in backports (for example [ftp://ftp2.caliu.info/backports/dists/hoary-backports/main/binary-i386/)](ftp://ftp2.caliu.info/backports/dists/hoary-backports/main/binary-i386/)). This is only with those that are offically supported, with others i can see the backport version and it updates properly. Any idea why it refuses to notice those packages that are offically supported? Hope you understand what i mean :D
Thanks for help.

---

### Post by Samout on 2005-11-18
Hey... i'm bringing this post up again, since even though i did a fresh new install of breezy, i STILL have the same problem. No one else hasn't had this problem? 
It came up again when i tried to install the mail-notification package i got from here. Well it depends on package called libgnome-menu0, but i couldn't find it with synaptic (or with apt-get for that matter). There is a package called libgnome-menu2, which is, surprise surprise, offically supported (has the ubuntu logo on it). Well i came back to the forum, trying to search for solution, but nobody else seems to have the same problem. So i started to suspect it mught be the same problem again. So i started to look around ubuntu archives with my browser, and guess what...i found it in [http://archive.ubuntulinux.org/ubuntu/pool/main/g/gnome-menus/](http://archive.ubuntulinux.org/ubuntu/pool/main/g/gnome-menus/). So again, even though i have all repositories, those packages which are offically supported don't show the newer version in backports, universe, or other extra repositories.
Again a long post, but i guess my question is, can i somehow "dump" this whole offically supported packages system. It's no use for me anyway, since i install a lot of packages for example from these forums. 
Who knows what other packages (offically supported) i'm missing while my package system refuses even to notice unoffical repositories.

---

### Post by jsmidt on 2005-11-18
Perhaps you could try different repo's.  Here are mine found in /etc/apt/sources.list

```

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
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
deb http://us.archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe


```
      Hopefully this could help

---

### Post by haocheng on 2005-11-23
Packages like firefox are supposed to be upgraded in backports.
Without backports, they will only be upgraded when 
there are security issues.
And the backports server is empty until this morning, 
so I guess it's normal to have nothing to upgrade these days.

However, if you have backports server in your source.list, 
you should notice some upgrades today.

Hope this helps!  :)

---

### Post by Samout on 2005-11-23
[QUOTE=haocheng]Packages like firefox are supposed to be upgraded in backports.
Without backports, they will only be upgraded when 
there are security issues.
And the backports server is empty until this morning, 
so I guess it's normal to have nothing to upgrade these days.

However, if you have backports server in your source.list, 
you should notice some upgrades today.

Hope this helps!  :)[/QUOTE]
AWESOME!! It appears that was the problem. I started synaptic and it found plenty of packages from backports (even those officially supported!!! \o/ ) I'm so happy i don't have the problem anymore with breezy. Now i can be sure i'm not missing any newer versions. :D Thanks for the info!

---

### Post by Licaon on 2005-11-23
using Breezy or Breezy w/ kubuntu-desktop  i have a problem like this:
apt-get/update-notifier/adept says that there are updates available  BUT Synaptic does not see any updates... afaik they share the same sources.list (official+planetmirror+wine but even w/o any un-official )

and another one: how can i stop the update-notifier from showing up in my gnome taskbar? 

any ideas?

10x

---

