---
title: "Installing ZoneMinder"
date: 2013-12-28
forum: Server Platforms
---

### Post by saul4 on 2013-12-28
I need to install ZoneMinder in a headless BSD server. Unfortunately, it currently won't build under FreeBSD. As a workaround I installed Ubuntu Server in a virtual machine.
```
Linux vserver 3.8.0-34-generic #49~precise1-Ubuntu SMP Wed Nov 13 18:08:04 UTC 2013 i686 i686 i386 GNU/Linux
```
I've added the repository:
```
cat /etc/apt/sources.list.d/iconnor-zoneminder-precise.list 
deb http://ppa.launchpad.net/iconnor/zoneminder/ubuntu precise main
```
So far so good. Now I make an attempt to install ZoneMinder:
```
 apt-get install zoneminder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 zoneminder : Depends: libavcodec53 (>= 4:0.8-1~) but it is not going to be installed or
                       libavcodec-extra-53 (>= 4:0.8-1~) but it is not going to be installed
              Depends: libavformat53 (>= 4:0.8-1~) but it is not going to be installed or
                       libavformat-extra-53 (>= 4:0.8-1~) but it is not going to be installed
              Depends: libjpeg8 (>= 8c) but it is not installable
              Depends: libphp-serialization-perl but it is not installable
              Depends: libdate-manip-perl but it is not installable
              Depends: libmime-lite-perl but it is not installable
              Depends: libwww-perl but it is not installable
              Depends: libarchive-zip-perl but it is not installable
              Depends: libdevice-serialport-perl but it is not installable
              Depends: ffmpeg but it is not going to be installed
              Depends: libsys-mmap-perl but it is not installable
              Depends: libjson-any-perl but it is not installable
              Depends: netpbm but it is not installable
              Depends: libavdevice53 but it is not going to be installed
              Depends: zip but it is not installable
              Depends: libnet-sftp-foreign-perl but it is not installable
E: Unable to correct problems, you have held broken packages.
```
This leaves me dry and high. I tried some Google search regarding 'ubuntu server' in conjunction with those packages but couldn't dig up anything useful.

I just need a lean CLI only Linux installation, should I go with Lubuntu and uninstall GUI instead?

---

### Post by volkswagner on 2013-12-28
Did you run apt-get update first?

What does your /etc/apt/sources.list look like?

What happens if you search one of the dependancies?

```
sudo apt-get update
sudo apt-cache search libavcodec53
```

---

### Post by saul4 on 2013-12-28
Thank you for your reply. Methinks I miss a repo. But then again, I stopped using Debian in 2003 (in favor of Gentoo), my apt skills are rusty and probably outdated. Here's the output you requested:
```
root@vserver:~# apt-cache search libavcodec53
libavcodec53 - Libav codec library
root@vserver:~# apt-get install libavcodec53
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libavcodec53 : Depends: libgsm1 (>= 1.0.13) but it is not installable
                Depends: libschroedinger-1.0-0 (>= 1.0.0) but it is not installable
                Depends: libspeex1 (>= 1.2~beta3-1) but it is not installable
                Depends: libtheora0 (>= 1.0) but it is not installable
                Depends: libva1 (> 1.0.15~) but it is not installable
                Depends: libvorbis0a (>= 1.1.2) but it is not installable
                Depends: libvorbisenc2 (>= 1.1.2) but it is not installable
                Depends: libvpx1 (>= 1.0.0) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

```
root@vserver:~# cat /etc/apt/sources.list# 


# deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.2)]/ precise main restricted


#deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release i386 (20130820.2)]/ precise main restricted


deb http://security.ubuntu.com/ubuntu precise-security main
deb-src http://security.ubuntu.com/ubuntu precise-security main
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse


## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by tgalati4 on 2013-12-28
Try installing the dependencies:

tgalati4@Mint14-Extensa ~ $ apt-cache search libavcodec53
libavcodec53 - Libav codec library
tgalati4@Mint14-Extensa ~ $ apt-cache depends libavcodec53
libavcodec53
 |Depends: libavutil51
  Depends: libavutil-extra-51
  Depends: libc6
  Depends: libgsm1
  Depends: libschroedinger-1.0-0
  Depends: libspeex1
  Depends: libtheora0
  Depends: libva1
  Depends: libvorbis0a
  Depends: libvorbisenc2
  Depends: libvpx1
  Depends: zlib1g
  PreDepends: multiarch-support
    multiarch-support:i386
  Conflicts: libavcodec-extra-53
  Conflicts: libavcodec-extra-53:i386
  Breaks: mplayer
  Breaks: mplayer:i386
  Replaces: libavcodec53:i386

---

### Post by saul4 on 2013-12-29
Alright, I installed Ubuntu LTS Precise and stripped it. I was able to install ZoneMinder. I still do not know why Ubuntu Server Precise didn't allow it.

---

