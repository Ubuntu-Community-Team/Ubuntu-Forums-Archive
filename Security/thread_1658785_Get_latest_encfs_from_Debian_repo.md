---
title: "Get latest encfs from Debian repo?"
date: 2011-01-03
forum: Security
---

### Post by mark_101 on 2011-01-03
Hi,

I've already asked this on the installation forum but unfortunately doesn't seem to be anyone around who may have the answer there.

I wish to use encfs, however there were several security vulns ([http://seclists.org/fulldisclosure/2010/Aug/316](http://seclists.org/fulldisclosure/2010/Aug/316)) that now seem to have been fixed ([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=595998](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=595998)) in version 1.7.2-1.

It looks like this version will be merged into Natty, however I wish to  use it now on 10.04.  How do I go about getting 1.7.2-1 of encfs from  the debian main?  I'm guessing if I add their repo to my unbuntu 10.04  install then it would cause all kinds of grief with other incorrect  dependencies!  I haven't found any authentic places to download a deb from either.


Many thanks in advance for any guidance on this

Mark

---

### Post by mark_101 on 2011-01-03
ok, quick update.  I managed to find the package here as an rpm - [http://download.fedora.redhat.com/pub/fedora/linux/updates/13/i386/fuse-encfs-1.7.2-1.fc13.i686.rpm](http://download.fedora.redhat.com/pub/fedora/linux/updates/13/i386/fuse-encfs-1.7.2-1.fc13.i686.rpm)

I then converted this with 

alien -k fuse....

Does anyone see any issues with taking a package from redhat?  It seems to have installed just fine?

Cheers

---

### Post by mark_101 on 2011-01-03
I'll close this thread off and move to install questions as there's a dependency issue.

---

