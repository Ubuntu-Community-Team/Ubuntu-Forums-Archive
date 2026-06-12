---
title: "Feisty proftpd from repsitory is vulnerable"
date: 2008-09-27
forum: Security
---

### Post by beniji on 2008-09-27
WARNING TO ANYONE RUNNING proftpd ON FEISTY:

One of my fully up to date feisty servers (NB feisty is still supported until next month) got hacked due to a bug known in proftpd since April 2007.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=419255](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=419255)

It looks to me that Debian Sarge was patched in January 2008 but Feisty's official version remains vulnerable even now, whilst Gutsy/Hardy are ok.

proftpd is in universe and therefore officially unsupported by the security team but this is still a biggie in my opinion.

feisty: 1.3.0-21ubuntu1 VULNERABLE
gutsy: 1.3.0-24ubuntu1
hardy: 1.3.1-6ubuntu1

feisty changelog does not include the required patch:
[http://changelogs.ubuntu.com/changelogs/pool/universe/p/proftpd-dfsg/proftpd-dfsg_1.3.0-21ubuntu1/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/p/proftpd-dfsg/proftpd-dfsg_1.3.0-21ubuntu1/changelog)

Beniji

---

