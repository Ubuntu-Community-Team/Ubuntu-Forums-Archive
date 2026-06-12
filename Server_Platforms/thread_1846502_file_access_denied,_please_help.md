---
title: "file access denied, please help"
date: 2011-09-19
forum: Server Platforms
---

### Post by refz on 2011-09-19
i got this problem:

ubuntu@ubuntu-HP-dx2810-MT:~$ update-initramfs -c -k 2.6.38-8-generic -b /nfsroot
update-initramfs: Generating /nfsroot/initrd.img-2.6.38-8-generic
touch: cannot touch `/nfsroot/initrd.img-2.6.38-8-generic.new': Permission denied
/usr/sbin/mkinitramfs: 354: cannot create /nfsroot/initrd.img-2.6.38-8-generic.new: Permission denied
E: mkinitramfs failure find 141 cpio 141 gzip 2
update-initramfs: failed for /nfsroot/initrd.img-2.6.38-8-generic

anyone know about this? please help

---

### Post by lisati on 2011-09-19
You might need to use the "sudo" command to run the program with temporarily elevated user priviliges. For more information see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

