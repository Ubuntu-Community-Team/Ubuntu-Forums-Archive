---
title: "Request - lsb 3.0.10 (or .11)"
date: 2005-11-24
forum: Requests
---

### Post by dcstar on 2005-11-24
Current lsb init-functions script does not contain the new **log_daemon_msg** function.

The new ClamAV 0.87.1 scripts now call this function, but it ain't there in the current package.......

The Debian changelog says that this function should now be used instead of some of the existing ones:

[http://packages.debian.org/changelogs/pool/main/l/lsb/lsb_3.0-11/changelog](http://packages.debian.org/changelogs/pool/main/l/lsb/lsb_3.0-11/changelog)

---

### Post by FrostByghte on 2005-12-04
Also noticed this on my install.  :(

---

### Post by Bil-E-daKid on 2005-12-05
Yep - and mine.   :-)

---

### Post by pcatiprodotnet on 2005-12-17
Does anyone have a fix / work-around to get log_daemon_msg command working in Ubuntu?

---

### Post by dpm on 2006-01-25
Same problem here.

See dcstar's suggestion for a workaround:

[http://www.ubuntuforums.org/showpost.php?p=640468&postcount=4]("http://www.ubuntuforums.org/showpost.php?p=640468&postcount=4")

Cheers

---

