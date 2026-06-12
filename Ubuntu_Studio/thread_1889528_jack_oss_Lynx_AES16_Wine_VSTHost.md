---
title: "jack oss Lynx AES16 Wine VSTHost ?"
date: 2011-12-01
forum: Ubuntu Studio
---

### Post by JuanPabloCuervo on 2011-12-01
Hi,

seems i got a problem...
want to use Lynx AES16 pci soundcard, with Linux.

i have installed KXStudio 10.04 32bit... synaptic etc... because OSS-v4.2-2005-amd64 does not work with 64bit Ubuntu/Kubuntu.
the oss-v4.2-2004-64bit works, but very limited.

installed oss-linux-v4.2-2005 32bit .tar.bz2
Ctrl+Alt+F1
$ login: 
$ pass:
$ cd /
$ sudo tar -jvxf /home/user/Downloads/oss-linux .tar.bz2
$ sudo sh /usr/lib/oss/build/install.sh
reboot
Phenom works.
VLC works.
osstest works.
ossxmix works.
ossinfo is ok.
found a "bug"... {*}Rate Lock in $ossxmix turns on&off the SRC.

modified the /usr/lib/oss/conf/osscore.conf
SRCquality=6 
& stuff like that.

build jack-audio-connection-kit-0.121.3.tar.gz, because it seems jackd 1.9.7 does not support OSS...
$ sudo ./configure --prefix=/usr
$ sudo make
$ sudo make install

configured Wine 1.3.24 "the best build"
installed VSTHost.exe

**here i have 2 problems...**
the Wine OSS MME inputs are not detected by VSTHost.exe ???
&
jackd-0.121.3 does not start...
> 
$ jackd -doss --help
$ jackd -doss -r96000 -p1024 -n2 -w16 -i8 -o8 -C/dev/dsp_in -P/dev/dsp_out

JACK compiled with System V SHM support.
loading driver ..
OSS: failed to open output device /dev/dsp_out: oss_driver.c@514, errno=16
OSS: failed to set fragment size: oss_driver.c@336, errno=9
oss_driver: /dev/dsp_in : 0x10/2/96000 (16384)
oss_driver: indevbuf 16384 B, outdevbuf 4096 B
oss_driver: using barrier mode, (dual thread)

too many consecutive interrupt delays ... engine pausing
delay of 31997.000 usecs exceeds estimated spare time of 10663.000; restart ...
cycle execution failure, exiting:confused:

have also tested: 
/dev/dsp
/dev/dsp_mmap
/dev/des_multich
/dev/oss/lynxtwo0/pcm0 pcmin0 & pcm8

$ ossinfo
...
oss support e-mail  is not much help.

VLC multichannel 5.1/7.1 audio does not work.

any ideas?
different Kernel ?
different OS ?
buy a MAC ?

---

