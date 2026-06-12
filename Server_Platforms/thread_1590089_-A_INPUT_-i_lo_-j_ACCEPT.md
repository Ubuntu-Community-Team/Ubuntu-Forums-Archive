---
title: "-A INPUT -i lo -j ACCEPT"
date: 2010-10-07
forum: Server Platforms
---

### Post by Thyagaraj on 2010-10-07
What if the rule is "-A INPUT -i lo -j ACCEPT" is excluded in the iptable config file.
will I get into trouble?

---

### Post by BkkBonanza on 2010-10-07
If the default policy is DROP then yes. Normally the default policy is ACCEPT which means the lack of a rule would result in the loopback interface being ACCEPTed anyway.

---

### Post by Thyagaraj on 2010-10-07
Hi Bonanza!
This is actually related to other thread I posted [http://ubuntuforums.org/showthread.php?t=1590031 ]("http://ubuntuforums.org/showthread.php?t=1590031")
Please answer to this thread...

---

### Post by metcarob on 2010-10-08
I didn't have this rule and I just had every INPUT packet drop.
Then my PHP scripts couldn't connect to the mysql database.
After adding this rule it worked.

What I didn't realise was that traffic internal to my server still goes through the INPUT chain. This rule basically says allow all local traffic.

---

