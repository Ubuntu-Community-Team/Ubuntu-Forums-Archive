---
title: "VMWARE Server Install error"
date: 2007-10-24
forum: Virtualisation
---

### Post by sledgeyj on 2007-10-24
I have tried to install VMWARE SERVER AS FOLLOWS:
UBUNTU 7.10
vmware 1.04
vmware.any.any.114

have installed vmware, and compiles ok. but when I run configure, it gives the following error:

Unable to find any instance of the super-server "inetd" or "xinetd".  It is 
possible that you do not have one of these packages installed on this machine. 
Please install "inetd" or "xinetd".

If you do have "inetd" or "xinetd" installed, make sure that /etc/inetd.conf or
/etc/xinetd.d exists.
The configuration will continue, but you should re-run 
/usr/bin/vmware-config.pl after you fix the super-server.

I have gotten the same error on two seperate boxes running 7.10

Please advise if you have any good ideas, i will even settle for bad ones right now.

Thanks!

---

### Post by drachenstern on 2007-10-25
do you indeed have xinetd installed?

---

### Post by gtdaqua on 2007-10-25
you need these before u install VMWare

```

aptitude install linux-headers-`uname -r` build-essential
aptitude install xinetd

```

That will install xinetd superserver and run it.

This might help as well:
```

sudo aptitude install libxtst6 libxt6 libxrender1

```

On 64-bit do this:
```

sudo apt-get install ia32-libs libc6-i386

```

Oh, btw, if you have VMWare 1.04 then you dont need the 'any any' patch. 1.04 works well without the patch and so its a straight forward install!

---

