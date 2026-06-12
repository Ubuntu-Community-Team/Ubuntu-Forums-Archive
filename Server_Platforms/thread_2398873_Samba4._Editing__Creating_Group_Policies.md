---
title: "Samba4. Editing / Creating Group Policies"
date: 2018-08-18
forum: Server Platforms
---

### Post by vittmann2018 on 2018-08-18
Hello. Faced the **strange behavior of the domain controller on Samba4.**


When raising a domain, I tried to create a group policy for test purposes and it was created without problems.


Recently, I decided to create a group policy for deploying the software. I ran gpmc.ms with the built-in Administrator, deleted this old, test policy and tryed to create a new one. But I get the error "Group Policy Management. Access is Denied ».


I tried to fix this command:


```
samba-tool ntacl sysvolreset

```

But it did not help
Are there any ideas?

---

