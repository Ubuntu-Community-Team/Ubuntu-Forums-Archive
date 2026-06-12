---
title: "move VMware vmdk files to a new system"
date: 2009-07-13
forum: Virtualisation
---

### Post by IQRules on 2009-07-13
Can we copy vmdk files from old Intel Desktop system to a HP intel core 2 duo Ubuntu 8.10 server?

They are 2 different type Intel CPUs here, is that okay?

---

### Post by HermanAB on 2009-07-13
Just shut down the VM, then make a tar ball of the whole VM directory, copy and untar it on the other machine.  Simple as that.

---

### Post by IQRules on 2009-07-13
Forgot to mention, the guest OS is Windows XP. Is it just simple tar and copy?

---

### Post by fjgaude on 2009-07-13
> **IQRules said:**
> Forgot to mention, the guest OS is Windows XP. Is it just simple tar and copy?

Yes. I've moved from AMD to Intel CPUs without issue with the guest being WinXP. Just follows the prompts you get from Windows when you run in the new environment.

---

### Post by veloce on 2009-07-13
> **IQRules said:**
> Forgot to mention, the guest OS is Windows XP. Is it just simple tar and copy?

You may need to re-activate Windows.  If the "hardware" changes "too much" then Windows (and office) require you to reactivate.

---

