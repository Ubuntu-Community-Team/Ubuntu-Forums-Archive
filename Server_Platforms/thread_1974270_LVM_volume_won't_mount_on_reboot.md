---
title: "LVM volume won't mount on reboot"
date: 2012-05-05
forum: Server Platforms
---

### Post by Resilldoux on 2012-05-05
Hi,

I just reinstalled my Ubuntu server with the new 12.04. I decided not to upgrade, but to do a fresh install. I left my LVM configuration intact and I was able to have them mount upon bootup while I was repartitioning my disks using the installer. The problem is, however, that when I reboot, Ubuntu can't mount my LVM volume on reboot without me activating the volume every time I reboot. This wasn't necessary in 11.04 so I wonder what's going on here.

When I reboot it gives me this message:
```
The disk drive for /media/data is not ready yet or not present.
Continue to wait, or Press S to skip mounting or M for manual recovery
```When I press S to skip I can login to the server and I can "solve" this issue by entering this command:
```
sudo vgchange -ay
```It then "suddenly sees" my LVM volume again and I can mount it again with:
```
sudo mount -a
```Because it's in my /etc/fstab file.

This is a pretty sloppy work-around, especially when I need to do this every time I reboot so can anybody tell me what I'm doing wrong here? I'd be happy to provide more information if required.

---

### Post by rudyd on 2012-05-30
Greetings!

  Just almost the same problem here. Trying to figure out a solution. Just would like to mount a swap and a former system partition (now became data) at boot time from lvm. The 'new system' is not on lvm. I had to install lvm2 after system install.
Tried to find some tips online:
[http://serverfault.com/questions/199185/logical-volumes-are-inactive-at-boot-time]("http://serverfault.com/questions/199185/logical-volumes-are-inactive-at-boot-time")
but have to figure out more detailed steps for some of the tips now on.

If any would find a solution please post it here.
('old' LVM was default install of 9.10 and the new system is 12.4)

Albeit I also would like to avoid to temper with system commands after each kernel update... If possible.

Thanks in advance!
-- R

---

### Post by rudyd on 2012-05-30
Greetings!

Found some nasty workaround:

Added the > noauto to the according lines of the ```
/etc/fstab
``` file.
Then added the commands to the end of the ```
/etc/rc.local
``` file.

For some reason I needed to tell the name of the lvm. 
It looks similar to this:
```

lvchange -ay name_of_lvm
# mountall # did not work 
swapon -a # to activate swap on lvm
mount /mnt/point/in_fstab/to_lvm
exit 0

```

Still looking for the proper solution for this!
-- 
R

---

