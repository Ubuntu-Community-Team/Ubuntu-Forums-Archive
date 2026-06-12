---
title: "How to convert Wubi installed ubuntu drives to virtual machine OS for windows?"
date: 2013-04-09
forum: Virtualisation
---

### Post by Kaykha on 2013-04-09
Hi all Dears,
Some years ago I installed ubuntu 10.10 on my laptop through wubi and after installing too many important softwares suddenly its boot damaged and I could not repair it but since I have important softwares in it I saved its disks. now I need them again. Is it any way to convert the wubi drive to virtual disks under windows for programs like Vmware?
Now I have direct installation of ubuntu 12.04 on my laptop beside windows 7.
thanks a lot.

---

### Post by Kaykha on 2013-04-20
any idea?

---

### Post by bcbc on 2013-04-20
If it doesn't boot normally, how would you boot it in a VM? If it does boot normally then you can just add an entry for it in Grub and boot it. If you just want the data you can mount it and copy it.

What went wrong before and at what point did you copy the root.disk file (before or after it stopped booting)?

---

### Post by Kaykha on 2013-04-21
it doesn't boot normally. I copied the all disks after I couldn't repair its boot.

---

### Post by bcbc on 2013-04-21
You can mount it from your current Ubuntu install. Let's say it's on /dev/sda3

```
sudo mkdir /media/win
sudo mount /dev/sda3 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
nautilus /mnt/home
```

Steps above:
1. create mountpoint directory
2. mount host partition
3. loop mount root.disk
4. browse /home on old Wubi install with Nautilus

To unmount:
```
sudo umount /mnt
sudo umount /media/win
sudo rmdir /media/win
```

If you get any errors mounting it, you could report back.

Note that once you get it mounted and it looks okay, it's possible to chroot into the install and update it.

If you want to just try to boot it, (again assuming the host is on /dev/sda3 and the path to the root.disk is /ubuntu/disks/root.disk) you could try adding a custom entry to this file:
```
gksu gedit /etc/grub.d/40_custom
```
And make it look like this:
```
#!/bin/shexec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Old Wubi install' {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos3)'
        loopback loop0 /ubuntu/disks/root.disk
        set root=(loop0)
        linux   /vmlinuz root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
        initrd  /initrd.img
}

```

This will then appear at the bottom of your current grub menu

---

### Post by bcbc on 2013-04-21
PS after editing 40_custom you need to regenerate grub.cfg:
```
sudo update-grub
```

---

