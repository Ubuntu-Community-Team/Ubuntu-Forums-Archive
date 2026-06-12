---
title: "Problem while making virtualization with kvm on ubuntu 9.04"
date: 2009-08-03
forum: Server Platforms
---

### Post by marcogood411 on 2009-08-03
I want to use kvm to build a virtualization environment on ubuntu 9.04.

I follow this guide on Howtoforge :
[http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-9.04](http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-9.04)
But I failed, The console message is here.

```

[root@server ~] vmbuilder kvm ubuntu --suite=intrepid --flavour=virtual --arch=amd64 --mirror=http://archive.ubuntu.com/ubuntu -o --libvirt=qemu:///system --tmpfs=- --ip=172.25.3.1 --part=vmbuilder.partition --templates=mytemplates --user=administrator --name=Administrator --pass=howtoforge --addpkg=vim-nox --addpkg=unattended-upgrades --addpkg=acpid --firstboot=boot.sh --mem=256 --hostname=vm1 --bridge=br0

2009-08-04 10:47:01,358 INFO     Creating disk image: /tmp/vmbuilderY9w0fr/disk0.img
2009-08-04 10:47:01,369 INFO     Adding partition table to disk image: /tmp/vmbuilderY9w0fr/disk0.img
2009-08-04 10:47:01,414 INFO     Adding type 1 partition to disk image: /tmp/vmbuilderY9w0fr/disk0.img
2009-08-04 10:47:01,419 INFO     Adding type 3 partition to disk image: /tmp/vmbuilderY9w0fr/disk0.img
2009-08-04 10:47:01,453 INFO     Creating loop devices corresponding to the created partitions
2009-08-04 10:47:01,457 INFO     Creating file systems
2009-08-04 10:47:01,475 INFO     mke2fs 1.41.4 (27-Jan-2009)
2009-08-04 10:47:02,190 INFO     Creating disk image: /tmp/vmbuilderY9w0fr/disk1.img
2009-08-04 10:47:02,211 INFO     Adding partition table to disk image: /tmp/vmbuilderY9w0fr/disk1.img
2009-08-04 10:47:04,976 INFO     Adding type 1 partition to disk image: /tmp/vmbuilderY9w0fr/disk1.img
2009-08-04 10:47:05,010 INFO     Creating loop devices corresponding to the created partitions
2009-08-04 10:47:05,013 INFO     Creating file systems
2009-08-04 10:47:05,058 INFO     mke2fs 1.41.4 (27-Jan-2009)
2009-08-04 10:47:05,059 INFO     warning: 140 blocks unused.
2009-08-04 10:47:05,059 INFO     
2009-08-04 10:47:06,380 INFO     Mounting target filesystems
2009-08-04 10:47:06,421 INFO     Installing guest operating system. This might take some time...
^A bridge-utils
2009-08-04 10:55:45,655 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 10:55:45,752 INFO     Moving old data out of the way
2009-08-04 10:55:46,355 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 10:55:47,430 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-08-04 10:55:47,594 INFO     Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
2009-08-04 10:55:47,595 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-08-04 10:55:47,599 INFO     Testing for an existing GRUB menu.lst file ...
2009-08-04 10:55:47,599 INFO     
2009-08-04 10:55:47,599 INFO     Could not find /boot/grub/menu.lst file.
2009-08-04 10:55:47,600 INFO     Generating /boot/grub/menu.lst
2009-08-04 10:55:47,691 INFO     Searching for splash image ... none found, skipping ...
2009-08-04 10:55:47,808 INFO     grep: /boot/config*: No such file or directory
2009-08-04 10:55:47,882 INFO     Updating /boot/grub/menu.lst ... done
2009-08-04 10:55:47,883 INFO     
2009-08-04 10:55:48,050 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-08-04 10:55:48,141 INFO     Searching for default file ... found: /boot/grub/default
2009-08-04 10:55:48,144 INFO     Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
2009-08-04 10:55:48,338 INFO     Searching for splash image ... none found, skipping ...
2009-08-04 10:55:48,356 INFO     grep: /boot/config*: No such file or directory
2009-08-04 10:55:48,433 INFO     Updating /boot/grub/menu.lst ... done
2009-08-04 10:55:48,434 INFO     
2009-08-04 10:55:48,465 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-08-04 10:57:04,479 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 10:57:05,058 INFO     Done.
2009-08-04 10:57:08,128 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 10:57:08,129 INFO     Running depmod.
2009-08-04 10:57:08,129 INFO     update-initramfs: Generating /boot/initrd.img-2.6.27-14-server
2009-08-04 10:58:13,290 INFO     Running postinst hook script /usr/sbin/update-grub.
2009-08-04 10:58:13,821 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-08-04 10:58:15,824 INFO     Searching for default file ... found: /boot/grub/default
2009-08-04 10:58:15,825 INFO     Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
2009-08-04 10:58:17,827 INFO     Searching for splash image ... none found, skipping ...
2009-08-04 10:58:18,080 INFO     grep: /boot/config*: No such file or directory
2009-08-04 10:58:18,639 INFO     Found kernel: /boot/vmlinuz-2.6.27-14-server
2009-08-04 10:58:21,211 INFO     Replacing config file /var/run/grub/menu.lst with new version
2009-08-04 10:58:22,030 INFO     Updating /boot/grub/menu.lst ... done
2009-08-04 10:58:22,030 INFO     
2009-08-04 10:59:04,352 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 10:59:04,713 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 10:59:04,729 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 10:59:10,944 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 10:59:16,663 INFO     
2009-08-04 10:59:16,663 INFO     Current default timezone: 'Asia/Hong_Kong'
2009-08-04 10:59:16,665 INFO     Local time is now:      Tue Aug  4 10:59:16 HKT 2009.
2009-08-04 10:59:16,666 INFO     Universal Time is now:  Tue Aug  4 02:59:16 UTC 2009.
2009-08-04 10:59:16,666 INFO     
2009-08-04 10:59:18,944 INFO     update-initramfs: Generating /boot/initrd.img-2.6.27-14-server
Extracting templates from packages: 100%
2009-08-04 11:01:50,688 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:01:51,234 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:01:51,966 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:01:52,605 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:01:52,825 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:01:53,282 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:01:53,363 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:01:53,701 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:01:53,761 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:01:54,174 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:01:54,425 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:01:54,863 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:01:55,025 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:01:59,024 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:02:05,291 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:02:05,291 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:02:05,292 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:02:05,292 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:02:05,293 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:02:05,293 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:02:05,293 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:02:05,294 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:02:05,294 INFO     find: `/var/cache/fontconfig': No such file or directory
2009-08-04 11:02:05,294 INFO     find: `/var/cache/fonts': No such file or directory
2009-08-04 11:02:05,295 INFO     find: `/var/cache/anthy': No such file or directory
2009-08-04 11:02:05,295 INFO     find: `/var/lib/gconf': No such file or directory
2009-08-04 11:02:05,295 INFO     find: `/var/lib/defoma': No such file or directory
2009-08-04 11:02:05,295 INFO     find: `/var/log/installer': No such file or directory
2009-08-04 11:02:05,296 INFO     find: `/cdrom': No such file or directory
2009-08-04 11:02:05,296 INFO     find: `/media/cdrom': No such file or directory
2009-08-04 11:02:05,296 INFO     find: `/usr/share/fonts': No such file or directory
2009-08-04 11:02:05,297 INFO     find: `/var/lib/anthy': No such file or directory
2009-08-04 11:02:05,297 INFO     find: `/var/lib/defoma': No such file or directory
2009-08-04 11:02:05,368 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:02:05,994 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:02:06,175 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:02:06,744 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:02:07,016 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:02:07,704 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:02:08,359 INFO     
2009-08-04 11:02:08,360 INFO     Current default timezone: 'Asia/Hong_Kong'
2009-08-04 11:02:08,419 INFO     Local time is now:      Tue Aug  4 11:02:08 HKT 2009.
2009-08-04 11:02:08,420 INFO     Universal Time is now:  Tue Aug  4 03:02:08 UTC 2009.
2009-08-04 11:02:08,420 INFO     Run 'dpkg-reconfigure tzdata' if you wish to change it.
2009-08-04 11:02:08,420 INFO     
2009-08-04 11:02:08,455 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:02:21,791 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-08-04 11:04:13,231 INFO     Updating certificates in /etc/ssl/certs....done.
2009-08-04 11:04:13,360 INFO     Running hooks in /etc/ca-certificates/update.d....done.
2009-08-04 11:04:17,700 INFO     grep: /proc/self/status: No such file or directory
2009-08-04 11:04:24,800 INFO     update-initramfs: deferring update (trigger activated)
2009-08-04 11:05:34,794 INFO     Copying to disk images
2009-08-04 11:05:39,016 INFO     Installing bootloader
2009-08-04 11:05:39,030 INFO     Cleaning up
Traceback (most recent call last):
  File "/usr/bin/vmbuilder", line 29, in <module>
    VMBuilder.run()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/__init__.py", line 66, in run
    frontend.run()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/plugins/cli/__init__.py", line 67, in run
    vm.create()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/vm.py", line 457, in create
    self.install()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/vm.py", line 406, in install
    self.distro.install_bootloader()
  File "/usr/lib/python2.6/dist-packages/VMBuilder/plugins/ubuntu/distro.py", line 147, in install_bootloader
    EOT''')
  File "/usr/lib/python2.6/dist-packages/VMBuilder/util.py", line 106, in run_cmd
    proc = subprocess.Popen(args, stdin=stdin_arg, stderr=subprocess.PIPE, stdout=subprocess.PIPE, env=proc_env)
  File "/usr/lib/python2.6/subprocess.py", line 595, in __init__
    errread, errwrite)
  File "/usr/lib/python2.6/subprocess.py", line 1092, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

```

I got a lot of error while using KVM virtualization. At first, I got something like "mask = OxFFFF" error, I correct this by replacing the 0(zero) instead of O.
I have reinstall the system three time and I got the same error :confused:

Can anyone help me to finish the installation of building a VM on Ubuntu 9.04 ?

---

### Post by Revyver on 2009-09-13
I got this same error too, but I was able to fix it by specifying ```
--flavour server
``` rather than ```
--flavour virtual
``` as it implies in the tutorial. I realized this after finding this little note:

> Until Ubuntu 8.10, the virtual kernel was only built for 32 bit architecture, so if you want to define an amd64 machine on Hardy, you should use --flavour server instead.

Source: [http://jimmyg.org/blog/2009/an-introduction-to-kvm-and-jeos-images-on-ubuntu-intrepid.html](http://jimmyg.org/blog/2009/an-introduction-to-kvm-and-jeos-images-on-ubuntu-intrepid.html)

The same seems to apply for 9.04.

---

