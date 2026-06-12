---
title: "debian-marillat configuration"
date: 2005-04-10
forum: The Cafe
---

### Post by emmanuel on 2005-04-10
Hello,

(running hoary)
I added debian-marillat to my repositories to get mplayer/mencoder, libdvdcss and many codecs. However I'm having problems to upgrade today. I'm not sure I configured it well.

apt-get says:
mplayer-nogui:
 Depends: libavcodeccvs (>=2:20050409-0sarge0.0) but 2:20050331-0.4 is to be installed
 Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
 Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed 

I said i want debian-marillat "testing" (sarge) but now upgrade is broken due to too recent fontconfig and vorbis dependencies. i tried to write all three marillat repositories (stable/testing/unstable), it would change some of my packages but doesn't fix this problem.

Should I use multiverse instead of marillat? or additionnally to marillat? this using several repositories potentially containing the same package really confuses me, it's really super smart to work at all...
What is the config that modifies the least the default config files _and_ adds dvd playing and non-free codecs with the least hassle? I tried adding multiverse/all three marillat branches to get like on ubuntuguide.org but it didn't help that particular problem.

Too bad there is not straight ubuntu package for that (I saw one once but only for Warty).

Any insight appreciated!

here is my sources.list:
------------------------

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050310)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://si.archive.ubuntu.com/ubuntu](http://si.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://si.archive.ubuntu.com/ubuntu](http://si.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://si.archive.ubuntu.com/ubuntu](http://si.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://si.archive.ubuntu.com/ubuntu](http://si.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://si.archive.ubuntu.com/ubuntu](http://si.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://si.archive.ubuntu.com/ubuntu](http://si.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

---

### Post by humanity_to_others on 2005-04-10
In Hoary, you don't need marillat for mplayer.

---

