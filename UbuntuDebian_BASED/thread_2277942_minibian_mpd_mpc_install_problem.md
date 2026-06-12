---
title: "minibian mpd mpc install problem"
date: 2015-05-12
forum: Ubuntu/Debian BASED
---

### Post by gam01hr on 2015-05-12
Hallo,
I use minibian ([https://minibianpi.wordpress.com/](https://minibianpi.wordpress.com/))  or raspberry pi B board. Everything is OK. Except I want to install mpd and mpc player and I  got dependency problem. Please could you advice me how to solve it. thx.
```
root@raspberrypi:~# apt-get install mpc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.13-38+rpi2+deb7u7) but 2.13-38+rpi2+deb7u8 is to be installed
 mpc : Depends: libmpdclient2 (>= 2.2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@raspberrypi:~#
```
```
root@raspberrypi:~# apt-get install mpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.13-38+rpi2+deb7u7) but 2.13-38+rpi2+deb7u8 is to be installed
 mpd : Depends: libao4 (>= 1.1.0) but it is not going to be installed
       Depends: libasound2 (>= 1.0.16)
       Depends: libaudiofile1 (>= 0.3.4) but it is not going to be installed
       Depends: libavahi-client3 (>= 0.6.16) but it is not going to be installed
       Depends: libavahi-common3 (>= 0.6.16) but it is not going to be installed
       Depends: libavahi-glib1 (>= 0.6.16) but it is not going to be installed
       Depends: libavcodec53 (>= 5:0.8-2~) but it is not going to be installed or
                libavcodec-extra-53 (>= 5:0.8-2~) but it is not going to be installed
       Depends: libavformat53 (>= 5:0.8-2~) but it is not going to be installed
       Depends: libavutil51 (>= 5:0.8-2~) but it is not going to be installed
       Depends: libcurl3-gnutls (>= 7.16.2) but it is not going to be installed
       Depends: libfaad2 (>= 2.7) but it is not going to be installed
       Depends: libflac8 (>= 1.2.1) but it is not going to be installed
       Depends: libglib2.0-0 (>= 2.31.8) but it is not going to be installed
       Depends: libid3tag0 (>= 0.15.1b) but it is not going to be installed
       Depends: libjack-jackd2-0 (>= 1.9.5~dfsg-14) but it is not going to be installed or
                libjack-0.116
       Depends: libmad0 (>= 0.15.1b-3) but it is not going to be installed
       Depends: libmikmod2 (>= 3.1.10) but it is not going to be installed
       Depends: libmms0 (>= 0.4) but it is not going to be installed
       Depends: libmp3lame0 but it is not going to be installed
       Depends: libmpcdec6 (>= 1:0.1~r435) but it is not going to be installed
       Depends: libogg0 (>= 1.1.0) but it is not going to be installed
       Depends: libpulse0 (>= 0.99.1) but it is not going to be installed
       Depends: libsamplerate0 (>= 0.1.7) but it is not going to be installed
       Depends: libshout3 but it is not going to be installed
       Depends: libsqlite3-0 (>= 3.5.9) but it is not going to be installed
       Depends: libvorbis0a (>= 1.1.2) but it is not going to be installed
       Depends: libvorbisenc2 (>= 1.1.2) but it is not going to be installed
       Depends: libvorbisfile3 (>= 1.1.2) but it is not going to be installed
       Depends: libwavpack1 (>= 4.40.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@raspberrypi:~# 
```

---

### Post by sandyd on 2015-05-13
Moved to *Other OS Support and Projects*

---

