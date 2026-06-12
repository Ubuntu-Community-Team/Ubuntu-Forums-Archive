---
title: "firewall enabled install date"
date: 2015-08-24
forum: Security
---

### Post by jammydodger2 on 2015-08-24
Hi All 
Is there a way to check, when I first enabled/installed my firewall UFW 
as I don,t recall enabling UFW when installing Unbuntu over a year ago(if that option is available)
any help appreciated
JD

---

### Post by untrustytahr on 2015-08-24
The installation date can be retrieved from the ubuntu software center or alternatively from /var/log/dpkg*.  Logrotate has different intervals for different logs but I think dpkg logs are held for 12 months.
As for when it was enabled, I don't know.  Since it requires 'sudo' you could check /var/log/auth*, but I don't think logrotate maintains 12 months on that one.

---

