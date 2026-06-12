---
title: "[SOLVED] Vmbuilder: virtual machine created how to launch ?"
date: 2008-12-09
forum: Virtualisation
---

### Post by gecka on 2008-12-09
Hello,

I created a virtual machine using vmbuilder:

> $ sudo vmbuilder kvm ubuntu --suite intrepid --flavour virtual --arch i386 -o  --libvirt qemu:///system --ip 10.0.4.20 --part vmbuilder.partition --user user  --name user --pass default  --tmpfs - --firstboot boot.sh --firstlogin login.sh es[sudo] password for laurent: 
2008-12-10 09:21:17,518 INFO     Creating disk image: /tmp/vmbuilderqy6pgK/disk0.img
2008-12-10 09:21:17,521 INFO     Adding partition table to disk image: /tmp/vmbuilderqy6pgK/disk0.img
2008-12-10 09:21:17,582 INFO     Adding type 1 partition to disk image: /tmp/vmbuilderqy6pgK/disk0.img
2008-12-10 09:21:17,586 INFO     Adding type 3 partition to disk image: /tmp/vmbuilderqy6pgK/disk0.img
2008-12-10 09:21:17,592 INFO     Creating loop devices corresponding to the created partitions
2008-12-10 09:21:17,599 INFO     Creating file systems
2008-12-10 09:21:17,603 INFO     mke2fs 1.41.3 (12-Oct-2008)
2008-12-10 09:21:18,063 INFO     Creating disk image: /tmp/vmbuilderqy6pgK/disk1.img
2008-12-10 09:21:18,066 INFO     Adding partition table to disk image: /tmp/vmbuilderqy6pgK/disk1.img
2008-12-10 09:21:20,120 INFO     Adding type 1 partition to disk image: /tmp/vmbuilderqy6pgK/disk1.img
2008-12-10 09:21:20,125 INFO     Creating loop devices corresponding to the created partitions
2008-12-10 09:21:20,131 INFO     Creating file systems
2008-12-10 09:21:20,165 INFO     mke2fs 1.41.3 (12-Oct-2008)
2008-12-10 09:21:21,570 INFO     Mounting target filesystems
2008-12-10 09:21:21,579 INFO     Installing guest operating system. This might take some time...
2008-12-10 10:30:26,954 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:30:26,990 INFO     Moving old data out of the way
2008-12-10 10:30:27,327 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:30:28,064 INFO     Searching for GRUB installation directory ... found: /boot/grub
2008-12-10 10:30:28,592 INFO     Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
2008-12-10 10:30:28,593 INFO     Searching for GRUB installation directory ... found: /boot/grub
2008-12-10 10:30:28,598 INFO     Testing for an existing GRUB menu.lst file ...
2008-12-10 10:30:28,598 INFO     
2008-12-10 10:30:28,598 INFO     Could not find /boot/grub/menu.lst file.
2008-12-10 10:30:28,598 INFO     Generating /boot/grub/menu.lst
2008-12-10 10:30:28,637 INFO     Searching for splash image ... none found, skipping ...
2008-12-10 10:30:28,725 INFO     grep: /boot/config*: No such file or directory
2008-12-10 10:30:28,771 INFO     Updating /boot/grub/menu.lst ... done
2008-12-10 10:30:28,771 INFO     
2008-12-10 10:30:29,008 INFO     Searching for GRUB installation directory ... found: /boot/grub
2008-12-10 10:30:29,057 INFO     Searching for default file ... found: /boot/grub/default
2008-12-10 10:30:29,057 INFO     Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
2008-12-10 10:30:29,122 INFO     Searching for splash image ... none found, skipping ...
2008-12-10 10:30:29,145 INFO     grep: /boot/config*: No such file or directory
2008-12-10 10:30:29,193 INFO     Updating /boot/grub/menu.lst ... done
2008-12-10 10:30:29,193 INFO     
2008-12-10 10:30:29,327 INFO     Searching for GRUB installation directory ... found: /boot/grub
2008-12-10 10:34:12,545 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:34:12,719 INFO     Done.
2008-12-10 10:34:15,634 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:34:15,757 INFO     Running depmod.
2008-12-10 10:34:15,813 INFO     update-initramfs: Generating /boot/initrd.img-2.6.27-9-server
2008-12-10 10:34:17,881 INFO     Running postinst hook script /usr/sbin/update-grub.
2008-12-10 10:34:17,978 INFO     Searching for GRUB installation directory ... found: /boot/grub
2008-12-10 10:34:18,733 INFO     Searching for default file ... found: /boot/grub/default
2008-12-10 10:34:18,738 INFO     Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
2008-12-10 10:34:18,802 INFO     Searching for splash image ... none found, skipping ...
2008-12-10 10:34:18,825 INFO     grep: /boot/config*: No such file or directory
2008-12-10 10:34:18,834 INFO     Found kernel: /boot/vmlinuz-2.6.27-9-server
2008-12-10 10:34:18,891 INFO     Replacing config file /var/run/grub/menu.lst with new version
2008-12-10 10:34:18,906 INFO     Updating /boot/grub/menu.lst ... done
2008-12-10 10:34:18,918 INFO     
2008-12-10 10:35:49,728 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:35:50,034 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:35:50,294 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:35:50,624 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:35:51,074 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:35:51,351 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:35:51,827 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:35:52,185 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:35:52,454 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:35:52,800 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:35:52,955 INFO     find: `/var/cache/fontconfig': No such file or directory
2008-12-10 10:35:52,956 INFO     find: `/var/cache/fonts': No such file or directory
2008-12-10 10:35:52,956 INFO     find: `/var/cache/anthy': No such file or directory
2008-12-10 10:35:52,958 INFO     find: `/var/lib/belocs': No such file or directory
2008-12-10 10:35:52,958 INFO     find: `/var/lib/gconf': No such file or directory
2008-12-10 10:35:52,958 INFO     find: `/var/lib/defoma': No such file or directory
2008-12-10 10:35:52,959 INFO     find: `/var/log/installer': No such file or directory
2008-12-10 10:35:52,959 INFO     find: `/cdrom': No such file or directory
2008-12-10 10:35:52,959 INFO     find: `/media/cdrom': No such file or directory
2008-12-10 10:35:52,960 INFO     find: `/usr/share/fonts': No such file or directory
2008-12-10 10:35:52,960 INFO     find: `/var/lib/anthy': No such file or directory
2008-12-10 10:35:52,961 INFO     find: `/var/lib/defoma': No such file or directory
2008-12-10 10:35:53,039 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:35:53,494 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:35:53,706 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:35:56,831 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2008-12-10 10:35:57,986 INFO     Updating certificates in /etc/ssl/certs....done.
2008-12-10 10:35:57,986 INFO     Running hooks in /etc/ca-certificates/update.d....done.
2008-12-10 10:36:00,547 INFO     grep: /proc/self/status: No such file or directory
2008-12-10 10:36:01,845 INFO     Copying to disk images
2008-12-10 10:36:05,903 INFO     Installing bootloader
2008-12-10 10:36:14,649 INFO     Unmounting target filesystem
2008-12-10 10:36:14,813 INFO     Converting /tmp/vmbuilderqy6pgK/disk0.img to qcow2, format ubuntu-kvm/disk0.qcow2
2008-12-10 10:36:25,600 INFO     Converting /tmp/vmbuilderqy6pgK/disk1.img to qcow2, format ubuntu-kvm/disk1.qcow2
2008-12-10 10:36:46,642 INFO     Cleaning up


Nice.
Now I don't know how to launch, destroy or clone the VM. virsh list retuns no VM at all but the VM exists.

> $ ls /etc/libvirt/qemu/
networks  ubuntu.xml

Regards

---

### Post by maximd on 2009-01-07
> **gecka said:**
> 
Now I don't know how to launch, destroy or clone the VM. virsh list retuns no VM at all but the VM exists.


You can use virt-manager to see all your virtual machines.

If you want to use virsh, you can force the display of the inactive virtual machines with:
```

virsh list --inactive

```

Hope this helps.

---

### Post by gecka on 2009-01-09
> **maximd said:**
> Y
```

virsh list --inactive

```

Hope this helps.

Sure it helps. 
Ok I can see my VM with that command. Now how do I activate it?

---

### Post by gecka on 2009-01-09
```

# virsh start vmname

```

---

