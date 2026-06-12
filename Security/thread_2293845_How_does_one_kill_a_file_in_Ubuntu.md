---
title: "How does one kill a file in Ubuntu?"
date: 2015-09-08
forum: Security
---

### Post by david434 on 2015-09-08
I just want to get rid of a file.  Is it possible?  I cannot open the one in question, and Clamav says it is infected........................./usr/share/mime/mime.cache      PUA.Win.Exploit.CVE_2012_0110

---

### Post by CharlesA on 2015-09-08
Read these please:
[http://ubuntuforums.org/showthread.php?t=2274088](http://ubuntuforums.org/showthread.php?t=2274088)
[http://askubuntu.com/questions/611291/pua-win-exploit-cve-2012-0110-found](http://askubuntu.com/questions/611291/pua-win-exploit-cve-2012-0110-found)

---

### Post by david434 on 2015-09-08
Thanks!

---

### Post by maglin2 on 2015-09-09
As others have commented elsewhere, this detection is present even on a fresh install/livecd. Unless Canonical have taken to gratuitously shipping windows malware it is a false positive. I have reported it to ClamAV, however their response is that they do not currently consider it to be a false positive. I guess what is considered a PUA is necessarily context related.

---

