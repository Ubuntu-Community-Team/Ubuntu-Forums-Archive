---
title: "Why squid3 not come enable-arp-acl ?"
date: 2010-05-04
forum: Server Platforms
---

### Post by tadeucruz on 2010-05-04
Why squid3 not come enable-arp-acl ? 

root@cache01:/etc/squid3# apt-cache policy squid3
squid3:
  Instalado: 3.0.STABLE1-1ubuntu1
  Candidato: 3.0.STABLE1-1ubuntu1
  Tabela de versÃ£o:
 *** 3.0.STABLE1-1ubuntu1 0
        500 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) hardy/universe Packages
        100 /var/lib/dpkg/status

root@cache01:/etc/squid3# lsb_release -rd
Description:    Ubuntu 8.04.4 LTS
Release:        8.04

root@cache01:/etc/squid3# squid3 -v
Squid Cache: Version 3.0.STABLE1
configure options:  '--build=x86_64-linux-gnu' '--prefix=/usr' '--includedir=${prefix}/include' '--mandir=${prefix}/share/man' '--infodir=${prefix}/share/info' '--sysconfdir=/etc' '--localstatedir=/var' '--libexecdir=${prefix}/lib/squid3' '--disable-maintainer-mode' '--disable-dependency-tracking' '--srcdir=.' '--datadir=/usr/share/squid3' '--sysconfdir=/etc/squid3' '--mandir=/usr/share/man' '--with-cppunit-basedir=/usr' '--enable-inline' '--enable-async-io=8' '--enable-storeio=ufs,aufs,coss,diskd' '--enable-removal-policies=lru,heap' '--enable-poll' '--enable-delay-pools' '--enable-cache-digests' '--enable-snmp' '--enable-htcp' '--enable-select' '--enable-carp' '--enable-large-files' '--enable-underscores' '--enable-icap-client' '--enable-auth=basic,digest,ntlm' '--enable-basic-auth-helpers=LDAP,MSNT,NCSA,PAM,SASL,SMB,YP,getpwnam,multi-domain-NTLM' '--enable-ntlm-auth-helpers=SMB' '--enable-digest-auth-helpers=ldap,password' '--enable-external-acl-helpers=ip_user,ldap_group,session,unix_group,wbinfo_group' '--with-filedescriptors=65536' '--with-default-user=proxy' '--enable-epoll' '--enable-linux-netfilter' 'build_alias=x86_64-linux-gnu' 'CC=cc' 'CFLAGS=-g -O2 -g -Wall -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CXX=g++' 'CXXFLAGS=-g -O2 -g -Wall -O2' 'FFLAGS=-g -O2'

Thanks.

---

### Post by cdenley on 2010-05-04
I think that may have been removed a long time ago as a workaround for a bug.
> 
Changes to squid-2.5.STABLE5 (1 Mar 2004):
	...
	- Bug #729: --enable-arp-acl may give warning about net/route.h

[http://bugs.squid-cache.org/show_bug.cgi?id=729](http://bugs.squid-cache.org/show_bug.cgi?id=729)

It looks like that compile option is used for karmic and lucid.
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=538023](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=538023)
[http://changelogs.ubuntu.com/changelogs/pool/universe/s/squid3/squid3_3.0.STABLE18-1/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/s/squid3/squid3_3.0.STABLE18-1/changelog)
> 
squid3 (3.0.STABLE18-1) unstable; urgency=high

  * New upstream release
    - Removed patches integrated upstream
      + 12-gcc44-fixes
      + 13-signed-unsigned-fixes
      + SQUID-2009-2

  * debian/rules
    **- Enable ARP ACLs (Closes: #538023)**
    - Enable SNMP support (Closes: #537187)

  * debian/control
    - Fix dependency for squid3-dbg on squid3 =${binary:Version}
    - Added dependency of squid3-dbg on ${misc:Depends}

  * debian/squid3-common.postinst
    - Added DEBHELPER placeholder

 -- Luigi Gangitano <luigi@debian.org>  Sun, 09 Aug 2009 00:28:56 +0200



I seriously doubt that compile options are going to be added for hardy.
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

---

