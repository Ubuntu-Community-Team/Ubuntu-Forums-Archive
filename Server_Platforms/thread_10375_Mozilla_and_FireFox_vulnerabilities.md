---
title: "Mozilla and FireFox vulnerabilities"
date: 2005-01-07
forum: Server Platforms
---

### Post by nocturn on 2005-01-07
I just read in The Register that there were flaws discovered in Mozilla and FireFox.

The article is here:
[http://www.theregister.co.uk/2005/01/07/mozilla_flaws/](http://www.theregister.co.uk/2005/01/07/mozilla_flaws/)

It describes a buffer overflow in the NNTP components of the Mozilla products, affecting Mozilla <= 1.7.5 and FireFox < 1.0.

The second flaw affects FireFox <= 1.0, it seems it is possible to spoof the source of downloads in the download dialog.  

The third one only affects FireFox and Thunderbird and is exploitable locally only.  It seems insecure temporary files can allow users to see the downloads and attachments of other users on the system.

---

### Post by jdong on 2005-01-07
Some of them don't have patches/fixes yet. I filed a bug report on one of the issues.

---

