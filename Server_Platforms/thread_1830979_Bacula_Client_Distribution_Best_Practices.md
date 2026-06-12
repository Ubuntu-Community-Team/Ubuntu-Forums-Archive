---
title: "Bacula Client Distribution Best Practices?"
date: 2011-08-22
forum: Server Platforms
---

### Post by Jake.Debord on 2011-08-22
What are ways you would suggest rolling out Bacula clients in a Windows  environment. I would like to keep users from knowing the password. What  ways do you give users Bacula? Do you go to each machine and manually  install it yourself, or do you send them the installer with the dir name  and password and let them? Do you create your own installer?

All tips and advice are welcome!!!

Thanks in advance!

---

### Post by Jake.Debord on 2011-08-24
Bump :)

---

### Post by shairozan on 2011-11-09
Hello there, 

Deployment for bacula in a mass environment becomes difficult because both the password on the client and the password on the director must sync up. During my most recent deployment (66 devices) we did a modular deployment that doubled as test. 

As such, we went to a single department, manually installed there, created the client and the job in the director file and moved to the next machine. Eventually we had installed it on every machine and used webacula to monitor current jobs and or terminated jobs.

---

### Post by Habitual on 2011-11-10
> **Jake.Debord said:**
> ...installer with the dir name  and password and let them?

uh, No, Never, EVER

---

