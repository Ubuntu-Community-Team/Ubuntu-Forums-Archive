---
title: "apt-get update fails- no repositories problem"
date: 2012-07-06
forum: Server Platforms
---

### Post by pdcc on 2012-07-06
Hi,

I have a server with ubuntu server 11.10 and my apt-get update don't work.
I get this error:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages")  404  Not Found


my sources.list is that:


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main restricted universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted universe$
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# GIS no Ubuntu
deb [http://ppa.launchpad.net/ubuntugis/ppa/ubuntu](http://ppa.launchpad.net/ubuntugis/ppa/ubuntu) natty main
deb-src [http://ppa.launchpad.net/ubuntugis/ppa/ubuntu](http://ppa.launchpad.net/ubuntugis/ppa/ubuntu) natty main
# P.Mapper
deb [http://www.pmapper.net/dl/debian](http://www.pmapper.net/dl/debian) binary/
deb [http://ppa.launchpad.net/georepublic/pgrouting/ubuntu](http://ppa.launchpad.net/georepublic/pgrouting/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/georepublic/pgrouting/ubuntu](http://ppa.launchpad.net/georepublic/pgrouting/ubuntu) oneiric main
deb [http://apt.opengeo.org/ubuntu](http://apt.opengeo.org/ubuntu) lucid main


After i make apt-get clean the apt-get update doens't work and i can't install nothing...

I know that repositories work because i downloaded some deb files with wget..

Anybody can help me please?

thanks

---

### Post by pdcc on 2012-07-06
When i try uninstall anything i'm also get this dpkg erros:

[FONT=monospace]
dpkg: warning: files list file for package `sharutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdbm3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcairo2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libboost-serialization1.42-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `man-db' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libffi6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `module-init-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libflac8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gettext-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libperl5.12' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbus-1-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openssl-blacklist' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libssl1.0.0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gpgv' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `login' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `telnet' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `console-tools-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `expat' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `makedev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `initramfs-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11proto-input-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libisccfg62' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `postgresql-contrib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-shm0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `finger' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `samba' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsysfs2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `debianutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfreetype6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sudo' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `coreutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgl1-mesa-dri' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhdf5-serial-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxdmcp6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpq5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `shared-mime-info' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mktemp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dash' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libltdl-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `opengeo-jai' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `debconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgmpxx4ldbl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `java-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtext-wrapi18n-perl' missing, assuming package has no files currently installed.[/FONT]
[FONT=-moz-fixed][/FONT]

---

### Post by wojox on 2012-07-06
What happens when you run:
```
sudo apt-get -f install
```

---

### Post by pdcc on 2012-07-06
Hi,

Thanks for your help.

root@vm107:/# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@vm107:/#

---

### Post by pdcc on 2012-07-06
all the output of apt-get update:

[http://pastebin.com/jAg8DYtJ](http://pastebin.com/jAg8DYtJ)

---

### Post by wojox on 2012-07-06
woops

---

### Post by wojox on 2012-07-06
Run this in the terminal, then look on your Desktop for it. Upload the attachment for our viewing pleasure. 
```
ls -lR /var/lib/dpkg > ~/Desktop/dpkg-files.txt
```

---

### Post by pdcc on 2012-07-06
My machine is a remote server..
In directory /var/lib/dpkg I execute ls -lR and output was that


total 1752
drwxr-xr-x 2 root root   4096 Jul  5 10:29 alternatives
-rw-r--r-- 1 root root      0 Jul  6 12:48 available
-rw-r--r-- 1 root root 507718 Jul  6 09:15 available-old
-rw-r--r-- 1 root root      9 Feb 17 17:52 cmethopt
-rw-r--r-- 1 root root    334 Jun 12 16:30 diversions
-rw-r--r-- 1 root root    380 Jun 12 16:29 diversions-old
-rw-r--r-- 1 root root      1 Feb 17 17:53 format
drwxr-xr-x 2 root root 118784 Jul  6 13:22 info
-rw-r----- 1 root root      0 Jul  6 13:30 lock
drwxr-xr-x 7 root root   4096 Feb 17 17:55 methods
drwxr-xr-x 2 root root   4096 Feb 17 17:55 parts
-rw-r--r-- 1 root root    165 Feb 17 18:04 statoverride
-rw-r--r-- 1 root root    130 Feb 17 18:04 statoverride-old
-rw-r--r-- 1 root root 550224 Jul  6 13:30 status
-rw-r--r-- 1 root root 550224 Jul  6 13:22 status-old
drwxr-xr-x 2 root root   4096 Jul  5 10:29 triggers
drwxr-xr-x 2 root root   4096 Jul  6 13:30 updates

./alternatives:
total 396
-rw-r--r-- 1 root root   190 Jul  4 23:30 appletviewer
-rw-r--r-- 1 root root   145 Jul  4 23:30 apt
-rw-r--r-- 1 root root   269 Mar 29 19:12 automake
-rw-r--r-- 1 root root   208 Feb 17 17:54 awk
-rw-r--r-- 1 root root    83 Feb 17 17:55 builtins.7.gz
-rw-r--r-- 1 root root   103 Mar  8 16:11 c++
-rw-r--r-- 1 root root   111 Mar  8 16:11 c89
-rw-r--r-- 1 root root   111 Mar  8 16:11 c99
-rw-r--r-- 1 root root   100 Mar  8 16:11 cc
-rw-r--r-- 1 root root    32 Mar  8 16:11 cpp
-rw-r--r-- 1 root root    97 Feb 17 18:04 csh
-rw-r--r-- 1 root root   538 Jun 12 16:30 editor
-rw-r--r-- 1 root root   402 Jun 12 16:30 ex
-rw-r--r-- 1 root root   170 Jul  4 23:30 extcheck
-rw-r--r-- 1 root root  1100 Mar  8 16:11 fakeroot
-rw-r--r-- 1 root root   116 Feb 17 18:02 from
-rw-r--r-- 1 root root   118 Feb 17 18:02 ftp
-rw-r--r-- 1 root root   216 Jun 12 16:30 i386-linux-gnu_gl_conf
-rw-r--r-- 1 root root   150 Jul  4 23:30 idlj
-rw-r--r-- 1 root root   129 Feb 17 18:02 infobrowser
-rw-r--r-- 1 root root   145 Jul  4 23:30 jar
-rw-r--r-- 1 root root   175 Jul  4 23:30 jarsigner
-rw-r--r-- 1 root root   158 Jul  4 23:30 java
-rw-r--r-- 1 root root   155 Jul  4 23:30 javac
-rw-r--r-- 1 root root   165 Jul  4 23:30 javadoc
-rw-r--r-- 1 root root   155 Jul  4 23:30 javah
-rw-r--r-- 1 root root   155 Jul  4 23:30 javap
-rw-r--r-- 1 root root    71 Jul  4 23:30 javaws
-rw-r--r-- 1 root root   170 Jul  4 23:30 jconsole
-rw-r--r-- 1 root root   145 Jul  4 23:30 jdb
-rw-r--r-- 1 root root   152 Jul  4 23:30 jexec
-rw-r--r-- 1 root root   150 Jul  4 23:30 jhat
-rw-r--r-- 1 root root   155 Jul  4 23:30 jinfo
-rw-r--r-- 1 root root   150 Jul  4 23:30 jmap
-rw-r--r-- 1 root root   145 Jul  4 23:30 jps
-rw-r--r-- 1 root root   180 Jul  4 23:30 jrunscript
-rw-r--r-- 1 root root   175 Jul  4 23:30 jsadebugd
-rw-r--r-- 1 root root   160 Jul  4 23:30 jstack
-rw-r--r-- 1 root root   155 Jul  4 23:30 jstat
-rw-r--r-- 1 root root   160 Jul  4 23:30 jstatd
-rw-r--r-- 1 root root   173 Jul  4 23:30 keytool
-rw-r--r-- 1 root root   110 Feb 17 18:04 lft
-rw-r--r-- 1 root root    66 Jul  5 10:29 libblas.so.3gf
-rw-r--r-- 1 root root    69 Jul  5 10:29 liblapack.so.3gf
-rw-r--r-- 1 root root   173 Feb 17 18:03 locate
-rw-r--r-- 1 root root   347 Feb 17 18:04 mailx
-rw-r--r-- 1 root root    98 Feb 17 17:55 mt
-rw-r--r-- 1 root root   190 Jul  4 23:30 native2ascii
-rw-r--r-- 1 root root   117 Jun 12 16:30 net
-rw-r--r-- 1 root root    83 Feb 17 18:02 newt-palette
-rw-r--r-- 1 root root   146 Jun 12 16:30 nmblookup
-rw-r--r-- 1 root root   158 Jul  4 23:30 orbd
-rw-r--r-- 1 root root   173 Jul  4 23:30 pack200
-rw-r--r-- 1 root root   193 Feb 17 18:02 pager
-rw-r--r-- 1 root root   105 Jun 12 16:31 php
-rw-r--r-- 1 root root   140 Jun 12 16:31 php-config
-rw-r--r-- 1 root root   120 Jun 12 16:31 phpize
-rw-r--r-- 1 root root   104 Mar  8 18:18 pico
-rw-r--r-- 1 root root   188 Jul  4 23:30 policytool
-rw-r--r-- 1 root root   712 Jun 12 16:31 postmaster.1.gz
-rw-r--r-- 1 root root 18378 Jun 12 16:31 psql.1.gz
-rw-r--r-- 1 root root   103 Feb 17 18:03 rcp
-rw-r--r-- 1 root root   120 Feb 17 18:04 rename
-rw-r--r-- 1 root root   118 Feb 17 18:03 rlogin
-rw-r--r-- 1 root root   150 Jul  4 23:30 rmic
-rw-r--r-- 1 root root   158 Jul  4 23:30 rmid
-rw-r--r-- 1 root root   193 Jul  4 23:30 rmiregistry
-rw-r--r-- 1 root root   113 Feb 17 17:55 rmt
-rw-r--r-- 1 root root   103 Feb 17 18:03 rsh
-rw-r--r-- 1 root root    44 Jun 12 16:30 rview
-rw-r--r-- 1 root root    43 Jun 12 16:30 rvim
-rw-r--r-- 1 root root   175 Jul  4 23:30 schemagen
-rw-r--r-- 1 root root   357 Feb 17 18:04 sendmail-msp
-rw-r--r-- 1 root root   658 Feb 17 18:04 sendmail-mta
-rw-r--r-- 1 root root   175 Jul  4 23:30 serialver
-rw-r--r-- 1 root root   188 Jul  4 23:30 servertool
-rw-r--r-- 1 root root   147 Jun 12 16:30 smbstatus
-rw-r--r-- 1 root root   162 Feb 17 18:04 tcptraceroute
-rw-r--r-- 1 root root   133 Feb 17 18:03 telnet
-rw-r--r-- 1 root root   142 Jun 12 16:30 testparm
-rw-r--r-- 1 root root   183 Jul  4 23:30 tnameserv
-rw-r--r-- 1 root root   145 Feb 17 18:04 traceproto
-rw-r--r-- 1 root root   205 Feb 17 18:04 traceroute
-rw-r--r-- 1 root root   284 Feb 17 18:04 traceroute6
-rw-r--r-- 1 root root   183 Jul  4 23:30 unpack200
-rw-r--r-- 1 root root   402 Jun 12 16:30 vi
-rw-r--r-- 1 root root   472 Jun 12 16:30 view
-rw-r--r-- 1 root root    42 Jun 12 16:30 vim
-rw-r--r-- 1 root root    46 Jun 12 16:30 vimdiff
-rw-r--r-- 1 root root   107 Feb 17 17:56 w
-rw-r--r-- 1 root root   122 Feb 17 18:02 write
-rw-r--r-- 1 root root   155 Jul  4 23:30 wsgen
-rw-r--r-- 1 root root   170 Jul  4 23:30 wsimport
-rw-r--r-- 1 root root   129 Feb 17 18:04 www-browser
-rw-r--r-- 1 root root   145 Jul  4 23:30 xjc

./info:
total 168
-rw-r--r-- 1 root root   359 Jul  5 10:29 libblas3gf.list
-rw-r--r-- 1 root root   439 Sep  9  2011 libblas3gf.md5sums
-rwxr-xr-x 1 root root   359 Sep  9  2011 libblas3gf.postinst
-rwxr-xr-x 1 root root   132 Sep  9  2011 libblas3gf.postrm
-rwxr-xr-x 1 root root   142 Sep  9  2011 libblas3gf.prerm
-rw-r--r-- 1 root root    59 Sep  9  2011 libblas3gf.shlibs
-rwxr-xr-x 1 root root   378 Sep 10  2011 liblapack3gf.config
-rw-r--r-- 1 root root   365 Jul  5 10:29 liblapack3gf.list
-rw-r--r-- 1 root root   443 Sep 10  2011 liblapack3gf.md5sums
-rwxr-xr-x 1 root root   282 Sep 10  2011 liblapack3gf.postinst
-rwxr-xr-x 1 root root   206 Sep 10  2011 liblapack3gf.postrm
-rwxr-xr-x 1 root root   145 Sep 10  2011 liblapack3gf.prerm
-rw-r--r-- 1 root root    65 Sep 10  2011 liblapack3gf.shlibs
-rw-r--r-- 1 root root  1565 Sep 10  2011 liblapack3gf.templates
-rw-r--r-- 1 root root  2052 Jul  5 10:29 python-gdal.list
-rw-r--r-- 1 root root  3335 Dec  7  2011 python-gdal.md5sums
-rwxr-xr-x 1 root root   345 Dec  7  2011 python-gdal.postinst
-rwxr-xr-x 1 root root   279 Dec  7  2011 python-gdal.preinst
-rwxr-xr-x 1 root root  1215 Dec  7  2011 python-gdal.prerm
-rw-r--r-- 1 root root 23532 Jul  5 10:29 python-numpy.list
-rw-r--r-- 1 root root 32543 Aug 25  2011 python-numpy.md5sums
-rwxr-xr-x 1 root root   189 Aug 25  2011 python-numpy.postinst
-rwxr-xr-x 1 root root   636 Aug 25  2011 python-numpy.preinst
-rwxr-xr-x 1 root root   192 Aug 25  2011 python-numpy.prerm
-rw-r--r-- 1 root root  1346 Jul  5 10:29 python-support.list
-rw-r--r-- 1 root root  1325 May 27  2011 python-support.md5sums
-rwxr-xr-x 1 root root   409 May 27  2011 python-support.postinst
-rwxr-xr-x 1 root root   156 May 27  2011 python-support.postrm
-rwxr-xr-x 1 root root   229 May 27  2011 python-support.prerm
-rw-r--r-- 1 root root    19 May 26  2011 python-support.triggers
-rw-r--r-- 1 root root     0 Jul  6 13:22 wide-dhcpv6-client.list

./methods:
total 20
drwxr-xr-x 2 root root 4096 Feb 17 17:55 disk
drwxr-xr-x 2 root root 4096 Feb 17 17:55 floppy
drwxr-xr-x 2 root root 4096 Feb 17 17:55 ftp
drwxr-xr-x 2 root root 4096 Feb 17 17:55 mnt
drwxr-xr-x 2 root root 4096 Feb 17 17:55 multicd

./methods/disk:
total 0

./methods/floppy:
total 0

./methods/ftp:
total 0

./methods/mnt:
total 0

./methods/multicd:
total 0

./parts:
total 0

./triggers:
total 20
-rw-r--r-- 1 root root 962 Jul  4 23:26 File
-rw------- 1 root root   0 Jul  6 13:30 Lock
-rw-r--r-- 1 root root   0 Jul  5 10:29 Unincorp
-rw-r--r-- 1 root root  15 Mar  8 12:31 cleanup-pkgprepare-updates
-rw-r--r-- 1 root root   9 Jun 12 16:29 ldconfig
-rw-r--r-- 1 root root  15 Jul  5 10:29 pysupport
-rw-r--r-- 1 root root  16 Feb 17 17:55 update-initramfs

./updates:
total 0

---

### Post by wojox on 2012-07-06
Never seen this. Is this a VM or are you behind a proxy?

---

### Post by pdcc on 2012-07-06
It is a VM...

I don't know what to do...

---

### Post by wojox on 2012-07-06
> **pdcc said:**
> It is a VM...

I don't know what to do...

Me either. I don't have much experince with VM's. Nice thing is you can wipe them out and start over. :p

---

### Post by pdcc on 2012-07-06
the output of apt-get update also have this:


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by pdcc on 2012-07-06
Nobody have an ideia?

---

### Post by pdcc on 2012-07-06
If i try reinstall dpkg like that:

apt-get install --reinstall dpkg 

i get this error:

Reinstallation of dpkg is not possible, it cannot be downloaded.

---

