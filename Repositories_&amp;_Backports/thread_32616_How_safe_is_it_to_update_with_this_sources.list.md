---
title: "How safe is it to update with this sources.list?"
date: 2005-05-08
forum: Repositories &amp; Backports
---

### Post by maspro on 2005-05-08
Well, I'm not sure about something. I have installed Ubuntu 5.04 and the Ubuntu add-on cd. I also have the backports and the marillat repositories added to my sources.list. 

If I disable the marillat & backport repositories then Ubuntu says that there are no updates available and that my system is up-to-date. But if I enable those repositories then Synaptic says that there are updates available. How safe is it the get those updates without breaking my system?

This is my sources.list:

## UBUNTU CDROM
#deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## UBUNTU MAIN
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## UBUNTU UNIVERSE
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe

## UBUNTU SECURITY
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## UBUNTU MULTIVERSE
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## UBUNTU BACKPORTS
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

## MARILLAT
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

---

### Post by benplaut on 2005-05-08
not sure about Marillat (what is it, anyway?), but the rest looks A-OK  \\:D/

---

### Post by Xian on 2005-05-08
[QUOTE=maspro]If I disable the marillat & backport repositories then Ubuntu says that there are no updates available and that my system is up-to-date. But if I enable those repositories then Synaptic says that there are updates available. How safe is it the get those updates without breaking my system?[/QUOTE]
They are relatively safe as many users have those listed in their source list ifle, but since those packages are unsupported you just need to understand that they are akin to a testing repository, and _could_ cause some system issues.

---

### Post by Xian on 2005-05-08
[QUOTE=benplaut]not sure about Marillat (what is it, anyway?)[/QUOTE]
Codecs, mplayer, other multimedia packages, etc.

---

### Post by dewey on 2005-05-08
Marillat is nerim.net, run by Christian Marillat.  I've never met him, but he seems to be well trusted, so the chances of one of his packages being intentionally malicious is pretty small.  I have it added to my sources, without any conflicting problems.

Both Marillat and Backports are unsupported by Ubuntu, so you can't hold them responsible, but if you want the latest and greatest packages, they're the way to go.

---

### Post by maspro on 2005-05-09
Well I don't mean that it could be malicious, but I hear several stories that it is unwise to add Debian Sarge and Sid repositories because Ubunutu isn't 100% compatible with Debian. And since Marillat and the backports aren't official either. 

Also in the past sometimes I got errors while trying to update with the Marillat repositories enabled, after I disabled Marillat all was fine again. I did add the keyserver for Marillat.

---

