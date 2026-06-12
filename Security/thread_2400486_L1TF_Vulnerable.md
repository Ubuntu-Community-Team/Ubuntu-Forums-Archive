---
title: "L1TF Vulnerable"
date: 2018-09-06
forum: Security
---

### Post by amottier on 2018-09-06
Hello,
I did follow the Ubuntu's recommendations to protect my machine against L1TF by updating the Kernel, but I am still vulnerable, how can I fix this ?
```

$ lsb_release -a
Description:    Ubuntu 16.04.1 LTS
$ uname -r
4.4.0-134-generic
$ cat /sys/devices/system/cpu/vulnerabilities/l1tf
Vulnerable
```

I also tried to upgrade to kernel 4.4.154 and to Bionic with Kernel 4.14, same result.

---

### Post by deadflowr on 2018-09-06
Update all.
You should be showing lsb_release -a as Ubuntu 16.04.5.
(This will show regardless of which version was installed on all fully up-to-date releases of 16.04)
The fact that it's showing 16.04.1 means the system isn't fully up-to-date.

But that's that, your issues seems to be the rare rule seen here:
[https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/L1TF]("https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/L1TF")
> In some cases, which are believed to be rare, there may be no mitigation available due to the PTE inversion technique being incompatible with the number of physical address bits used by the processor and the amount of memory installed in the system. In these cases, the file will indicate the no mitigations are in place and that the system is vulnerable:

$ cat /sys/devices/system/cpu/vulnerabilities/l1tf
Vulnerable

---

### Post by mralfabet on 2018-09-12
I'm having the same issue, even after upgrading to 18.04

```

$ cat /sys/devices/system/cpu/vulnerabilities/l1tf
Vulnerable
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:        18.04
Codename:       bionic
$ uname -r
4.15.0-34-generic

```

---

