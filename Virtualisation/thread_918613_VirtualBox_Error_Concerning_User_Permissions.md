---
title: "VirtualBox Error Concerning User Permissions"
date: 2008-09-13
forum: Virtualisation
---

### Post by drdoombot on 2008-09-13
I'm a total Linux n00b, so please bear with me.

After installing VirtualBox in Hardy Heron, and configuring a WinXP machine within VirtualBox, I get the following error when trying to start it:

> VirtualBox - Error

Failed to start the virtual machine WinXP SP2


The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}



I've already checked to make sure that I'm a member of the vboxusers group. I also checked /dev/vboxdrv to make sure that vboxusers members have read and write access. There is only one account on this machine (besides root). I've also made sure to logout after each of these checks.

Being so new to Linux, I have no idea what I have missed. I've searched Google and these forums but haven't found a solution that works for me.

---

### Post by drdoombot on 2008-09-14
No one else has encountered this problem?

---

### Post by sisco311 on 2008-09-14
open a terminal and post the output of:
(Applications -> Accessories -> Terminal)
```
id
```
and
```
ls -l /dev/vboxdrv
```

---

### Post by drdoombot on 2008-09-14
Output of id:
```

uid=1000(victor) gid=1000(victor) groups=4(adm),6(disk),20(dialout),24(cdrom),
25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),
115(admin),125(sambashare),126(vboxusers),1000(victor)

```

Output of ls -l /dev/vboxdrv
```

crw-rw---- 1 root vboxusers 10, 63 2008-09-14 16:24 /dev/vboxdrv

```

---

