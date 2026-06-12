---
title: "Multiple guest entries in /etc/passwd"
date: 2012-08-03
forum: Security
---

### Post by followurdrmz on 2012-08-03
Im using Ubuntu 12.04 x64. I have two accounts enabled, one is a administrator and another one is a Guest account. Guys other than me use the Guest account. I noticed that there are multiple Guest entries in the /etc/passwd file, why? Is this normal?

guest-pYOxnH:x:115:126:Guest,,,:/tmp/guest-pYOxnH:/bin/bash
guest-I33nTW:x:116:127:Guest,,,:/tmp/guest-I33nTW:/bin/bash
guest-PQ7HaK:x:117:128:Guest,,,:/tmp/guest-PQ7HaK:/bin/bash
guest-eK5E3L:x:118:131:Guest,,,:/tmp/guest-eK5E3L:/bin/bash
guest-Tm8JcU:x:119:133:Guest,,,:/tmp/guest-Tm8JcU:/bin/bash
guest-ETzFUt:x:120:134:Guest,,,:/tmp/guest-ETzFUt:/bin/bash
guest-bJYcaf:x:121:135:Guest,,,:/tmp/guest-bJYcaf:/bin/bash

Should i delete these entries? At the logon screen only one Guest account is visible.

---

### Post by vipulkumar7 on 2012-08-03
yes it's normal in ubuntu 1000 + User ID ( uid) are allowed for Normal user and  below 1000(uid) are assigned to system application and daemons :)
so Yes it's normal and if you want to check completely how many user are on you system. Get inside root account and then use this command

> cat /etc/passwd | grep "/home"

You will see the list of user :)

---

### Post by followurdrmz on 2012-08-03
@vipul - Thanks, that helps. I'll try to remove the guest account and create a new user and see if that works good.

---

### Post by zombifier25 on 2012-08-03
For me the guest accounts are removed periodically (can't check, but I logged in as guest more than half a dozen times, but none sticked around very long in /etc/passwd). I don't see why you need to do it yourself.

---

