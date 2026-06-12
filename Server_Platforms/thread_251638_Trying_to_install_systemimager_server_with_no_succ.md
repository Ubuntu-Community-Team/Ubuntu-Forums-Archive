---
title: "Trying to install systemimager server with no success...."
date: 2006-09-05
forum: Server Platforms
---

### Post by kenquad on 2006-09-05
Hi all:

I'm trying to install system imager server on Ubuntu 6.06 Dapper, having added "deb [http://download.systemimager.org/debian](http://download.systemimager.org/debian) stable main" to my /etc/apt/sources.list.  (It gives me an unknown public key error but lets me overrid it.  Here's the output:

Reading package lists...
Building dependency tree...
The following extra packages will be installed:
  binutils libc6 libc6-i686 libdb4.4 libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl liburi-perl libwww-perl libxml-libxml-common-perl
  libxml-libxml-perl libxml-namespacesupport-perl libxml-parser-perl
  libxml-sax-perl libxml-simple-perl mkisofs mtools perl perl-base
  perl-modules systemimager-boot-i386-standard tzdata
Suggested packages:
  binutils-doc glibc-doc libio-socket-ssl-perl cdrecord cdrtools-doc floppyd
  libterm-readline-gnu-perl libterm-readline-perl-perl
Recommended packages:
  libmailtools-perl libhtml-format-perl libcompress-zlib-perl perl-doc
  dhcp3-server dhcp syslinux
The following NEW packages will be installed:
  binutils libdb4.4 libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  liburi-perl libwww-perl libxml-libxml-common-perl libxml-libxml-perl
  libxml-namespacesupport-perl libxml-parser-perl libxml-sax-perl
  libxml-simple-perl mkisofs mtools systemimager-boot-i386-standard
  systemimager-server tzdata
The following packages will be upgraded:
  libc6 libc6-i686 perl perl-base perl-modules
5 upgraded, 18 newly installed, 0 to remove and 167 not upgraded.
Need to get 34.5MB of archives.
After unpacking 47.7MB of additional disk space will be used.
Do you want to continue [Y/n]? WARNING: The following packages cannot be authenticated!
  perl-modules tzdata libc6 libc6-i686 perl-base perl binutils mtools
  libhtml-tagset-perl liburi-perl libhtml-parser-perl libhtml-tree-perl
  libwww-perl libxml-simple-perl mkisofs systemimager-boot-i386-standard
  systemimager-server
Install these packages without verification [y/N]? Err [http://download.systemimager.org](http://download.systemimager.org) stable/main perl-modules 5.8.8-4
  404 Not Found
Err [http://download.systemimager.org](http://download.systemimager.org) stable/main tzdata 2006c-2
  404 Not Found
Err [http://download.systemimager.org](http://download.systemimager.org) stable/main libc6 2.3.6-7
  404 Not Found
Err [http://download.systemimager.org](http://download.systemimager.org) stable/main libc6-i686 2.3.6-7
  404 Not Found
Err [http://download.systemimager.org](http://download.systemimager.org) stable/main perl-base 5.8.8-4
  404 Not Found
Err [http://download.systemimager.org](http://download.systemimager.org) stable/main perl 5.8.8-4
  404 Not Found
Err [http://download.systemimager.org](http://download.systemimager.org) stable/main binutils 2.16.1cvs20060413-1
  404 Not Found
Err [http://download.systemimager.org](http://download.systemimager.org) stable/main mtools 3.9.10.ds1-1
  404 Not Found
Err [http://download.systemimager.org](http://download.systemimager.org) stable/main libhtml-tagset-perl 3.10-2
  404 Not Found
Err [http://download.systemimager.org](http://download.systemimager.org) stable/main liburi-perl 1.35-2
  404 Not Found
Err [http://download.systemimager.org](http://download.systemimager.org) stable/main libhtml-parser-perl 3.54-1
  404 Not Found
Err [http://download.systemimager.org](http://download.systemimager.org) stable/main libhtml-tree-perl 3.19.01-2
  404 Not Found
Err [http://download.systemimager.org](http://download.systemimager.org) stable/main libwww-perl 5.805-1
  404 Not Found
Err [http://download.systemimager.org](http://download.systemimager.org) stable/main libxml-simple-perl 2.14-4
  404 Not Found
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe libdb4.4 4.4.20-4build1 [437kB]
Err [http://download.systemimager.org](http://download.systemimager.org) stable/main mkisofs 4:2.01+01a03-5
  404 Not Found
Get:2 [http://download.systemimager.org](http://download.systemimager.org) stable/main systemimager-boot-i386-standard 3.6.2-2 [16.2MB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libxml-libxml-common-perl 0.13-5 [14.0kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libxml-namespacesupport-perl 1.09-2 [15.2kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libxml-sax-perl 0.12-5 [79.5kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libxml-libxml-perl 1.58-3 [273kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main libxml-parser-perl 2.34-4 [292kB]

With my limited experience, I would say this is a dependency issue.  But I really don't know.  Any help would be appreciated.

---

### Post by Glut on 2006-09-06
The only packages available on that server seem to be the systemimager ones. It's searching for others, but they're not there. The reason it's not using the ubuntu available packages is that the ubuntu packages are older versions. I'd be lying if I said I know an easy way out, without using a debian repository (which is a can of worms I'm not touching)

---

### Post by kenquad on 2006-09-06
What if I were to try an older version of systemimager?  I don't care about having the latest-greatest.  Would that maybe help?

---

