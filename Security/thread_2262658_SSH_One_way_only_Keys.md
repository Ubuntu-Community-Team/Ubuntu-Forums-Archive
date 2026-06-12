---
title: "SSH One way only Keys"
date: 2015-01-26
forum: Security
---

### Post by Matt_Houldsworth on 2015-01-26
I have a bash script that needs to SCP files from one server to another. Ordinarily I would setup keys between the servers so that password authentication is not required.

However, in this instance, I want Server1 to have access to SCP to Server2 without Server2 having access to SCP/SSH to Server1

Is that possible?

Thanks for any advice

---

### Post by SeijiSensei on 2015-01-26
Sure.  Just don't create an entry in the appropriate authorized_hosts file on Server1.

---

