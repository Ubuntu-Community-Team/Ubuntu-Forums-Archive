---
title: "O/S level auditing"
date: 2009-07-22
forum: Security
---

### Post by whtabtbill on 2009-07-22
Hello everyone!  Please be gentle as this is my first foray into Ubuntu :-)  I have a customer whose security team requires system and application auditing in order for a system to be accreditation.  I'm setting up apparmor to manage the applications, but I can't seem to find something that gives me the ability to log changes made within the O/S.  Is there something I can use (freeware or otherwise) that can address this need?  If I need to give more details, please let me know.

---

### Post by The Tronyx on 2009-07-22
You would want to use a host intrusion detection system or similar tool to look for file/system changes in the specified location.  You might want to look into OSSEC.  There is a sticky regarding OSSEC setup on the top of the forums - it's in the Snort thread.

---

### Post by sasho_zl on 2009-07-22
Well OSSEC Host Intrusion Detection System has a syscheck daemon that creates SHA1 and MD5 checksums of all important and user specified files in the system and periodically tracks those files for changes. Is that what you are searching for?

---

