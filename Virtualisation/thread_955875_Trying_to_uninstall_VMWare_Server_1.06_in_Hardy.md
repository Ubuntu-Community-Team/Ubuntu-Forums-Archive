---
title: "Trying to uninstall VMWare Server 1.06 in Hardy"
date: 2008-10-22
forum: Virtualisation
---

### Post by dirtydave on 2008-10-22
I am trying to remove VMware Server, I tried sudo vmware-uninstall.pl, but did not work.  I then tried sudo rm -Rf /etc/vmware/ .  Now things are really hosed.  VMWare is not uninstalled entirely.  I wanted to remove 1.06 sot that I could try 2.0.  Any ideas?

---

### Post by Spitphire on 2008-10-22
```

sudo /usr/bin/vmware-uninstall.pl

```

Was your best bet - you should have stopped all vmware processes before executing.. don't know what to tell you now.

---

### Post by bodhi.zazen on 2008-10-22
What was not removed ?

I thought (although I have not tried it) you could just install 2.0 without removing 1.6 first.

---

### Post by dirtydave on 2008-10-23
This is what I am getting when trying to install 2.0

```
david@david-desktop:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.pl
[sudo] password for david: 
The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmmon
vmnet

I.e. - 'rm /lib/modules/2.6.24-21-generic/misc/<ModuleName>.{o,ko}'

Execution aborted.

```

---

### Post by bodhi.zazen on 2008-10-23
> **dirtydave said:**
> This is what I am getting when trying to install 2.0

```
david@david-desktop:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.pl
[sudo] password for david: 
The following VMware kernel modules have been found on your system that were 
not installed by the VMware Installer.  Please remove them then run this 
installer again.

vmmon
vmnet

I.e. - 'rm /lib/modules/2.6.24-21-generic/misc/<ModuleName>.{o,ko}'

Execution aborted.

```

Well, that error message also tells you the solution ;)

```
sudo rm /lib/modules/2.6.24-21-generic/misc/vmmon.{o,ko}
sudo rm /lib/modules/2.6.24-21-generic/misc/vmnet.{o,ko}
```

---

