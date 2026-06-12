---
title: "PHP 5.2.4 and Prior Versions Multiple Vulnerabilities"
date: 2008-03-04
forum: Security Discussions
---

### Post by toniturn on 2008-03-04
Nessus reported mutliple php vulnerabilities when I scanned my server (edgy 6.10, libapache2-mod-php5/edgy uptodate 5.1.6-1ubuntu2.7). When searching for the relevant CVE ids, I came across this page:
[http://www.securityfocus.com/bid/26403](http://www.securityfocus.com/bid/26403)

Is this something to be concerned about, an if so what should one do?
Thanks
toni

---

### Post by cdenley on 2008-03-04
Last I checked, this wasn't patched in Ubuntu. Red Hat and Mandriva apparently don't consider it a security issue, so I'm guessing Ubuntu developers feel the same way. The only reason this would be a problem is if you pass input parameters to the dl function, which would be really stupid.

[http://ubuntuforums.org/showthread.php?t=701574](http://ubuntuforums.org/showthread.php?t=701574)
[http://nvd.nist.gov/nvd.cfm?cvename=CVE-2007-4887](http://nvd.nist.gov/nvd.cfm?cvename=CVE-2007-4887)

---

