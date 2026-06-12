---
title: "Quotacheck At Boot"
date: 2020-11-11
forum: Server Platforms
---

### Post by obeisance2 on 2020-11-11
I'm running a server with Ubuntu 16.04, the server has 24 disks.

Boot time currently takes around 35 minutes with 30 minutes of that caused by quotachecks.

Is there a way to disable the quotacheck at boot?

I know I can run /fastboot but I would still like to run fsck just without the long quotacheck.

---

### Post by obeisance2 on 2020-11-11
I added an entry in the /etc/default/grub file which I believe should resolve the issue.

GRUB_CMDLINE_LINUX_DEFAULT="quotacheck.mode=skip"

---

### Post by QIII on 2020-11-11
Moved to **Server Platforms**

---

