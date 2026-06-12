---
title: "wifi connected but no internet"
date: 2017-11-25
forum: Ubuntu/Debian BASED
---

### Post by apriliyaa on 2017-11-25
> **jeremy31 said:**
> We can uninstall the module by Larry Finger and try one I made some changes to
```
sudo dkms uninstall 8188eu/1.0
sudo dkms remove 8188eu/1.0 --all
```


```
cd ~
git clone https://github.com/jeremyb31/rtl8188eu.git
sudo dkms add ./rtl8188eu
sudo dkms build 8188eu/1.0
sudo dkms install 8188eu/1.0
```

Reboot and see if the signal strength improves

Error for me:

```
root@debian:~# sudo dkms uninstall 8188eu/1.0

-------- Uninstall Beginning --------
Module:  8188eu
Version: 1.0
Kernel:  4.13.0-kali1-amd64 (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


8188eu.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.13.0-kali1-amd64/
rmdir: failed to remove '': No such file or directory
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod......


Backing up initrd.img-4.13.0-kali1-amd64 to /boot/initrd.img-4.13.0-kali1-amd64.old-dkms
Making new initrd.img-4.13.0-kali1-amd64
(If next boot fails, revert to initrd.img-4.13.0-kali1-amd64.old-dkms image)
update-initramfs..........


DKMS: uninstall completed.
root@debian:~# sudo dkms remove 8188eu/1.0 --all


-------- Uninstall Beginning --------
Module:  8188eu
Version: 1.0
Kernel:  4.13.0-kali1-amd64 (x86_64)
-------------------------------------


Status: This module version was INACTIVE for this kernel.
depmod......


DKMS: uninstall completed.


------------------------------
Deleting module version: 1.0
completely from the DKMS tree.
------------------------------
Done.
root@debian:~# kernel
bash: kernel: command not found
root@debian:~# cd ~
root@debian:~# git clone [https://github.com/jeremyb31/rtl8188eu.git](https://github.com/jeremyb31/rtl8188eu.git)
Cloning into 'rtl8188eu'...
remote: Counting objects: 9993, done.
remote: Total 9993 (delta 0), reused 0 (delta 0), pack-reused 9993
Receiving objects: 100% (9993/9993), 12.30 MiB | 53.00 KiB/s, done.
Resolving deltas: 100% (7377/7377), done.
root@debian:~# sudo dkms add ./rtl8188eu


Creating symlink /var/lib/dkms/8188eu/1.0/source ->
                 /usr/src/8188eu-1.0


DKMS: add completed.
root@debian:~# sudo dkms build 8188eu/1.0


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area...
'make' all KVER=4.13.0-kali1-amd64......(bad exit status: 2)
Error! Bad return status for module build on kernel: 4.13.0-kali1-amd64 (x86_64)
Consult /var/lib/dkms/8188eu/1.0/build/make.log for more information.
root@debian:~# sudo dkms install 8188eu/1.0


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area...
'make' all KVER=4.13.0-kali1-amd64...(bad exit status: 2)
Error! Bad return status for module build on kernel: 4.13.0-kali1-amd64 (x86_64)
Consult /var/lib/dkms/8188eu/1.0/build/make.log for more information.
root@debian:~# 
```

---

### Post by howefield on 2017-11-25
Post moved to own thread in the "*Ubuntu/Debian BASED"* forum and quote tags switched to code tags.

---

### Post by jeremy31 on 2017-11-25
The module for the 8188eu wifi cards is part of the 4.13 kernel so I don't know why you would need to install anything

---

### Post by apriliyaa on 2017-11-26
> **jeremy31 said:**
> The module for the 8188eu wifi cards is part of the 4.13 kernel so I don't know why you would need to install anything


[IMG]http://up.vbiran.ir/uploads/15034151168122913287_Untitled.jpg[/IMG]

kali 2017 r3 
in wm

---

### Post by apriliyaa on 2017-11-28
No idea?

---

