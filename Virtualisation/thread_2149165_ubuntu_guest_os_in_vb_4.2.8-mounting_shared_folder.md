---
title: "ubuntu guest os in vb 4.2.8-mounting shared folders problem"
date: 2013-05-27
forum: Virtualisation
---

### Post by lvgandhi on 2013-05-27
I have ubuntu as guest os in VBox. My ubuntu is
lvgandhi@lvgandhi-ubuntu-VirtualBox:~$ uname -a
Linux lvgandhi-ubuntu-VirtualBox 3.2.0-44-generic #69-Ubuntu SMP Thu May 16 17:35:01 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
I have mounted local folders as shared folders without auto mounting and have the following fstab additions
Lvg	/media/Lvg	vboxsf	uid=1000,rw	0	0
Downloads	/media/Downloads	 vboxsf  uid=1000,rw     0       0
NOW2AMIJ 	/media/NOW2AMIJ         vboxsf  uid=1000,rw     0       0
It used to work until yesterday. Today shared folders are not getting mounted. Any solutions?
When I do manual mounting
lvgandhi@lvgandhi-ubuntu-VirtualBox:/media$ sudo mount -t vboxsf -o uid=1000,gid=1000 Lvg /media/Lvg
/sbin/mount.vboxsf: mounting failed with the error: No such device

---

### Post by Morbius1 on 2013-05-28
Starting with version 4.0.0 of VBox your shared folders are automatically mounted to /media/sf_XXX so there is no need to mount anything in fstab.

---

### Post by lvgandhi on 2013-05-28
> **Morbius1 said:**
> Starting with version 4.0.0 of VBox your shared folders are automatically mounted to /media/sf_XXX so there is no need to mount anything in fstab.

Thanks for the response. I know that while creating shared folders there is option for automounting and mounts to /media/sf_XXX. But how about permissions? Can it be incorporated anywhere in automounting?

Second my problem was not due to mounting. It was due to guest-additions were done with previous kernel and after updating to new kernel. However it is still mystery to me that guest additions worked when kernels were changed from .38 (original one) to .39, .40, .41 and .43. But when kernel .44 was installed, it stopped working.
However when I tried to reinstall guest-additions, it was giving error. After I removed iso from cdrom in settings/storage for ubuntu virtual machine and did install guest-additions from device option after starting ubuntu, it reinstalled for new kernel. Now everything is ok.

---

### Post by Morbius1 on 2013-05-28
> Thanks for the response. I know that while creating shared folders there  is option for automounting and mounts to /media/sf_XXX. But how about  permissions? Can it be incorporated anywhere in automounting?
/media/sf_XXX is mounted with these permissions:

owner = root
group = vboxsf
perms = 770

Everyone who is a member of the vboxsf group has read / write access so you need to add yourself to that group. In the Ubuntu guest:
```
sudo gpasswd -a lvgandhi vboxsf
```
Then logoff and logon again.

---

### Post by lvgandhi on 2013-05-28
> **Morbius1 said:**
> /media/sf_XXX is mounted with these permissions:

owner = root
group = vboxsf
perms = 770

Everyone who is a member of the vboxsf group has read / write access so you need to add yourself to that group. In the Ubuntu guest:
```
sudo gpasswd -a lvgandhi vboxsf
```
Then logoff and logon again.

Thanks.
what does the last command in your post does?

---

### Post by Morbius1 on 2013-05-29
It uses the gpasswd utility to add (-a)  		lvgandhi to the vboxsf group in the /etc/group file.

---

### Post by lvgandhi on 2013-05-29
> **Morbius1 said:**
> It uses the gpasswd utility to add (-a)  		lvgandhi to the vboxsf group in the /etc/group file.

Thanks.

---

