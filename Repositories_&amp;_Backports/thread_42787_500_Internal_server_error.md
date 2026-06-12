---
title: "500 Internal server error"
date: 2005-06-19
forum: Repositories &amp; Backports
---

### Post by transport on 2005-06-19
What happend with [http://us.archive.ubunu.com?](http://us.archive.ubunu.com?) I instll ubuntu Hoary 5.04 and I need to upgrade any packages. The server says: 500 Internal server error. My sources.list I get from [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by Xian on 2005-06-19
Check that. It should be 'us.archive.ubuntu.com'.

---

### Post by transport on 2005-06-19
**sources.list** 
##deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

**sudo apt-get update** 
samuel@ubuntu:~$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release [26.2kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources [48.4kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release [16.8kB]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Get:7 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages [24.7kB]
Get:8 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages [28.6kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages [490kB]
Get:10 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages [438B]
Get:11 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages [33B]
Get:12 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages [2153B]
Get:13 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages [1735B]
Get:14 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages [33B]
Get:15 [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages [5565B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages [4374B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources [175kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources [1320B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages [2169kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources [857kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages [5437B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages [14B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources [1618B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources [14B]
Fetched 3858kB in 8m56s (7198B/s)
Reading package lists... Done
samuel@ubuntu:~$

**problem**
samuel@ubuntu:~$ sudo apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-mpeg2dec gstreamer0.8-sid gstreamer0.8-swfdec jackd
  liba52-0.7.4 libid3tag0 libjack0.80.0-0 libmad0 libmikmod2 libmpeg2-4
  libsidplay1-c102 libsndfile1 libswfdec0.3
Suggested packages:
  qjackctl jack-tools meterbridge libjackasyn0 sidplay-base xsidplay
The following NEW packages will be installed:
  gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd gstreamer0.8-caca
  gstreamer0.8-festival gstreamer0.8-jack gstreamer0.8-mad gstreamer0.8-mikmod
  gstreamer0.8-mpeg2dec gstreamer0.8-plugins gstreamer0.8-sid
  gstreamer0.8-swfdec jackd liba52-0.7.4 libid3tag0 libjack0.80.0-0 libmad0
  libmikmod2 libmpeg2-4 libsidplay1-c102 libsndfile1 libswfdec0.3
0 upgraded, 22 newly installed, 0 to remove and 48 not upgraded.
Need to get 1119kB/1174kB of archives.
After unpacking 3486kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  liba52-0.7.4 gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-artsd
  gstreamer0.8-caca gstreamer0.8-festival libsndfile1 jackd libjack0.80.0-0
  gstreamer0.8-jack libid3tag0 libmad0 gstreamer0.8-mad libmikmod2
  gstreamer0.8-mikmod libmpeg2-4 gstreamer0.8-mpeg2dec libsidplay1-c102
  gstreamer0.8-sid libswfdec0.3 gstreamer0.8-swfdec gstreamer0.8-plugins
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main liba52-0.7.4 0.7.4-1
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe gstreamer0.8-a52dec 0.8.8-1ubuntu4
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main gstreamer0.8-aa 0.8.8-1ubuntu4
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main gstreamer0.8-artsd 0.8.8-1ubuntu4
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main gstreamer0.8-caca 0.8.8-1ubuntu4
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main gstreamer0.8-festival 0.8.8-1ubuntu4  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libsndfile1 1.0.10-2
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main jackd 0.99.0-2ubuntu1
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libjack0.80.0-0 0.99.0-2ubuntu1
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main gstreamer0.8-jack 0.8.8-1ubuntu4
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libid3tag0 0.15.1b-3
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libmad0 0.15.1b-1
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe gstreamer0.8-mad 0.8.8-1ubuntu4
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libmikmod2 3.1.11-a-6ubuntu2
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main gstreamer0.8-mikmod 0.8.8-1ubuntu4
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libmpeg2-4 0.4.0b-2ubuntu1
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe gstreamer0.8-mpeg2dec 0.8.8-1ubuntu4
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libsidplay1-c102 1.36.59-2
  500 Internal Server Error [IP: 82.211.81.151 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main gstreamer0.8-sid 0.8.8-1ubuntu4
  500 Internal Server Error [IP: 82.211.81.151 80]
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libswfdec0.3 0.3.2-2 [61.2kB]
Fetched 61.2kB in 58s (1044B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/a/a52dec/liba52-0.7.4_0.7.4-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/a/a52dec/liba52-0.7.4_0.7.4-1_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-a52dec_0.8.8-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-a52dec_0.8.8-1ubuntu4_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins0.8/gstreamer0.8-aa_0.8.8-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins0.8/gstreamer0.8-aa_0.8.8-1ubuntu4_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins0.8/gstreamer0.8-artsd_0.8.8-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins0.8/gstreamer0.8-artsd_0.8.8-1ubuntu4_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins0.8/gstreamer0.8-caca_0.8.8-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins0.8/gstreamer0.8-caca_0.8.8-1ubuntu4_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins0.8/gstreamer0.8-festival_0.8.8-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins0.8/gstreamer0.8-festival_0.8.8-1ubuntu4_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/libsndfile1_1.0.10-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/libsndfile1_1.0.10-2_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/j/jack-audio-connection-kit/jackd_0.99.0-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/j/jack-audio-connection-kit/jackd_0.99.0-2ubuntu1_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/j/jack-audio-connection-kit/libjack0.80.0-0_0.99.0-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/j/jack-audio-connection-kit/libjack0.80.0-0_0.99.0-2ubuntu1_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins0.8/gstreamer0.8-jack_0.8.8-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins0.8/gstreamer0.8-jack_0.8.8-1ubuntu4_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libid3tag/libid3tag0_0.15.1b-3_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmad/libmad0_0.15.1b-1_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-mad_0.8.8-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-mad_0.8.8-1ubuntu4_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmikmod/libmikmod2_3.1.11-a-6ubuntu2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmikmod/libmikmod2_3.1.11-a-6ubuntu2_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins0.8/gstreamer0.8-mikmod_0.8.8-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins0.8/gstreamer0.8-mikmod_0.8.8-1ubuntu4_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/m/mpeg2dec/libmpeg2-4_0.4.0b-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/m/mpeg2dec/libmpeg2-4_0.4.0b-2ubuntu1_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-mpeg2dec_0.8.8-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins0.8/gstreamer0.8-mpeg2dec_0.8.8-1ubuntu4_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsidplay/libsidplay1-c102_1.36.59-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsidplay/libsidplay1-c102_1.36.59-2_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins0.8/gstreamer0.8-sid_0.8.8-1ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins0.8/gstreamer0.8-sid_0.8.8-1ubuntu4_i386.deb)  500 Internal Server Error [IP: 82.211.81.151 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
samuel@ubuntu:~$

where is the problem? I dont know.
Network devices is (Edge modem zadacom(Nokia12cable): www. zadacom.sk)
to connect to internet I use **pppd call edge** 
**scripts** 
/etc/ppp/peers/edge

/dev/ttyUSB0 230400
crtscts
user ""
debug
noauth
connect '/usr/sbin/chat -v -f /etc/ppp/chatscripts/edge'
nodetach
noipx
usepeerdns
ipcp-accept-local
local
novj
novjccomp
nobsdcomp
disconnect '/usr/sbin/chat -v -f /etc/ppp/chatscripts/edge-hang'
defaultroute
usepeerdns

/etc/ppp/chatscripts/edge

TIMEOUT 20
ABORT BUSY
ABORT "NO CARRIER"
ABORT VOICE
ABORT "NO DIALTONE"
""
ATZ OK
at+cgdcont=1,"IP","internet" OK
"ATD*99#" CONNECT


/etc/ppp/chatscripts/edge-hang

"" "+++ath"

/etc/ppp/chap-secret /etc/ppp/pap-secret

*[tab]*[tab]""

the web is working fine and ICQ and MSN no problem, I dont know, if works fine IRC, I dont know, if my ip is public.

---

### Post by Xian on 2005-06-19
Let's go on the assumtion that apt is telling the truth.

Try this source list in place of your's.
Rename your current list to serve as a backup.

```
##deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by transport on 2005-06-23
I tried the new sources.list, only ftp servers with ubuntu sources, and works fine.

---

