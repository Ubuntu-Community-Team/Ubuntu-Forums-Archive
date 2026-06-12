---
title: "PHP Vulnerabilities"
date: 2010-03-29
forum: Security
---

### Post by watfordjc on 2010-03-29
This morning's Comodo HackerGuardian scan suggests that the version of PHP5 installed on my server has multiple vulnerabilities.

```

php --version
PHP 5.2.4-2ubuntu5.10 with Suhosin-Patch 0.9.6.2 (cli) (built: Jan  6 2010 22:01:14)
Copyright (c) 1997-2007 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.4 LTS
Release:        8.04
Codename:       hardy

```

There isn't a later version of PHP5 available in the main Ubuntu Hardy repositories.

Comodo suggest the level of action needed for versions < 5.2.7 is "Urgent" (multiple vulnerabilities) and "Medium Priority" for all versions < 5.3.2/5.2.13.

CVE-2008-2371, CVE-2008-2665, CVE-2008-2666, CVE-2008-2829, CVE-2008-3658, CVE-2008-3659, CVE-2008-3660, CVE-2008-5557, CVE-2008-5624, CVE-2008-5625, CVE-2008-5658, CVE-2007-4850, CVE-2008-0599, CVE-2008-1384, CVE-2008-2050, CVE-2008-2051, CVE-2007-4887, CVE-2007-5898, CVE-2007-5900, CVE-2009-3557, CVE-2009-3558, CVE-2009-4017, CVE-2009-4142, CVE-2009-4143, CVE-2008-5498, CVE-2009-3291, CVE-2009-3292, CVE-2009-3293, CVE-2009-3294, CVE-2009-2687, [http://securityreason.com/achievement_securityalert/82](http://securityreason.com/achievement_securityalert/82)

Is this a false positive, and all those vulnerabilities and flaws have been patched in "5.2.4-2ubuntu5.10 with Suhosin-Patch 0.9.6.2", or is there any plan to make the version of PHP5 available to the LTS Server version of Ubuntu secure?


John.

---

### Post by cdenley on 2010-03-29
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)
[http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.4-2ubuntu5.10/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.4-2ubuntu5.10/changelog)

Those "security scanners" simply look at the version number, and assume it hasn't been patched since that versions official release. However, the previously released version continues to be maintained, and patches are backported to keep it secure.

There have been plenty of security updates added by ubuntu since 5.2.4 was released in August 2007.

---

### Post by watfordjc on 2010-03-29
> **cdenley said:**
> [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)
[http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.4-2ubuntu5.10/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.4-2ubuntu5.10/changelog)

Those "security scanners" simply look at the version number, and assume it hasn't been patched since that versions official release. However, the previously released version continues to be maintained, and patches are backported to keep it secure.

There have been plenty of security updates added by ubuntu since 5.2.4 was released in August 2007.

Thanks for the links.

Thought they were likely false positives but didn't know where to double-check (Google had me going round in circles).


John.

---

