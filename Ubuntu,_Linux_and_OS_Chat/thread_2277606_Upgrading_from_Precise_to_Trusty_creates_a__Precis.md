---
title: "Upgrading from Precise to Trusty creates a  Precise shell from kernel!"
date: 2015-05-10
forum: Ubuntu, Linux and OS Chat
---

### Post by ventrical on 2015-05-10
I was doing an experiment with the upgrade tool. I wanted to test if Comodo Anti-Virus would survive an upgrade from Precise to Trusty. CAV would not work with the new Trusty kernels so I did the procedure for fix to activate filters and it still would not work. I notice in Grub an instance:

```

ventrical@ventrical-MS-7798:~$ uname -a
Linux ventrical-MS-7798 3.5.0-54-generic #81~precise1-Ubuntu SMP Tue Jul 15 04:05:58 UTC 2014 i686 i686 i686 GNU/Linux

```

and so I booted from there and now CAV works better than before and lsb_release still tells me I am in trusty:

```

ventrical@ventrical-MS-7798:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty
ventrical@ventrical-MS-7798:~$ 


```

so theoretically, by preserving the last  kernel update from precise and appending it to the new upgrade it more or less effectively created a Precise (12.04) shell of sorts, preserving the config and kernel bindings for Comodo AV.

 More amazing stuff I've learned about Ubuntu!:)

 
Regards..

---

