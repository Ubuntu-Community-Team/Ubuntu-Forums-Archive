---
title: "Intel atom processor giving me problems"
date: 2008-09-16
forum: Server Platforms
---

### Post by zebog13 on 2008-09-16
So I have this mini-box ([www.mini-box.com](www.mini-box.com)) with the new Intel Atom processor. I tried installing Hardy Server 8.04, but it dumped. A co-worker took it, and  had to update the kernel to version 22 to get clean support for the NIC card.

So I got the box back, and tried to install something (doesn't matter because all installations produce same error), it says "Depends: ____ but it is not going to be installed ... Depends: storage-core-modules-2.6.24-22-generic-di but it is not going to be installed E:Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)"

I ran apt-get -f install, it tries to install storage-core-modules-2.6.24-22-generic-di: But I get "E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas will be greatful

---

### Post by hrod beraht on 2008-09-16
Interestingly, I just happened to be reading an [[COLOR="Blue"]Intel page about the D945GCLF Atom motherboard[/COLOR]]("http://www.intel.com/support/motherboards/desktop/d945gclf/sb/CS-029475.htm").

Apparently, 8.04 with the 2.6.24-16-generic kernel is definitely a no-go with the LAN. But, it says that 8.04.1 with the 2.6.24-19-generic kernel has native support.

Have you tried the 8.04.1 version?

Bob

---

### Post by zebog13 on 2008-09-16
> **hrod beraht said:**
> 
Apparently, 8.04 with the 2.6.24-16-generic kernel is definitely a no-go with the LAN. But, it says that 8.04.1 with the 2.6.24-19-generic kernel has native support.

Have you tried the 8.04.1 version?



Yes. With the 22 kernel. Co-worker says it's a waste of time, we'll just wait for the next version of ubuntu that supports it. :lolflag: I don't doubt 19 kernel works.

---

### Post by cdenley on 2008-09-16
> **zebog13 said:**
> Yes. With the 22 kernel. Co-worker says it's a waste of time, we'll just wait for the next version of ubuntu that supports it. :lolflag: I don't doubt 19 kernel works.

It sounds like your packaging system is broken. That package your error mentioned is only for installers. You shouldn't have anything installed that depends on it. I would start over with an 8.04.1 installation CD.

---

### Post by inphektion on 2008-09-16
Yea you def are doing something inherently wrong as we have about 5 system here built from the D945GCLF Atom motherboard.
all installed perfectly with 8.04.1 desktop i386 disk.

---

### Post by Thomaseov on 2008-10-03
> **inphektion said:**
> Yea you def are doing something inherently wrong as we have about 5 system here built from the D945GCLF Atom motherboard.
all installed perfectly with 8.04.1 desktop i386 disk.

exactly, the problem is using an 8.04 vs 8.04.1 installer.  Download 8.04.1 and you are good to go.  I had same problem.

Thomas

---

### Post by zebog13 on 2008-10-13
Same box so same thread.
<quote> q
sudo pecl install pecl_http
sudo: unable to resolve host mindsightatom
[sudo] password for administrator:
downloading pecl_http-1.6.1.tgz ...
Starting to download pecl_http-1.6.1.tgz (172,539 bytes)
.....................done: 172,539 bytes
71 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20060613
Zend Extension Api No:   220060519
configure.in:77: warning: LTOPTIONS_VERSION is m4_require'd but not m4_defun'd
aclocal.m4:2912: LT_INIT is expanded from...
aclocal.m4:2947: AC_PROG_LIBTOOL is expanded from...
configure.in:77: the top level
configure.in:77: warning: LTSUGAR_VERSION is m4_require'd but not m4_defun'd
configure.in:77: warning: LTVERSION_VERSION is m4_require'd but not m4_defun'd
configure.in:77: warning: LTOBSOLETE_VERSION is m4_require'd but not m4_defun'd
configure:10356: error: possibly undefined macro: m4_ifval
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure:12892: error: possibly undefined macro: _LT_SET_OPTIONS
configure:12892: error: possibly undefined macro: LT_INIT
ERROR: `phpize' failed
</quote>

Running
Ubuntu intrepid (development branch) \n \l

---

### Post by zebog13 on 2008-10-16
didn;t install libcurl3-dev

---

