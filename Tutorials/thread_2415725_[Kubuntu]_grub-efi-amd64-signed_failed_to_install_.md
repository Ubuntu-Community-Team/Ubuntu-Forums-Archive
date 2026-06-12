---
title: "[Kubuntu] grub-efi-amd64-signed failed to install during installation"
date: 2019-03-30
forum: Tutorials
---

### Post by karl96 on 2019-03-30
Ok so I was installing Kubuntu for a desktop system and the bootloader kept failing to install. I went online and could not find any solution to the problem:
```
grub-efi-amd64-signed failed to install
```

So I am posting the workaround here.

The issue is the installer is not correctly retrieving the packages on the installation CD.

So first thing we're going to do is mount the new system.
```
 sudo su 
```
```
 mount /dev/sda2 /mnt 
```
```
 mount -o proc proc /mnt/proc 
```
```
 mount -o sysfs sys /mnt/sys 
```
```
 mount -t bind dev /mnt/dev 
```

If you're on an EFI system don't forget to
```
 mount /dev/sda1 /mnt/boot/efi 
```

Then we need the WIFI to keep working so do this
```
 cp /etc/resolv.conf /mnt/etc/resolv.conf 
```

Now chroot into the new system.
```
 chroot /mnt 
```

And edit the sources.list so it can retrieve the GRUB packages online instead of fetching them locally from the disk.
```
 nano /etc/apt/sources.list 
```

Now we need to fetch GRUB
```
 apt-get update 
```
```
 apt-get install grub-efi-amd64-signed 
```

And install it
```
 grub-install /dev/sda 
```

Finally update it
```
 update-grub
```

Sorted. Hopefully didn't miss a step :)

This tutorial also shows you how to reinstall or update grub on any ubuntu as the general principles are the same :).

I've also just realized Kubuntu now has its own dedicated forum. It's been a while!

---

