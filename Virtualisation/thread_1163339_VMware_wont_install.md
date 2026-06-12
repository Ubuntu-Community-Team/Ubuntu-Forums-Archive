---
title: "VMware wont install"
date: 2009-05-18
forum: Virtualisation
---

### Post by ant2ne on 2009-05-18
I installed once, but didn't complete the process or something. I tried running the uninstall script and I tried 

```
ant2ne@2ne-buntu:~/vmware/vmware-server-distrib$ sudo ./vmware-install.plThe following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.



I.e. - 'rm /lib/modules/2.6.28-11-generic/misc/<ModuleName>.{o,ko}'

Execution aborted.

ant2ne@2ne-buntu:~/vmware/vmware-server-distrib$ ls -l /lib/modules/2.6.28-11-generic/misc/
total 0
ant2ne@2ne-buntu:~/vmware/vmware-server-distrib$ 

```

As you can see... there is nothing listed to remove.

I tried the rm /etc/vmware trick too. Still no luck.

---

### Post by dcstar on 2009-05-21
> **ant2ne said:**
> I installed once, but didn't complete the process or something. I tried running the uninstall script and I tried 

```
ant2ne@2ne-buntu:~/vmware/vmware-server-distrib$ sudo ./vmware-install.plThe following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.



I.e. - 'rm /lib/modules/2.6.28-11-generic/misc/<ModuleName>.{o,ko}'

Execution aborted.

ant2ne@2ne-buntu:~/vmware/vmware-server-distrib$ ls -l /lib/modules/2.6.28-11-generic/misc/
total 0
ant2ne@2ne-buntu:~/vmware/vmware-server-distrib$ 

```

As you can see... there is nothing listed to remove.

I tried the rm /etc/vmware trick too. Still no luck.

Try:

```
sudo ls -l /lib/modules/2.6.28-11-generic/misc/
```

---

### Post by Mach1US on 2009-06-17
run

rm /lib/modules/2.6.28-11-generic/misc/*.{o,ko}

then run the script again

---

### Post by fermulator on 2010-07-01
Lame.  How did this happen?

---

