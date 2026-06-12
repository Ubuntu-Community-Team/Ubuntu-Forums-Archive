---
title: "MD5 program question"
date: 2009-01-16
forum: Server Platforms
---

### Post by sclough on 2009-01-16
Ok, I feel a little stupid, but running rkhunter on my machine is complains every day that it can't find md5.  The script is looking for an md5 binary.  I see md5sum, but not md5.  Should there be an md5 that I can install or should I just sym link md5 to md5sum to make rkhunter happy?

---

### Post by windependence on 2009-01-16
md5sum IS md5. More info here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

-Tim

---

### Post by sclough on 2009-01-16
That's sorta what I was thinking.  I'll just create an md5 in bin that's just symlinked to md5sum and that should make rkhunter happy.

---

