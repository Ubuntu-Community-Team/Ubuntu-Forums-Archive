---
title: "After Upgrade to 16.10, VMWare message: GCC 5.4.1 not found"
date: 2016-09-02
forum: Ubuntu Development Version
---

### Post by afaqbabar on 2016-09-02
Hi,
  I upgraded ubuntu to 16.10. Now the problem is that when I open vmware workstation 12, I get following message:

**"GNU C compiler (gcc) 5.4.1 was not found. ... "**

GCC version from command line gives following

 gcc (Ubuntu 6.2.0-2ubuntu11) 6.2.0 20160830. 

Kindly help, as what shall I do.

Regards,

Afaq

---

### Post by wildmanne39 on 2016-09-02
*Thread moved to **Ubuntu Development Version**.*

---

### Post by afaqbabar on 2016-09-15
I applied following command(s) and restarted computer. The issue is now resolved.

ln -s /usr/src/linux-headers-$(uname -r)/include/generated/uapi/linux/version.h /usr/src/linux-headers-$(uname -r)/include/linux/version.h
vmware-modconfig --console --install-all

---

