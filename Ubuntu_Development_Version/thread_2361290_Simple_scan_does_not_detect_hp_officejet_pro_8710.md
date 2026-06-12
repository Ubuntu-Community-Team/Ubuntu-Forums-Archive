---
title: "Simple scan does not detect hp officejet pro 8710"
date: 2017-05-14
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2017-05-14
That about sums it up.  Any ideas as what I should do.

Henry

PS Printer is installed and print test was OK.  Set as default.

---

### Post by Hewjr100 on 2017-05-14
Get the following when I run apt-cache policy libsane-hpaio sane-utils.

```
apt-cache policy libsane-hpaio sane-utilslibsane-hpaio:
  Installed: 3.16.11+repack0-2
  Candidate: 3.16.11+repack0-2
  Version table:
 *** 3.16.11+repack0-2 500
        500 http://us.archive.ubuntu.com/ubuntu zesty/main amd64 Packages
        100 /var/lib/dpkg/status
sane-utils:
  Installed: 1.0.25+git20150528-1ubuntu4
  Candidate: 1.0.25+git20150528-1ubuntu4
  Version table:
 *** 1.0.25+git20150528-1ubuntu4 500
        500 http://us.archive.ubuntu.com/ubuntu zesty/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by Hewjr100 on 2017-05-14
Got it fixed.  Re added printer, set as default, and renamed.  Now simple scan works but I cannot remove the first printer that ubuntu auto installed.  How do I remove printer. Right click and delete does nothing.

Henry

---

