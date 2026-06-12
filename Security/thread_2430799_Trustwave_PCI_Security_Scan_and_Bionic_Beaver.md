---
title: "Trustwave PCI Security Scan and Bionic Beaver"
date: 2019-11-07
forum: Security
---

### Post by jmurtari on 2019-11-07
Folks,

Trying to solve some problems with a Trustwave security scan done on one of our servers. The server failed because of an apache issue, CVE-2019-0211.

The server uses just the ubuntu repositories and is currently on 2.4.29 - actual package  2.4.29-1ubuntu4.11 
I checked the Ubuntu site and they report a backported fix in 2.4.29 in package 2.4.9-1ubunut4.6

So we should be good, trouble is the Trustwave scanner just looks at the version reported by Apache
and it wants to see at least 2.4.39

Now we can inhibit Apache from reporting version info, that would quiet the scan...  I also know I can add another
repository and bring the system up to a current apache 2.4.41, but we like to keep things just on Ubuntu.

So.... I know this must be affecting other installations.  Is there a way Ubuntu can just update the Apache version
to the latest from their distribution sites?

Thanks!
John

---

### Post by johnarnold on 2019-11-09
It's really important to inhibit Apache from reporting the version. You are making it way too easy for hackers if you provide such information - they can look up known vulnerabilities in an instant.

---

### Post by TheFu on 2019-11-11
Perhaps opening a bug with Trustwave about recognizing Ubuntu backported fixes would be good?

---

