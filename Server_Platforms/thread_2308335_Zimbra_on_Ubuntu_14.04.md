---
title: "Zimbra on Ubuntu 14.04"
date: 2016-01-02
forum: Server Platforms
---

### Post by sumitsrjhs on 2016-01-02
Hi

i have installed Zimbra on Ubuntu 14.04 mount 3.2 TB HDD.

Filesystem                           size   used  Avail   Use%      Mounted on
/dev/mapper/ltmail--vg-root  3.2T  5.9G  3.1T   1%             /

Please suggest should it ok to stable the server or we should mount File systems separately, For better Server stabilization or to prevent FS corruption.

Regards

Sumit

---

### Post by Habitual on 2016-01-02
[https://files.zimbra.com/website/docs/8.6/ZCS_System_Requirements_8.6.0.pdf](https://files.zimbra.com/website/docs/8.6/ZCS_System_Requirements_8.6.0.pdf)

---

### Post by nerdtron on 2016-01-02
Depends on how much paranoid are you. I suggest to have hardware RAID10 for you server (to survive hard drive failures of course). Then on the OS side, it would be also good to have it's own Volume Group and own Logical Volume so that it won't mix up with the OS volume groups and logical volumes.

---

