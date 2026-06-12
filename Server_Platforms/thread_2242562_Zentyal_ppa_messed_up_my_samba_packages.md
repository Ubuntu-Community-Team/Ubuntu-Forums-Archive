---
title: "Zentyal ppa messed up my samba packages"
date: 2014-09-02
forum: Server Platforms
---

### Post by talz13 on 2014-09-02
I was attempting to give zentyal a try on my 12.04 ubuntu server over the long weekend.  I added the zentyal 3.4 PPA to my apt sources.list, and apt-get update'd:

```
deb http://archive.zentyal.org/zentyal 3.4 main extra
```
Couldn't get zentyal to install due to package dependencies.  So I have kind of given up on that for the moment.

Anyways, I ran my usual apt-get update && apt-get dist-upgrade to update my installed packages, and noticed in passing that samba and smbclient were being removed.  I checked the packages afterwards, and yep, they were removed!  I tried to install samba again, to be greeted with:

```
jeff@server:/home/shares/video/unwatched/movie$ sudo apt-get install samba -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 samba : Depends: lsb-base (>= 4.1+Debian) but 4.0-0ubuntu20.3 is to be installed
         Depends: python-samba but it is not going to be installed
         Depends: samba-common-bin (= 2:4.1.6+dfsg-1~zentyal1~106)
         Depends: samba-dsdb-modules but it is not going to be installed
         Depends: sysv-rc (>= 2.88dsf-24) but 2.88dsf-13.10ubuntu11.1 is to be installed or
                  file-rc (>= 0.8.16) but it is not installable
         Depends: libbsd0 (>= 0.5.0) but 0.3.0-2 is to be installed
         Depends: samba-libs (= 2:4.1.6+dfsg-1~zentyal1~106) but it is not going to be installed
         Recommends: attr
         Recommends: samba-vfs-modules but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
jeff@server:/home/shares/video/unwatched/movie$ sudo apt-get remove samba -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package samba is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
jeff@server:/home/shares/video/unwatched/movie$ sudo apt-get dist-upgrade -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libldb1 libtevent0
The following packages have been kept back:
  libsmbclient libsmbclient-dev
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Inst libtevent0 (0.9.15-2 Ubuntu:12.04/precise [amd64])
Inst libldb1 (1:1.1.16-1~ubuntu13.10 Zentyal:archive.zentyal.org [amd64])
Conf libtevent0 (0.9.15-2 Ubuntu:12.04/precise [amd64])
Conf libldb1 (1:1.1.16-1~ubuntu13.10 Zentyal:archive.zentyal.org [amd64])

```

Seems that some samba 4.1.x packages were installed from the zentyal ppa, and cannot be replaced by the 3.6.x packages from the main Ubuntu repo?  How can I fix this?  I've already tried uncommenting / recommenting the zentyal repo line in the sources.list, and apt-get update'ing in between, but cannot figure this out.

---

### Post by talz13 on 2014-09-03
Bump... I can't get Samba reinstalled with this apt / dependency problem persisting.  All my LAN shares are locked away until I can get this fixed...

---

### Post by slickymaster on 2014-09-03
*Moved to the ***Server Platforms*** sub-forum.*

---

### Post by mastablasta on 2014-09-04
surely you weren't testing things in production environment?

also: > The 3.4 version is based on Ubuntu Server 13.10 and is available for 32 and 64 bit architectures ...
from: 
[https://wiki.zentyal.org/wiki/Installation_Guide](https://wiki.zentyal.org/wiki/Installation_Guide)

so since you messed it up would it be terrible if you just installed latest Zentyal on it from scratch (expert mode for no desktop install)? or do you have many stuff pre-setup?

---

### Post by talz13 on 2014-09-04
I think I fixed my package issues... Read up on installing specific versions of packages, and replaced the zentyal packages that were installed with the original ubuntu versions.

First I found all the zentyal packages with:

```
dpkg -l | grep zentyal
```

That showed the offenders (took this after replacing the packages / prior to purging, hence the 'rc' status):

```
jeff@server:/home/shares/video/unwatched/tv$ dpkg -l | grep zentyal
rc  libbind9-90                               2:9.9.3.dfsg.P2-4ubuntu1.1+zentyal12                BIND9 Shared Library used by BIND
rc  libdns99                                  2:9.9.3.dfsg.P2-4ubuntu1.1+zentyal12                DNS Shared Library used by BIND
rc  libisc95                                  2:9.9.3.dfsg.P2-4ubuntu1.1+zentyal12                ISC Shared Library used by BIND
rc  libisccc90                                2:9.9.3.dfsg.P2-4ubuntu1.1+zentyal12                Command Channel Library used by BIND
rc  libisccfg90                               2:9.9.3.dfsg.P2-4ubuntu1.1+zentyal12                Config File Handling Library used by BIND
rc  liblwres90                                2:9.9.3.dfsg.P2-4ubuntu1.1+zentyal12                Lightweight Resolver Library used by BIND
ii  libwbclient0                              2:4.1.6+dfsg-1~zentyal1~106                         Samba winbind client library
rc  samba-common                              2:4.1.6+dfsg-1~zentyal1~106                         common files used by both the Samba server and client
ii  samba-doc                                 2:4.1.6+dfsg-1~zentyal1~106                         Samba documentation
```

I used these packages to determine what to replace, with ```
apt-cache policy <package name>
``` to find the ubuntu package version number.

Then I used these package numbers for each of the applicable packages that were installed from the zentyal ppa:

```
sudo apt-get install bind9-host=1:9.8.1.dfsg.P1-4ubuntu0.8 dnsutils=1:9.8.1.dfsg.P1-4ubuntu0.8 libbind9-80=1:9.8.1.dfsg.P1-4ubuntu0.8 libdns81=1:9.8.1.dfsg.P1-4ubuntu0.8 libisc83=1:9.8.1.dfsg.P1-4ubuntu0.8 libisccc80=1:9.8.1.dfsg.P1-4ubuntu0.8 libisccfg82=1:9.8.1.dfsg.P1-4ubuntu0.8 liblwres80=1:9.8.1.dfsg.P1-4ubuntu0.8
sudo apt-get remove libbind9-90 libdns99 libisc95 libisccc90 libisccfg90 liblwres90
sudo apt-get purge libbind9-90 libdns99 libisc95 libisccc90 libisccfg90 liblwres90

sudo apt-get install libwbclient0=2:3.6.3-2ubuntu2.11 samba-common=2:3.6.3-2ubuntu2.11 samba-doc=2:3.6.3-2ubuntu2.11
sudo apt-get install samba
```

Now, all zentyal packages have been replaced with the ubuntu packages, zentyal versions have been purged, and ubuntu's version of samba has been reinstalled.  I confirmed the removal of all zentyal ppa packages with one last run of ```
dpkg -l | grep zentyal
``` and found no more packages.

I will confirm for myself if the samba service is running and reachable from my windows PCs once I get home tonight.

---

