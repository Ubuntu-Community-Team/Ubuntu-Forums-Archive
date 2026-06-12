---
title: "PHP &quot;rfc822_write_address()&quot; Function Buffer Overflow Vulnerability - Zero Day"
date: 2008-12-08
forum: Security
---

### Post by snowpalmer on 2008-12-08
We are running ubuntu server 8.04 and are trying to become PCI compliance. There is a compliance check created by Qualys that keeps failing this server because of this rfc822_write_address() problem. From what I can tell the problem has not been fixed by PHP, and isn't patched under any other distribution of PHP. Has anyone else run into this? Anyone else gone under PCI compliance that might had some advice?

Here is some more information.

```

THREAT:
PHP is prone to a buffer overflow vulnerability because it fails to perform boundary checks before copying user-supplied data to insufficiently sized
memory buffers.
Affected versions:
PHP 5.2 - 5.2.6
PHP 5.1 - 5.1.6
PHP 5.0 - 5.0.5
IMPACT:
Exploitation of this issue may allow an attacker to execute arbitrary machine code in the context of the affected Web server. Failed attempts will
likely cause a denial of service condition on the Web server.
SOLUTION:
There are no vendor-supplied patches available at this time.

```

---

### Post by cdenley on 2008-12-08
I'm not sure about any standards or Qualsys, but that bug appears to have been fixed in ubuntu.
[http://www.ubuntu.com/usn/usn-628-1](http://www.ubuntu.com/usn/usn-628-1)
[http://www.securityfocus.com/bid/29829](http://www.securityfocus.com/bid/29829)
Is Qualsys actually checking for vulnerabilities, or is it checking the version of your software. Ubuntu hardy may have PHP 5.2.4, but it has many patches that were included in newer releases.
[http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.4-2ubuntu5.3/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.4-2ubuntu5.3/changelog)

---

### Post by snowpalmer on 2008-12-08
Thanks for the information. I'm assuming that Qualsys is just checking the version against a database of vulnerabilities. I'll get this information to our sysadmin to see if he can check those off the list.

There are a couple more that I'm trying to find fixes listed for like:

PHP "safe_mode" Multiple Security Bypass Vulnerabilities - Zero Day
CVE-2008-2666, CVE-2008-2665

AND

Apache 2.2 Multiple Vulnerabilities
CVE-2007-6420, CVE-2008-2364

But I'm not finding them on the search on ubuntu.com or google. Well, I find a note about the Apache one on a mailing list, but not an official announcement like you provided. What's the best way to find these? Is there a one-stop place that lists all of the security patches?

Nathan

---

### Post by cdenley on 2008-12-08
> **snowpalmer said:**
> 
Is there a one-stop place that lists all of the security patches?

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

Unfortunately, I don't see those bugs mentioned there, or the package's changelog. I did find something about the last bug being "in progress".
[https://bugs.launchpad.net/bugs/cve/2008-2364](https://bugs.launchpad.net/bugs/cve/2008-2364)
It could be possible that some bugs were fixed by another patch. I know sometimes ubuntu developers don't consider things worth patching since the vulnerability can't be exploited unless it isn't properly configured. Or maybe someone patched it without giving a CVE reference. I know I have had to actually review the source code before to verify there wasn't a vulnerability in a package.

---

