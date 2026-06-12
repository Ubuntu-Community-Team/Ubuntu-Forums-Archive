---
title: "Can't get any packages from Synaptic"
date: 2005-03-29
forum: Repositories &amp; Backports
---

### Post by Ghost Freeman on 2005-03-29
Whenever I attempt to download and install a package with Synaptic (running Warty), I get this error saying I need to check the dependencies. I'll use beep-media-player as an example.

```
beep-media-player:
  Depends: libatk1.0-0 (>=1.9.0) but 1.8.0-1ubuntu2 is to be installed
  Depends: libglade2-0 (>=1:2.5.1) but 1:2.4.0-1 is to be installed
  Depends: libglib2.0-0 (>=2.6.0) but 2.4.7-0ubuntu2 is to be installed
  Depends: libgtk2.0-0 (>=2.6.0) but 2.4.10-1ubuntu1 is to be installed
  Depends: libpango1.0-0 (>=1.8.1) but 1.6.0b-0ubuntu1 is to be installed
  Depends: libxml2 (>=2.6.17) but 2.6.11-3ubuntu1.1 is to be installed
```

Here's my sources.list
```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu/ warty main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ warty universe 
deb-src http://archive.ubuntu.com/ubuntu/ warty universe 

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted 

deb http://archive.ubuntu.com/ubuntu/ warty multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ warty multiverse 

deb ftp://ftp.nerim.net/debian-marillat/ stable main 
deb ftp://ftp.nerim.net/debian-marillat/ unstable main 
#deb ftp://ftp.nerim.net/debian-marillat/ testing main 

deb http://ubuntu-bp.sourceforge.net/ubuntu/ warty-backports main universe  

## Enable apt-get wormux

# deb http://download.gna.org/wormux/package/debian/ / 
# deb-src http://download.gna.org/wormux/package/debian/src/ / 

## End enable apt-gen wormux

## Kubuntu


deb http://archive.ubuntu.com/ubuntu/ hoary universe 

#deb http://jasmine.19inch.net/~jr/away/kubuntu/ ./

#KDE Themes
#deb http://debian.neo.pl/wfmh unstable main contrib non-free
```

I was getting help for this in IRC but whoever helped must have abandoned me. That's a first considering the support i've been getting since installing Warty.

I think it should be noted I also did a smart update 24 hours ago, with
```
#deb ftp://ftp.nerim.net/debian-marillat/ testing main
```
uncommented. Not sure if that would have a role in this or not.

Help would be greatly appreciated.

---

### Post by mike998 on 2005-03-29
Drop the backports stuff and change all instances of warty to hoary.
Don't mix and match hoary and warty sources - that's bad. [-X

---

### Post by Ghost Freeman on 2005-03-29
Oops, I forgot I was running Warty. I really need to get some sleep.

Regardless, i'll remove the one entry for Hoary.

---

