---
title: "security problem for password and login setting"
date: 2009-07-16
forum: Security
---

### Post by liung on 2009-07-16
I want to do some security config, and I add a line in /etc/pam.d/common-auth file and a line in /etc/pam.d/commom-password, but they doesn't works, can somebody tell me where was wrong?

To limit wrong login times in /etc/pam.d/common-auth:
auth    required        pam_tally.so deny=2

To limit the password's length:
password    required      pam_cracklib.so retry=3 minlen=8 difok=3

Is there some documents for security setting?

Thanks for anybody's notice!

---

### Post by liung on 2009-07-26
Can somebody help me or tell me where I can find information for this ?

---

