---
title: "possible root kit"
date: 2012-11-15
forum: Security
---

### Post by Gster4 on 2012-11-15
so today i decided to check up on my system.  so i used rkhunter and got tons of warnings.  then i tried chkrootkit and got nothing.   ran 
```
rkhunter -u
rkhunter -c
```and got the same warnings.  so could this be a rootkit? im running 12.04 and updated recently.
rkhunter log in attachments.

---

### Post by Ms. Daisy on 2012-11-15
You can just use the code tags instead of attaching a tar.bz2 file.  Paranoia runs deep in this forum, so you're likely to get a few more views that way.

Without looking at the file, rkhunter throws tons of warnings after updates, especially kernel upgrades. You have to create a new baseline after every significant update to manage the false positives. Did the kernel update recently?

---

### Post by Gster4 on 2012-11-16
yeah, upgraded the kernel yesterday.  guess that must have thrown stuff off.  anyway i ran rkhunter again and looks like this stuff is all false positives.

---

