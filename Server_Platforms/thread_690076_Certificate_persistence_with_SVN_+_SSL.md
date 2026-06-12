---
title: "Certificate persistence with SVN + SSL"
date: 2008-02-07
forum: Server Platforms
---

### Post by steenbras on 2008-02-07
I've configured an Apache server to use an OpenSSL certificate, and when I try to use svn with an https:// URL I am prompted, as expected, to
```
 (R)eject, accept (t)emporarily or accept (p)ermanently? p
```

The problem is, accepting permanently doesn't accept it permanently; the very next time I issue an SVN command on the repository, I'm prompted again.

It should be noted that this is on an ssh shell into a Gutsy server - the repository is on another Gutsy server.

On my Gutsy workstation, I get a different issue - I don't even get given the option to accept the certificate permanently.

How can I overcome these issues?

---

