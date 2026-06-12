---
title: "Error installing Ubuntu with Virtual Box"
date: 2016-02-20
forum: Virtualisation
---

### Post by Satyros on 2016-02-20
When opening the .iso with Virtual Box I get this, instead of the installation menu: [URL="http://postimg.org/image/l7oeeg8ox/"]http://postimg.org/image/l7oeeg8ox/


[/URL]

---

### Post by MAFoElffen on 2016-02-21
Please use the following command in a command prompt to find the name of your vm:
```

VBoxManage list vms

```
Find the name of your vm and insert it into the next command:
```

VBoxManage showvminfo "PutVmNameHere"

```
Please post the results of that command... inside of code tags.


Also please post the results of
```

VBoxManage list systemproperties
VBoxManage list extpacks

```
Please describe the PC that is the host (CPU, Memory, Host OS).
Which iso are you trying to install (Which flavor of Ubuntu, version and 64 or 32 bit)?

---

### Post by oldos2er on 2016-02-21
Moved to Virtualisation.

---

