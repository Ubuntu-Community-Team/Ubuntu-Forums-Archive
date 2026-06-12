---
title: "Mounting a bin file(Vrtualization file) in Ubuntu"
date: 2012-03-18
forum: Virtualisation
---

### Post by akshay.sulakhe on 2012-03-18
Hello,
      I am working on a project in KVM: For that i need to mount the guest image file used in KVM. Initially,the file is in .img format. Using qemu-img,i successfully converted it into bin format. While mounting the bin file,i get a error,as i must specify the filesystem. I am pasting the command and output. Kindly have a look. Many thanks. :-)

Command and output :-

root@akshay-System-Product-Name:/var/lib/libvirt/images# DEV=$(losetup --find) && losetup -o $((63 * 512)) $DEV test2.bin && mount -o ro $DEV /mnt
mount: you must specify the filesystem type

I tried EXT4 as that was how my virtualized disk formatted. But no luck.

---

### Post by howefield on 2012-03-19
Thread moved to the "*Virtualization*" forum.

---

