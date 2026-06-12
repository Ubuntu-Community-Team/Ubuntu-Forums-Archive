---
title: "Unable to upgrade ubuntu 18.04 server"
date: 2020-02-10
forum: Server Platforms
---

### Post by deepakdeshp on 2020-02-10
Hello,
I have been unable to upgrade the Ubuntu 18.04 64 bit server running as a VM for past 6 months. It can ping google. Please advise.

```
sudo apt list --upgradable Listing... Done
uma@localhost:~$ uname -a
Linux localhost 4.15.0-58-generic #64-Ubuntu SMP Tue Aug 6 11:12:41 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
uma@localhost:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic



```

---

### Post by deepakdeshp on 2020-02-10
It is solved by running ```
[COLOR=#000000][FONT=&quot]sudo apt --fix-missing[/FONT][/COLOR]
```

---

