---
title: "Trying to install “Ubuntu Base” in Vmware but getting a kernel panic!"
date: 2020-10-20
forum: Virtualisation
---

### Post by automate-stuff on 2020-10-20
Here is how I install Ubuntu Base in Vmware:

load the live media

```

sudo passwd root
su root

parted -a optimal /dev/sda

* mklabel gpt
* print
* remove remaining partitions.(if there are any).
* unit mib
* mkpart primary 1 512
* name 1 boot
* set 1 boot on
* mkpart primary 512 -1
* name 2 rootfs
* print
* quit

mkfs.fat -F 32 /dev/sda1
mkfs.ext4 /dev/sda2

mount /dev/sda2 /mnt

tar xvfz ubuntu-base-20.04.1-base-amd64.tar.gz -C /mnt

cp /etc/resolv.conf /mnt/etc/resolv.conf

mount --rbind /sys /mnt/sys
mount --rbind /proc /mnt/proc
mount --rbind /dev /mnt/dev

chroot /mnt
mount /dev/sda1 /boot

apt-get update 
apt-get install --no-install-recommends grub-efi
apt-get install --no-install-recommends linux-image-5.4.0-48-generic
apt-get install --no-install-recommends initramfs-tools
apt-get install --no-install-recommends nano

nano -w /etc/default/grub 
```

          remove quiet splash
```
update-grub
grub-install --target=x86_64-efi --efi-directory=/boot

nano -w /etc/fstab 
----
/dev/sda1            /boot      vfat    defaults,noatime 0 2
/dev/sda2            /            ext4    noatime 0 1
----

adduser l3gi0n
addgroup l3gi0n adm
addgroup l3gi0n sudo

passwd root

exit
```

reboot



I am getting this Kernel Panic: [https://ibb.co/XFTKBtN](https://ibb.co/XFTKBtN)

What did I do wrong ?

---

### Post by QIII on 2020-10-20
Moved to Virtualisation

---

