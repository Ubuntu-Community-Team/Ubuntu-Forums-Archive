---
title: "ClamAV + amavisd-new, lstat() failed"
date: 2009-08-15
forum: Server Platforms
---

### Post by jerz on 2009-08-15
Following [this]("https://help.ubuntu.com/8.04/serverguide/C/mail-filtering.html") guide, I installed mail filtering services. I am fairly positive I configured it correctly, but ClamAV doesn't seem to be working. The mail log shows  "lstat() failed" when attempting to scan emails. This is apparently most likely a permissions problem, however I have added the user 'amavis' to the 'clamav' group, and 'AllowSupplementaryGroups' is set to 'true' in '/etc/clamav/clamd.conf'.

For the time being, I have had to disable virus scanning in amavis.

I am not sure what could be causing virus scanning to fail. Any help is appreciated.

Thanks,
Jeremy

---

### Post by jerz on 2009-08-21
For reference I resolved this by adding the 'clamav' user to the 'amavis' group. The documentation has got it backwards.

---

### Post by cariboo on 2009-08-21
I would suggest you report the error as a bug using the [link]("http://https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs") at the very bottom of the page. If the documentation team doesn't know about the error, it can't be fixed.

---

