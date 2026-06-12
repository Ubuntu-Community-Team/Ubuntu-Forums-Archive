---
title: "cannot start VM using virsh?"
date: 2011-08-14
forum: Server Platforms
---

### Post by gobbledigook on 2011-08-14
hi,

i run 11.04 and wanted to play about with VM's a bit, one for a zabbix server is what i started with.

anyways i installed using the command below and when i try to start i get:
```
server@server:~$ virsh -c qemu:///system start zabbixvm
error: Failed to start domain zabbixvm
error: Failed to add tap interface to bridge 'br0': No such device

```

obviously i haven't configured the bridge yet... but i thought i would be able to start the machine to see if it worked :(

have i missed something? been following the guides [libvirt]("https://help.ubuntu.com/10.04/serverguide/C/libvirt.html") and [jeOS and vmbuilder]("https://help.ubuntu.com/10.04/serverguide/C/jeos-and-vmbuilder.html#jeos-finish-install")

```
server@server:~$ sudo vmbuilder kvm ubuntu --suite lucid --flavour server lpia --libvirt qemu:///system --ip 192.168.1.30 --user zabbixvm \
> --pass whatever --addpkg unattended-upgrades --mem 256 --hostname zabbixvm --bridge=br0
[sudo] password for server: 
2011-08-14 15:32:39,419 INFO    : Calling hook: preflight_check
2011-08-14 15:32:39,455 INFO    : Calling hook: set_defaults
2011-08-14 15:32:39,456 INFO    : Calling hook: bootstrap
2011-08-14 15:42:04,635 INFO    : Calling hook: configure_os
2011-08-14 15:42:39,024 INFO    : update-rc.d: warning: unattended-upgrades start runlevel arguments (none) do not match LSB Default-Start values (0 6)
2011-08-14 15:42:39,025 INFO    : update-rc.d: warning: unattended-upgrades stop runlevel arguments (0 6) do not match LSB Default-Stop values (none)
2011-08-14 15:42:42,413 INFO    : 
2011-08-14 15:42:42,414 INFO    : Current default time zone: 'Etc/UTC'
2011-08-14 15:42:42,420 INFO    : Local time is now:      Sun Aug 14 14:42:42 UTC 2011.
2011-08-14 15:42:42,420 INFO    : Universal Time is now:  Sun Aug 14 14:42:42 UTC 2011.
2011-08-14 15:42:42,420 INFO    : 
Extracting templates from packages: 100%
2011-08-14 15:43:37,272 INFO    : 
2011-08-14 15:43:37,273 INFO    : Current default time zone: 'Etc/UTC'
2011-08-14 15:43:37,279 INFO    : Local time is now:      Sun Aug 14 14:43:37 UTC 2011.
2011-08-14 15:43:37,279 INFO    : Universal Time is now:  Sun Aug 14 14:43:37 UTC 2011.
2011-08-14 15:43:37,279 INFO    : Run 'dpkg-reconfigure tzdata' if you wish to change it.
2011-08-14 15:43:37,280 INFO    : 
2011-08-14 15:44:51,899 INFO    : restart: Unknown instance: 
2011-08-14 15:44:52,438 INFO    : start: Unknown parameter: JOB
2011-08-14 15:44:53,840 INFO    : Calling hook: post_install
2011-08-14 15:44:53,841 INFO    : Cleaning up
2011-08-14 15:44:53,843 INFO    : Calling hook: preflight_check
2011-08-14 15:44:56,463 INFO    : Calling hook: configure_networking
2011-08-14 15:44:56,494 INFO    : Calling hook: configure_mounting
2011-08-14 15:44:56,499 INFO    : Calling hook: mount_partitions
2011-08-14 15:44:56,499 INFO    : Mounting target filesystems
2011-08-14 15:44:56,499 INFO    : Creating disk image: "/tmp/tmpROuda6" of size: 5120MB
2011-08-14 15:44:56,571 INFO    : Adding partition table to disk image: /tmp/tmpROuda6
2011-08-14 15:44:56,958 INFO    : Adding type 4 partition to disk image: /tmp/tmpROuda6
2011-08-14 15:44:56,959 INFO    : Partition at beginning of disk - reserving first cylinder
2011-08-14 15:44:57,019 INFO    : Adding type 3 partition to disk image: /tmp/tmpROuda6
2011-08-14 15:44:57,031 INFO    : [0] ../../libparted/filesys.c:148 (ped_file_system_type_get): File system alias linux-swap(new) is deprecated
2011-08-14 15:44:57,101 INFO    : Creating loop devices corresponding to the created partitions
2011-08-14 15:44:57,136 INFO    : Creating file systems
2011-08-14 15:44:57,416 INFO    : mke2fs 1.41.14 (22-Dec-2010)
2011-08-14 15:44:59,958 INFO    : mkswap: /dev/mapper/loop0p2: warning: don't erase bootbits sectors
2011-08-14 15:44:59,959 INFO    :         on whole disk. Use -f to force.
2011-08-14 15:45:19,735 INFO    : Calling hook: install_bootloader
2011-08-14 15:45:39,091 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2011-08-14 15:45:39,152 INFO    : Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
2011-08-14 15:45:39,154 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2011-08-14 15:45:39,164 INFO    : Testing for an existing GRUB menu.lst file ... 
2011-08-14 15:45:39,164 INFO    : 
2011-08-14 15:45:39,164 INFO    : Could not find /boot/grub/menu.lst file. 
2011-08-14 15:45:39,165 INFO    : Generating /boot/grub/menu.lst
2011-08-14 15:45:39,296 INFO    : Searching for splash image ... none found, skipping ...
2011-08-14 15:45:39,540 INFO    : grep: /boot/config*: No such file or directory
2011-08-14 15:45:39,695 INFO    : Updating /boot/grub/menu.lst ... done
2011-08-14 15:45:39,695 INFO    : 
2011-08-14 15:45:40,199 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2011-08-14 15:45:40,261 INFO    : Searching for default file ... found: /boot/grub/default
2011-08-14 15:45:40,271 INFO    : Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
2011-08-14 15:45:40,498 INFO    : Searching for splash image ... none found, skipping ...
2011-08-14 15:45:40,526 INFO    : grep: /boot/config*: No such file or directory
2011-08-14 15:45:40,677 INFO    : Updating /boot/grub/menu.lst ... done
2011-08-14 15:45:40,677 INFO    : 
2011-08-14 15:45:40,908 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2011-08-14 15:45:40,923 INFO    : Calling hook: install_kernel
2011-08-14 15:46:12,689 INFO    : Done.
2011-08-14 15:46:26,499 INFO    : Running depmod.
2011-08-14 15:46:26,948 INFO    : update-initramfs: Generating /boot/initrd.img-2.6.32-33-server
2011-08-14 15:46:27,907 INFO    : grep: /proc/modules: No such file or directory
2011-08-14 15:46:27,914 INFO    : grep: /proc/modules: No such file or directory
2011-08-14 15:46:27,921 INFO    : grep: /proc/modules: No such file or directory
2011-08-14 15:46:27,931 INFO    : grep: /proc/modules: No such file or directory
2011-08-14 15:46:28,635 INFO    : grep: /proc/modules: No such file or directory
2011-08-14 15:46:28,642 INFO    : grep: /proc/modules: No such file or directory
2011-08-14 15:46:29,307 INFO    : grep: /proc/modules: No such file or directory
2011-08-14 15:46:33,971 INFO    : Running postinst hook script /usr/sbin/update-grub.
2011-08-14 15:46:34,102 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2011-08-14 15:46:34,202 INFO    : Searching for default file ... found: /boot/grub/default
2011-08-14 15:46:34,206 INFO    : Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
2011-08-14 15:46:34,429 INFO    : Searching for splash image ... none found, skipping ...
2011-08-14 15:46:34,479 INFO    : Found kernel: /boot/vmlinuz-2.6.32-33-server
2011-08-14 15:46:34,796 INFO    : Replacing config file /var/run/grub/menu.lst with new version
2011-08-14 15:46:34,852 INFO    : Updating /boot/grub/menu.lst ... done
2011-08-14 15:46:34,852 INFO    : 
2011-08-14 15:46:36,492 INFO    : Calling hook: unmount_partitions
2011-08-14 15:46:36,494 INFO    : Unmounting target filesystem
2011-08-14 15:46:41,191 INFO    : Calling hook: convert
2011-08-14 15:46:41,193 INFO    : Converting /tmp/tmpROuda6 to qcow2, format ubuntu-kvm/tmpROuda6.qcow2
2011-08-14 15:47:15,245 INFO    : Calling hook: fix_ownership
2011-08-14 15:47:15,248 INFO    : Calling hook: deploy

```

---

### Post by gobbledigook on 2011-08-16
*bump*

---

### Post by ruffEdgz on 2011-08-16
Can you go back into your VM called 'zabbixvm' and remove the bridged NIC that you placed on it for now? If you can, that will probably solve your issue since it needs the NIC br0 to be active.

Cheers!

---

### Post by gobbledigook on 2011-08-18
sweet thanx!

still learning....

---

