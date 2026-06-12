---
title: "vmbuilder fails to create guest machine"
date: 2009-01-31
forum: Virtualisation
---

### Post by lblogic on 2009-01-31
Hi
I am try to build a kvm based virtual machine using vmbuilder, and following the instructions here [https://help.ubuntu.com/community/JeOSVMBuilder]("https://help.ubuntu.com/community/JeOSVMBuilder"). but i keep getting the following errors and the vm is not created.


```
~/vm5# sudo vmbuilder kvm ubuntu --suite intrepid --flavour virtual --arch i386 -o --libvirt qemu:///system --ip 10.0.4.20 --part vmbuilder.partition --user athlon64 --name athlon64 --pass default --tmpfs - --firstboot boot.sh --firstlogin login.sh
2009-01-31 16:55:55,059 INFO     Creating disk image: /tmp/vmbuilderdaJ0ig/disk0.img
2009-01-31 16:55:55,078 INFO     Adding partition table to disk image: /tmp/vmbuilderdaJ0ig/disk0.img
2009-01-31 16:55:55,171 INFO     Adding type 1 partition to disk image: /tmp/vmbuilderdaJ0ig/disk0.img
2009-01-31 16:55:55,180 INFO     Adding type 3 partition to disk image: /tmp/vmbuilderdaJ0ig/disk0.img
2009-01-31 16:55:55,189 INFO     Adding type 1 partition to disk image: /tmp/vmbuilderdaJ0ig/disk0.img
2009-01-31 16:55:55,199 INFO     Creating loop devices corresponding to the created partitions
2009-01-31 16:55:55,215 INFO     Creating file systems
2009-01-31 16:55:55,265 INFO     mke2fs 1.41.3 (12-Oct-2008)
2009-01-31 16:55:56,911 INFO     mke2fs 1.41.3 (12-Oct-2008)
2009-01-31 16:55:58,925 INFO     Mounting target filesystems
2009-01-31 16:55:59,353 INFO     Installing guest operating system. This might take some time...
vi2009-01-31 17:50:01,353 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:50:01,372 INFO     Moving old data out of the way
2009-01-31 17:50:01,462 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:50:02,011 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-01-31 17:50:02,442 INFO     Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
2009-01-31 17:50:02,445 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-01-31 17:50:02,452 INFO     Testing for an existing GRUB menu.lst file ...
2009-01-31 17:50:02,452 INFO
2009-01-31 17:50:02,452 INFO     Could not find /boot/grub/menu.lst file.
2009-01-31 17:50:02,453 INFO     Generating /boot/grub/menu.lst
2009-01-31 17:50:02,528 INFO     Searching for splash image ... none found, skipping ...
2009-01-31 17:50:02,685 INFO     grep: /boot/config*: No such file or directory
2009-01-31 17:50:02,768 INFO     Updating /boot/grub/menu.lst ... done
2009-01-31 17:50:02,768 INFO
2009-01-31 17:50:02,968 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-01-31 17:50:03,051 INFO     Searching for default file ... found: /boot/grub/default
2009-01-31 17:50:03,057 INFO     Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
2009-01-31 17:50:03,187 INFO     Searching for splash image ... none found, skipping ...
2009-01-31 17:50:03,222 INFO     grep: /boot/config*: No such file or directory
2009-01-31 17:50:03,308 INFO     Updating /boot/grub/menu.lst ... done
2009-01-31 17:50:03,308 INFO
2009-01-31 17:50:03,348 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-01-31 17:50:53,343 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:50:53,554 INFO     Done.
2009-01-31 17:50:56,397 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:50:56,397 INFO     Running depmod.
2009-01-31 17:50:56,398 INFO     update-initramfs: Generating /boot/initrd.img-2.6.27-11-server
2009-01-31 17:51:00,380 INFO     Running postinst hook script /usr/sbin/update-grub.
2009-01-31 17:51:00,547 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-01-31 17:51:00,933 INFO     Searching for default file ... found: /boot/grub/default
2009-01-31 17:51:00,940 INFO     Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
2009-01-31 17:51:01,327 INFO     Searching for splash image ... none found, skipping ...
2009-01-31 17:51:01,361 INFO     grep: /boot/config*: No such file or directory
2009-01-31 17:51:01,427 INFO     Found kernel: /boot/vmlinuz-2.6.27-11-server
2009-01-31 17:51:01,630 INFO     Replacing config file /var/run/grub/menu.lst with new version
2009-01-31 17:51:01,657 INFO     Updating /boot/grub/menu.lst ... done
2009-01-31 17:51:01,657 INFO
2009-01-31 17:52:04,655 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,655 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,656 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,657 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,657 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,658 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,658 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,659 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,660 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,660 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,661 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,661 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,662 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,662 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,663 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,664 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,664 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,665 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,665 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,666 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,667 INFO     find: `/var/cache/fontconfig': No such file or directory
2009-01-31 17:52:04,667 INFO     find: `/var/cache/fonts': No such file or directory
2009-01-31 17:52:04,668 INFO     find: `/var/cache/anthy': No such file or directory
2009-01-31 17:52:04,668 INFO     find: `/var/lib/belocs': No such file or directory
2009-01-31 17:52:04,669 INFO     find: `/var/lib/gconf': No such file or directory
2009-01-31 17:52:04,669 INFO     find: `/var/lib/defoma': No such file or directory
2009-01-31 17:52:04,670 INFO     find: `/var/log/installer': No such file or directory
2009-01-31 17:52:04,670 INFO     find: `/cdrom': No such file or directory
2009-01-31 17:52:04,671 INFO     find: `/media/cdrom': No such file or directory
2009-01-31 17:52:04,671 INFO     find: `/usr/share/fonts': No such file or directory
2009-01-31 17:52:04,672 INFO     find: `/var/lib/anthy': No such file or directory
2009-01-31 17:52:04,672 INFO     find: `/var/lib/defoma': No such file or directory
2009-01-31 17:52:04,673 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,673 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,674 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:04,674 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-01-31 17:52:12,344 INFO     Updating certificates in /etc/ssl/certs....done.
2009-01-31 17:52:12,345 INFO     Running hooks in /etc/ca-certificates/update.d....done.
2009-01-31 17:52:12,345 INFO     grep: /proc/self/status: No such file or directory
2009-01-31 17:52:12,346 INFO     update-initramfs: deferring update (trigger activated)
2009-01-31 17:52:16,098 INFO     Copying to disk images
2009-01-31 17:52:34,719 INFO     Installing bootloader
2009-01-31 17:52:35,096 INFO     Cleaning up
Traceback (most recent call last):
  File "/usr/bin/vmbuilder", line 29, in <module>
    VMBuilder.run()
  File "/usr/lib/python2.5/site-packages/VMBuilder/__init__.py", line 66, in run
    frontend.run()
  File "/usr/lib/python2.5/site-packages/VMBuilder/plugins/cli/__init__.py", line 67, in run
    vm.create()
  File "/usr/lib/python2.5/site-packages/VMBuilder/vm.py", line 441, in create
    self.install()
  File "/usr/lib/python2.5/site-packages/VMBuilder/vm.py", line 390, in install
    self.distro.install_bootloader()
  File "/usr/lib/python2.5/site-packages/VMBuilder/plugins/ubuntu/distro.py", line 129, in install_bootloader
    EOT''')
  File "/usr/lib/python2.5/site-packages/VMBuilder/util.py", line 106, in run_cmd
    proc = subprocess.Popen(args, stdin=stdin_arg, stderr=subprocess.PIPE, stdout=subprocess.PIPE, env=proc_env)
  File "/usr/lib/python2.5/subprocess.py", line 594, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1153, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

```
Thanks!

---

### Post by zklaus on 2009-02-19
I am having the same problem right now. Has anyone a solution, or a hint?

Thanks!
Klaus

---

### Post by zklaus on 2009-02-19
Solution is to install grub. Will file a bug report.

---

