---
title: "chkrootkit indicates Suckit Rootkit.  Rootkit Hunter does not."
date: 2009-12-22
forum: Security
---

### Post by 55tptag on 2009-12-22
Hello,

I'm using: 
-chkrootkit version 0.48
-Rootkit Hunter version 1.3.4
-Ubuntu 9.10

I don't know much about computers.

A) Yesterday I ran 'chkrootkit' and it indicated:
- Searching for Suckit rootkit... Warning: /sbin/init INFECTED
Then, I ran 'rkhunter -c' and it said my PC did not have Suckit:
- Suckit Rootkit [ Not found ]

B) So, I thought my PC might be infected.  So I reinstalled from scratch.  After re-installing Ubuntu I installed 'chkrootkit' and ran it and it said:
- Searching for Suckit rootkit... nothing found

C) Next, I updated the system with Synaptic Package Manager.  And I re-ran 'chkrootkit'.  This time it found it again and said:
- Searching for Suckit rootkit... Warning: /sbin/init INFECTED
I also re-ran 'rkhunter -c'
- Suckit Rootkit [ Not found ]

D) What would you suggest the next step be?  Should I ignore this?

---

### Post by FuturePilot on 2009-12-22
Did you add any third party repos or install anything from outside the official Ubuntu repos between the time you reinstalled and the time you installed the updates? If not it's most likely a false positive.

---

### Post by jrusso2 on 2009-12-22
chkrootkit has so many false positives I don't know how anyone uses it.

---

### Post by 55tptag on 2009-12-22
Thanks for your help.  I only use the default repos.  
I'll assume it's a false positive.

Thanks!

---

### Post by oldos2er on 2009-12-23
Seems to be a known issue: [https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566](https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566)

---

### Post by 55tptag on 2009-12-23
> **oldos2er said:**
> Seems to be a known issue: [https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566](https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566)

Thank you!

---

