---
title: "cannot download/install efivars program for trusty"
date: 2015-01-04
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-01-04
Do I need to enable proposed?

Regards..

---

### Post by ventrical on 2015-01-04
This works just as well in trusty.

```

ventrical@ventrical-desktop:~$ dmesg | grep "EFI v"
[    0.000000] efi: EFI v2.00 by American Megatrends
ventrical@ventrical-desktop:~$ lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty
ventrical@ventrical-desktop:~$ 
ventrical@ventrical-desktop:~$ uname -a
Linux ventrical-desktop 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
ventrical@ventrical-desktop:~$ 


```

---

