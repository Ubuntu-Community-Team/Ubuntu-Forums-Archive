---
title: "What is ubuntu 12.04 acpi version&#65311;"
date: 2014-03-31
forum: Ubuntu, Linux and OS Chat
---

### Post by liu3 on 2014-03-31
I heard that acpi have different version.
acpi 1.1&#65292;acpi 2.0&#65292;acpi 3.0 and so on.
which version is ubuntu base on?

---

### Post by deadflowr on 2014-03-31
from apt-cache policy
```
acpi:
  Installed: (none)
  Candidate: 1.6-1
  Version table:
     1.6-1 0
        500 http://mirror.anl.gov/pub/ubuntu/ precise/universe amd64 Packages

```

if that means anything to you.

---

### Post by grahammechanical on 2014-03-31
Ubuntu sits on Linux and it is Linux that has the driver module to manage ACPI. The Linux kernel is under constant development. The latest kernel is 3.14. Here is a list of recent work done regarding ACPI.

[http://kernelnewbies.org/Linux_3.14-DriversArch#head-5dc8ebfa7c32ea6cc7db3eb2b6ea76c664511c56](http://kernelnewbies.org/Linux_3.14-DriversArch#head-5dc8ebfa7c32ea6cc7db3eb2b6ea76c664511c56)

At the moment the newest Linux kernel in Ubuntu is 3.13 but when Ubuntu 14.04 is released it may get kernel 3.14. This is the work that has been done for ACPI in the 3.13 kernel.

[http://kernelnewbies.org/Linux_3.13-DriversArch#head-26cd2d5636fe1e5dcd890f88506ac9883bdff8ac](http://kernelnewbies.org/Linux_3.13-DriversArch#head-26cd2d5636fe1e5dcd890f88506ac9883bdff8ac)

Regards.

---

