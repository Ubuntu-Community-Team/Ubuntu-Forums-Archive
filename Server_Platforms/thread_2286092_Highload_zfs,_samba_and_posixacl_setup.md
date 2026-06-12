---
title: "Highload zfs, samba and posixacl setup"
date: 2015-07-09
forum: Server Platforms
---

### Post by struct2 on 2015-07-09
I have zfs, samba and posixacl setup but periodically throughout the day I get a very high load which renders the storage system unusable.
Do anyone on this discussion thread have this issue? I need some insight what could cause such highload.
I'd appreciate any pointers. Thanks in advance.

---

### Post by cariboo on 2015-07-09
Moved to a thread of it's own.

---

### Post by cariboo on 2015-07-09
Moved to a thread of it's own.

---

### Post by volkswagner on 2015-07-11
Use the command
```
top
```
To see which process is hogging resources.

Check and post pertinent log info.

---

### Post by lukeiamyourfather on 2015-07-13
> **struct2 said:**
> I have zfs, samba and posixacl setup but periodically throughout the day I get a very high load which renders the storage system unusable.
Do anyone on this discussion thread have this issue? I need some insight what could cause such highload.
I'd appreciate any pointers. Thanks in advance.

More information is needed like details on the workload and configuration of the server. Is this something you setup from scratch or is this a project you inherited?

---

