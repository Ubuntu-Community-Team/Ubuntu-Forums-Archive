---
title: "Installing snort from source"
date: 2008-09-16
forum: Security
---

### Post by jba6511 on 2008-09-16
I thought I would make a quick note of some lessons learned when installing snort from scratch. This is based on the install I just went through using a fresh install of hardy. I did not use the repositories due to the dated version of snort available and because of the need to specify options when building snort as I saw fit.

1. download the latest version of snort from snort.org (currently snort-2.8.3.tar.gz)
2. install dependencies: build-essentials
                         libpcap-dev
                         libpcre3-dev
                         flex
3. untar snort: tar -zxvf snort-2.8.3.tar.gz
4. cd snort-2.8.3
5. ./configure (specify additional options during this time based on your needs (IDS, IPS, GRE Tunneling,...) --enable-gre, --enable-perfprofiling, --enable-inline, etc)
6. make
7. sudo make install

You should now be able to test snort to ensure everything installed properly before configuring snort.conf and downloading rules. In this case I just used the following:

sudo snort -i eth0 -dve

I plan to install barnyard, oinkmaster and BASE as well and will try and update with some quick tips later on. Hope this helps someone.

---

### Post by ruik on 2008-09-17
So.. what ./configure options did you use and why?

---

### Post by bodhi.zazen on 2008-09-17
See the sticky at the top of these forums : 

[http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472)

---

### Post by Nullexe on 2009-09-16
Thanks jba6511, I was having issues tracking down the needed dependencies.

---

