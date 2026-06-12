---
title: "Ubuntu 10.04 Server LTS Security Updates"
date: 2014-11-14
forum: Server Platforms
---

### Post by dlloyd3 on 2014-11-14
I understand that Ubuntu 10.04 Server LTS will continue to receive security updates until April 2015. During installation, the option to have security updates installed automatically was chosen.

Will MySQL and PHP also receive automatic security updates until April 2015? I checked the PHP version and it says "PHP Version 5.3.2-1ubuntu4.28", but isn't PHP 5.3 end of life?

---

### Post by ian-weisser on 2014-11-14
Security updates are not related to the version number.
Most security updates are patched older versions. This is to minimize the number of regressions to operational environments.

The Ubuntu Security Team provides security updates to all packages in the main and restricted repositories. So simply look to see if your package is in 10.04 main or 10.04 restricted or 10.04 security.

Examples:

This package is in -security. It gets security updates from the Ubuntu Security Team.
```
$ rmadison -u ubuntu mysql-client
 mysql-client | 5.1.73-0ubuntu0.10.04.1 | lucid-security   | all
```


This package is not in the 10.04 repositories anymore. This package is not in the main or restricted repositories. It does not get security updates from the Ubuntu Security Team.
```
$ rmadison -u ubuntu xtron
 xtron | 1.1a-14 | lucid/universe   | source, amd64, armel, i386, ia64, powerpc, sparc
 xtron | 1.1a-14 | precise/universe | source, amd64, armel, armhf, i386, powerpc
```

---

