---
title: "fstab entries won't mount on boot but sudo mount -a works fine"
date: 2021-03-18
forum: Virtualisation
---

### Post by RichJacot on 2021-03-18
I'm running an Ubuntu 20.04 desktop VM on a QNAP NAS. I have the NAS mounts in my fstab and credentials files in my home dir..  When I reboot it doesn't auto mount my NAS shares but if I run sudo mount -a they all mount without issue.   Does anyone know what I might be missing?

An example of one of my fstab lines is: 

//192.168.xx.xx/Media /mnt/Media cifs credentials=/home/xxxxx/.smbcredentials1,uid=xxxxx 0 0

---

### Post by slickymaster on 2021-03-18
*Thread moved to **Virtualisation**.*

---

### Post by Morbius1 on 2021-03-18
The current thinking is to modify your fstab declaration by adding two options to your list: noauto,x-systemd.automount:
```
 //192.168.xx.xx/Media /mnt/Media cifs credentials=/home/xxxxx/.smbcredentials1,uid=xxxxx,noauto,x-systemd.automount 0 0         
```

Then make systemd happy:
```
sudo systemctl daemon-reload
sudo systemctl restart remote-fs.target
```

**noauto** == makes it so it will not mount automatically at boot
**x-systemd.automount** == makes it so it will mount on demand

This may seem counterintuitive since you are telling it to not mount automatically but the way this works is it will mount only when the mount point is accessed. That can happen when you access it through Nautilus, or if you access it through another application, or you access it through a script, ....

The problem is fstab is being accessed way too early in the boot process so the network stack isn't fully operational and the cifs mount fails. After you log in everything should be operational so the automount now works and is why issuing a "mount -a" works.

---

### Post by RichJacot on 2021-03-18
That appears to have worked.  I have several automated applications that start on boot and when I ssh'd in after the reboot, the mounts were there already.  Thank you Very much!!!

---

