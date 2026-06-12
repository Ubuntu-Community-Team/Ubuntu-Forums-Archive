---
title: "Use Traditional, Not UUID"
date: 2013-07-15
forum: Server Platforms
---

### Post by meenxo on 2013-07-15
Hello,

I've done some digging around and I cannot find a direct answer to this. 

I am attempting to install Ubuntu 12.04 Server Edition on a brand new system and I would like to use the traditional device names (e.g. /dev/sda1) rather than the UUID. I understand the risks and the benefits of using UUID instead of the device names, it's a requirement that I have no control of. Throughout my search I read somewhere that I can choose to use traditional during installation but I cannot find that option anywhere. Can someone shed some light? What if the option no longer exists, how can I go by switching to the traditional format post-installation without breaking anything with the system?

Thanks!

---

### Post by oldfred on 2013-07-15
You can always just edit fstab. But also consider that you can mount with labels which are also better than device names as you can control that and just make sure not to use duplicate labels.

My Desktop system just plugging in a flash drive then uses a port I skipped on motherboard and it renumbers my drives in Ubuntu, so devices would give me lots of issues.

         Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)


 ls /dev/disk/by-label -lah
UUID & labels
sudo blkid -o list

---

### Post by meenxo on 2013-07-15
Thank you for the information!

---

