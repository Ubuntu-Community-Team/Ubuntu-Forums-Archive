---
title: "Can not install mplayer"
date: 2005-08-22
forum: Repositories &amp; Backports
---

### Post by clehel on 2005-08-22
Hi,
I tried to install mplayer (version 1:1.0-pre7-0.0 unstable) probably it is from Marillat repository. Synaptic gave the error message below. Previously I ran into similar problem with acroread version 7, it was also from Marillat repo, I think. Synaptic then was complaining about a libc6 dependency problem, too. Is there anything wrong with my sources.list file? Is there any way to install mplayer in Ubuntu, even an earlier version, in case if this one is not possible? Thank you very much in advance for your help!!

> Error message by Synaptic:

Could not mark all packages for installation or upgrade.The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

mplayer-386:
 Depends: libavcodeccvs but it is not going to be installed
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed
  Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
 Depends: libpostproc0 but it is not going to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
 Depends: libxvidcore4 but it is not going to be installed
 Depends: xmms but it is not going to be installed

> Available repositories in "sources.list" file:

deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hoary main restricted 
deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hoary main restricted 

deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 
deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hoary-updates main restricted 

deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hoary universe 
deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hoary universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse 

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted 

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 

---

### Post by Kapre on 2005-08-22
[QUOTE=clehel]Hi,
I tried to install mplayer (version 1:1.0-pre7-0.0 unstable) probably it is from Marillat repository. Synaptic gave the error message below. Previously I ran into similar problem with acroread version 7, it was also from Marillat repo, I think. Synaptic then was complaining about a libc6 dependency problem, too. Is there anything wrong with my sources.list file? Is there any way to install mplayer in Ubuntu, even an earlier version, in case if this one is not possible? Thank you very much in advance for your help!![/QUOTE]
Clehel - seems like your sources.list is outdated (still using the Marillat repo). Try to update it with the repo list on [Repository](http://ubuntuguide.org/#extrarepositories)

---

### Post by clehel on 2005-08-22
Thank you! It seems it did help. I had all repos mentioned in the Ubuntu Guide already, the Marillat was an extra. It seems that even as an extra repository it caused problem. Probably Synaptic picked the Marillat deb package and try to install that, instead of the Ubuntu package?? Thank you again!

---

