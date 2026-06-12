---
title: "VM - Ubuntu 20.04 can't connect &quot;sf_transfer_folder&quot;"
date: 2022-03-28
forum: Virtualisation
---

### Post by satimis on 2022-03-28
Host - Ubuntu 20.04
VM - Ubuntu 20.04

It is very strange.  Just found all Ubuntu 20.04 VMs unable to connect "sf_transfer_folder"

Warning:```

You do not have permissions necessaryh to view the contents of "sf_transfer_folder"

VBoxClienT: Failure waiting for event,rc=VERR_INVALID_HA...
```

On Ubuntu 20.04 VM Terminal

$ lsb_release -r
Release:        20.04

$ VBoxClient --version
6.1.32r149290

$ gcc --version
gcc (Ubuntu 9.4.0-1ubuntu1~20.04) 9.4.0

All Windows10 VMs don't have this problem.

Please advise how to solve the problem.  Thanks

Regards

---

