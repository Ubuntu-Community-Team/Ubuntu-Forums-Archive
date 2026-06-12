---
title: "GHOST Vunerability - Upgrade Glibc from 2.15"
date: 2015-01-28
forum: Security
---

### Post by mcparty2 on 2015-01-28
Hi All,

There is a vulnerability in the news which has been given a fancy name... "GHOST"
[COLOR=#252525][FONT=Verdana]Linux GNU C Library (glibc). This vulnerability enables hackers to remotely take control of systems without even knowing any system IDs or passwords... 
[/FONT][/COLOR]
The link explains it all: [http://www.openwall.com/lists/oss-security/2015/01/27/9](http://www.openwall.com/lists/oss-security/2015/01/27/9)

> "We identified a number of factors that mitigate the impact of this bug. In particular, we discovered that it was fixed on May 21, 2013 (between the releases of glibc-2.17 and glibc-2.18). Unfortunately, it was not recognized as a security threat; as a result, most stable and  long-term-support distributions were left exposed (and still are):   Debian 7 (wheezy), Red Hat Enterprise Linux 6 & 7, CentOS 6 & 7,  Ubuntu 12.04, for example."

I am using Ubuntu 12.04.1 LTS and there appears to be no update available for Glibc.
Can any one help? According to the report we need to be using 2.17 or higher.

```
ldd --version


ldd (Ubuntu EGLIBC 2.15-0ubuntu10.10) 2.15
Copyright (C) 2012 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
Written by Roland McGrath and Ulrich Drepper.

```

Thanks

---

### Post by CharlesA on 2015-01-28
Thanks. Seems Debian has already patched it. Ubuntu probably has as well:

```
Package Details:

Reading changelogs...
--- Changes for eglibc (libc6 libc6-dev libc-bin libc-dev-bin locales multiarch-support) ---
eglibc (2.13-38+deb7u7) wheezy-security; urgency=medium

  * debian/patches/any/cvs-gethostbyname.diff: new patch from upstream
    to fix a buffer overflow in gethostbyname (CVE-2015-0235).
  * debian/patches/any/cvs-iconvdata-ibm930.diff: new patch from upstream to
    fix a possible crash when using the iconv function to convert IBM930
    encoded data (CVE-2012-6656).
  * debian/patches/any/cvs-iconvdata-ibm.diff: new patch from upstream to fix
    fix a possible crash when using the iconv function to convert IBM933, 
    IBM935, IBM937, IBM939, IBM1364 encoded data (CVE-2014-6040).
  * debian/patches/any/cvs-wordexp.diff: new patch from upstream to fix a
    command execution in wordexp() with WRDE_NOCMD specified (CVS-2014-7817).

 -- Aurelien Jarno <aurel32@debian.org>  Tue, 27 Jan 2015 00:38:49 +0100
```

---

### Post by mcparty2 on 2015-01-28
Thanks for this, how can I be sure Ubuntu 12.04 is patched please?

---

### Post by slickymaster on 2015-01-28
> **mcparty2 said:**
> Thanks for this, how can I be sure Ubuntu 12.04 is patched please?

Ubuntu has patched the bug both for 12.04 and the older 10.04. See [here]("http://www.ubuntu.com/usn/usn-2485-1/").

---

### Post by mcparty2 on 2015-01-28
Great, thanks for the re-assurance.

---

### Post by slickymaster on 2015-01-28
You're welcome.

---

