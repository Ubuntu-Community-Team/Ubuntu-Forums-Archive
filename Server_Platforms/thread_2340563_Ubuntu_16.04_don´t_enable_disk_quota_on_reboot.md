---
title: "Ubuntu 16.04 don´t enable disk quota on reboot"
date: 2016-10-19
forum: Server Platforms
---

### Post by rhandy2 on 2016-10-19
Hello

After dist upgrade server from ubuntu 14.04 to ubuntu 16.04

I have to enable (rw) on filesystem because is locked.

Now I have rw enable and I can write on drive.

My problem is i Have to enable quotas by hand, every time I reboot server.

My fstab

```

 /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=xxxxxxxxxxxxxxxxxxxxxxxxxx      /       ext4    errors=remount-ro,rw,grpquota,usrquota  0       1
# swap was on /dev/sdb5 during installation
UUID=zzzzzzzzzzzzzzzzzzzzzzzzzz none            swap    sw              0       0



```


service status

```

&#9679; quota.service - Initial Check File System Quotas
   Loaded: loaded (/lib/systemd/system/quota.service; enabled; vendor preset: enabled)
   Active: active (exited) since Qua 2016-10-19 15:56:24 WEST; 5h 47min ago
     Docs: man:quotacheck(8)
  Process: 461 ExecStart=/usr/share/quota/quota-initial-check.sh (code=exited, status=0/SUCCESS)
 Main PID: 461 (code=exited, status=0/SUCCESS)
   CGroup: /system.slice/quota.service



```

My question is .  How I can enable quotas for users without make ```
$quotaon /
``` - everytime i reebot server.

---

### Post by rhandy2 on 2016-10-20
Ok!

Maybe is not the best way to do it. But I fix by using /etc/rc.local and add > quotaon -a

---

