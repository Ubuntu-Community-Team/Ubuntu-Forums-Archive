---
title: "How do I enforce a certain password complexity?"
date: 2007-10-06
forum: Server Platforms
---

### Post by darkpark on 2007-10-06
For local user accounts, how would I force people to use a certain level complexity in their passwords?   I want to be sure that nobody's password is too simple.

---

### Post by MrFSL on 2007-10-07
All hail google!

[http://www.linuxquestions.org/questions/linux-security-4/howto-change-system-password-policies-passwd-length-complexity-360522/](http://www.linuxquestions.org/questions/linux-security-4/howto-change-system-password-policies-passwd-length-complexity-360522/)
> Being in Ubuntu at the moment, I can tell you it is at /etc/pam.d/common-password. Once you open the file, you should see a line that begins with the words password required. Here, you should hopefully see a min= or minlen= variable. Set it to the length you prefer.

---

