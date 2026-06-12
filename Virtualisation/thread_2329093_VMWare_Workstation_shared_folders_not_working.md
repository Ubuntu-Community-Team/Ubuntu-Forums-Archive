---
title: "VMWare Workstation shared folders not working"
date: 2016-06-27
forum: Virtualisation
---

### Post by galapogos on 2016-06-27
Hi,

I'm running Ubuntu 14.04 LTS on VMWareware Workstation 12 Pro on a Win10 host. Lately my shared folders has stopped working. When i try to go into /mnt/hgfs, I get a "Protocol error".

I've tried re-installing vmware-tools but that didn't help.

Any ideas please? Thanks.

---

### Post by MAFoElffen on 2016-06-28
Please post 
```

sudo ls -l /mnt/hgfs
groups User_Name
uname -a

```
Replace User_Name with the user's login name.

And you said you had if working. Did you have if show in your Windows VM Guest as a separate shared volume or as a directory in one of your system volumes?

The reason I have a query on the kernel info is... there was one interim kernel version in 14.04 that had problems with folder sharing in VMware Workstation 12 Pro ... but if you do 
```

sudo apt-get update && sudo apt-get dist-upgrade

```
Current is past that and working fine.

---

