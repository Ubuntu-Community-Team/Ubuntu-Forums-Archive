---
title: "PCI-DSS Compliance 12.04"
date: 2013-12-30
forum: Security
---

### Post by adear11 on 2013-12-30
I'm trying to get PCI compliant and the PCI scanning company is flagging our Ubuntu 12.04 PHP 5.3.10-1ubuntu3.9 for CVE-2013-1635 according to [http://people.canonical.com/~ubuntu-security/cve/2013/CVE-2013-1635.html](http://people.canonical.com/~ubuntu-security/cve/2013/CVE-2013-1635.html) the Ubuntu response is "We do not support the user of open_basedir" and all version have been marked as ignored.

I'm at a loss for what to do here. I've point my scanning company to this same URL, but they don't accept that as and answer. 

What should I do?

---

### Post by CharlesA on 2013-12-30
Debian doesn't classify it as a security issue either, but it looks like they patched it in all versions.
[https://security-tracker.debian.org/tracker/CVE-2013-1635](https://security-tracker.debian.org/tracker/CVE-2013-1635)

You can try adding a PPA with an updated package, but that might cause problems down the line.
[http://askubuntu.com/questions/109404/how-do-i-install-latest-php-in-supported-ubuntu-versions-like-5-4-x-in-ubuntu-1](http://askubuntu.com/questions/109404/how-do-i-install-latest-php-in-supported-ubuntu-versions-like-5-4-x-in-ubuntu-1)

---

### Post by adear11 on 2013-12-30
I know Debian, and RedHat for that matter, do not consider this to be a security issue. Unfortunately though, the security assessment company does. One would think that since I am not using open_basedir that this would be a non-issue, but that's not the case either.

At the moment, using a new PPA isn't an option for me. The application I work on has a bunch of legacy code/libraries that do some things (call time pass by reference mostly) that are not allowed in php >= 5.4. So, if the PPA I'm using ever goes beyond php 5.3 I've got problems. As an aside we are working towards migrating all the legacy code either to different libraries or fixing the ones we use to be compatible with 5.4. But that is a ways off from finished and the PCI issue is rather immediate.

Short of convincing the security company that this CVE doesn't apply to me, I'm really at a loss for how to proceed with this.

---

### Post by CharlesA on 2013-12-31
If that's the case, your best bet is probably going to be downloading and compiling php5.3 from php.net.
[http://www.php.net/downloads.php#v5.3.28](http://www.php.net/downloads.php#v5.3.28)

Keep in mind that will mean you need to keep php up to date manually and if 5.3 ever goes end of life and you need to upgrade to php 5.4, you are going to have a major headache.

---

