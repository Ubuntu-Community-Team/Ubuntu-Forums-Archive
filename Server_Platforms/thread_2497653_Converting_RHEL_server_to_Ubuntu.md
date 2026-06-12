---
title: "Converting RHEL server to Ubuntu?"
date: 2024-05-13
forum: Server Platforms
---

### Post by stevehenderson710 on 2024-05-13
How are y'all?

Is there a way to convert RHEL7 and 8 servers to Ubuntu OS run servers?

Thanks,

---

### Post by ajgreeny on 2024-05-15
Convert?  No.

You would have to reinstall with Ubuntu.

---

### Post by MAFoElffen on 2024-05-17
Server Migration: Basic concept. If you Design your infrastructure architecture, into a 3-Tier system... You have your OS & applications, data, and presentation.

So you install the OS, whether a release upgrade or another OS. Since another OS, reinstall your applications/services. restore tweaked config's, as it is on a different Distor branch (RHEL vs Debian). Restore your data. Replicate the connections you had. Test.

---

