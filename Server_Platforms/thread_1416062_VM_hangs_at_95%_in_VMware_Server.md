---
title: "VM hangs at 95% in VMware Server"
date: 2010-02-25
forum: Server Platforms
---

### Post by abadr on 2010-02-25
Just though I'd post this here in case somebody else encounters the same problem.

After both host OS upgrade and a VMware server upgrade, a 32-bit win2k virtual machine running on 64-bit Ubuntu host refused to completely load and hangs at 95%. Deleting the lock files resolved the problems for me. You can find them in the virtual machine's directory in directories ending with '.lck'

---

