---
title: "rkhunter: different numbers of Rootkit checked"
date: 2012-01-25
forum: Security
---

### Post by cheuvreuile on 2012-01-25
Hi,

I installed rkhunter 1.3.6 on my server, and running it (sudo rkhunter -c), the result says that 244 Rootkit have been checked (Rootkits checked : 244).
After I upgrade rkhunter to the last version (1.3.8 ), he just check 243 Rootkits (Rootkits checked : 243).

rkhunter doesn't return any warning, and nothing have been modified between the two tests.

I don't understand why there is a difference, does anybody know?

Thank you!

---

### Post by Dangertux on 2012-01-25
> **cheuvreuile said:**
> Hi,

I installed rkhunter 1.3.6 on my server, and running it (sudo rkhunter -c), the result says that 244 Rootkit have been checked (Rootkits checked : 244).
After I upgrade rkhunter to the last version (1.3.8 ), he just check 243 Rootkits (Rootkits checked : 243).

rkhunter doesn't return any warning, and nothing have been modified between the two tests.

I don't understand why there is a difference, does anybody know?

Thank you!

Possibly a test was taking out? Or perhaps two tests were combined? For instance there were multiple checks for phalanx maybe they have been rolled into one check now?

Hope this helps.

---

### Post by cheuvreuile on 2012-01-25
Thank you for your interest!  I don't think that a test was taking out: I test another server with the same OS and version 1.3.8 of rkhunter, and it has 244 Rootkit checked, not 243...   I test the first server (with 243 Rootkit checked) with chkrootkit, and nothing seems wrong.

---

