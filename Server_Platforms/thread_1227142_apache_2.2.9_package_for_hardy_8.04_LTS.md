---
title: "apache 2.2.9 package for hardy 8.04 LTS?"
date: 2009-07-30
forum: Server Platforms
---

### Post by phlipdascrip on 2009-07-30
Hi all, I've been searching quite a bit to no avail. are there plans for releasing an apache 2.2.9 package for "hardy" 8.04 LTS? i'd like to update apache to 2.2.9 but the latest available package on hardy is 2.2.8. any specific reason for it?
cheers

---

### Post by cdenley on 2009-07-30
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)

Any specific reason you want 2.2.9?

---

### Post by phlipdascrip on 2009-07-30
actually I just need higher than 2.2.8 because of security issues fixed with 2.2.9. 2.2.9 and 2.2.11 are available as metapackages to intrepid and jaunty, karmic respectively:
[http://packages.ubuntu.com/search?keywords=apache2&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=apache2&searchon=names&exact=1&suite=all&section=all)

it would be great to know if and when a package higher than 2.2.8 is going to be released for hardy. anyone happen to have a clue?

---

### Post by cdenley on 2009-07-30
There will probably never be an apache-2.2.9 or apache-2.2.11 package built for hardy. What security vulnerability are you worried about, and what makes you think ubuntu's 2.2.8-1ubuntu0.10 package doesn't have it patched already?

[http://www.ubuntu.com/usn/USN-802-1](http://www.ubuntu.com/usn/USN-802-1)
[http://www.ubuntu.com/usn/usn-787-1](http://www.ubuntu.com/usn/usn-787-1)

---

### Post by phlipdascrip on 2009-07-30
[http://httpd.apache.org/security/vulnerabilities_22.html](http://httpd.apache.org/security/vulnerabilities_22.html)
CVE-2007-6420, CVE-2008-2364 (fixed in 2.2.9)
CVE-2009-1195 (fixed in 2.2.12) (referenced in your second link)

A security assessment brought them up and suggested updating apache as a fix, but in fact I was a bit quick to go with that and look into updating apache because the two modules that are affected by the first two vulnerabilities (mod_proxy_balancer, mod_proxy_http) are not needed on my server in question. you've helped me anyway and maybe this topic helps others in simliar situations too.
thanks for your competent and quick replies!

---

### Post by cdenley on 2009-07-30
CVE-2007-6420,CVE-2008-2364: fixed in 2.2.8-1ubuntu0.5
[http://www.ubuntu.com/usn/USN-731-1](http://www.ubuntu.com/usn/USN-731-1)
CVE-2009-1195: fixed in 2.2.8-1ubuntu0.8
(as indicated by my second link above)

Just because the official 2.2.8 release from apache has had security vulnerabilities discovered in it since doesn't mean the ubuntu package maintainers haven't patched the most current 2.2.8 packages in the repos.

---

### Post by phlipdascrip on 2009-07-30
i see, good to know. cheers!

---

