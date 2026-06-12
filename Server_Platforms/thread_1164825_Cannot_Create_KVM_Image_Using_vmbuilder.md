---
title: "Cannot Create KVM Image Using vmbuilder"
date: 2009-05-20
forum: Server Platforms
---

### Post by madman1133 on 2009-05-20
Hi everyone,

I'm trying to build my fist KVM image using vmbuilder without any luck.  Everytime I try to run the vmbuilder command I get a python error.  Can someone please advise on what I should look at?

It looks like it's about to finish and just bombs out.  I am running Ubuntu 9.04 64bit Server.  Please help!!  :)

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

kvm@acmeis100:~$ sudo vmbuilder kvm ubuntu --suite jaunty --flavour virtual --arch i386  -o --libvirt qemu:///system
2009-05-20 00:59:07,514 INFO     Creating disk image: /tmp/vmbuilderWncuQE/disk0.img
2009-05-20 00:59:07,588 INFO     Adding partition table to disk image: /tmp/vmbuilderWncuQE/disk0.img
2009-05-20 00:59:07,699 INFO     Adding type 1 partition to disk image: /tmp/vmbuilderWncuQE/disk0.img
2009-05-20 00:59:07,708 INFO     Adding type 3 partition to disk image: /tmp/vmbuilderWncuQE/disk0.img
2009-05-20 00:59:07,717 INFO     Creating loop devices corresponding to the created partitions
2009-05-20 00:59:07,733 INFO     Creating file systems
2009-05-20 00:59:07,765 INFO     mke2fs 1.41.4 (27-Jan-2009)
2009-05-20 00:59:08,371 INFO     Mounting target filesystems
2009-05-20 00:59:08,383 INFO     Installing guest operating system. This might take some time...
2009-05-20 01:02:40,160 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-05-20 01:02:40,161 INFO     Moving old data out of the way
2009-05-20 01:02:40,161 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-05-20 01:02:40,306 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-05-20 01:02:40,349 INFO     Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
2009-05-20 01:02:40,351 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-05-20 01:02:40,356 INFO     Testing for an existing GRUB menu.lst file ...
2009-05-20 01:02:40,356 INFO
2009-05-20 01:02:40,357 INFO     Could not find /boot/grub/menu.lst file.
2009-05-20 01:02:40,357 INFO     Generating /boot/grub/menu.lst
2009-05-20 01:02:40,410 INFO     Searching for splash image ... none found, skipping ...
2009-05-20 01:02:40,513 INFO     grep: /boot/config*: No such file or directory
2009-05-20 01:02:40,580 INFO     Updating /boot/grub/menu.lst ... done
2009-05-20 01:02:40,580 INFO
2009-05-20 01:02:40,755 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-05-20 01:02:40,796 INFO     Searching for default file ... found: /boot/grub/default
2009-05-20 01:02:40,802 INFO     Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
2009-05-20 01:02:40,891 INFO     Searching for splash image ... none found, skipping ...
2009-05-20 01:02:40,915 INFO     grep: /boot/config*: No such file or directory
2009-05-20 01:02:40,975 INFO     Updating /boot/grub/menu.lst ... done
2009-05-20 01:02:40,975 INFO
2009-05-20 01:02:41,025 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-05-20 01:02:49,580 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-05-20 01:02:49,580 INFO     Done.
2009-05-20 01:02:52,373 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-05-20 01:02:52,373 INFO     Running depmod.
2009-05-20 01:02:52,374 INFO     update-initramfs: Generating /boot/initrd.img-2.6.28-11-server
2009-05-20 01:02:54,377 INFO     Running postinst hook script /usr/sbin/update-grub.
2009-05-20 01:02:54,378 INFO     Searching for GRUB installation directory ... found: /boot/grub
2009-05-20 01:02:54,378 INFO     Searching for default file ... found: /boot/grub/default
2009-05-20 01:02:54,379 INFO     Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
2009-05-20 01:02:54,608 INFO     Searching for splash image ... none found, skipping ...
2009-05-20 01:02:54,676 INFO     Found kernel: /boot/vmlinuz-2.6.28-11-server
2009-05-20 01:02:54,839 INFO     Replacing config file /var/run/grub/menu.lst with new version
2009-05-20 01:02:54,855 INFO     Updating /boot/grub/menu.lst ... done
2009-05-20 01:02:54,856 INFO
2009-05-20 01:02:56,360 INFO
2009-05-20 01:02:56,361 INFO     Current default timezone: 'America/Chicago'
2009-05-20 01:02:56,364 INFO     Local time is now:      Wed May 20 01:02:56 CDT 2009.
2009-05-20 01:02:56,365 INFO     Universal Time is now:  Wed May 20 06:02:56 UTC 2009.
2009-05-20 01:02:56,365 INFO
2009-05-20 01:02:59,345 INFO     update-initramfs: Generating /boot/initrd.img-2.6.28-11-server
2009-05-20 01:03:04,977 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-05-20 01:03:04,978 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-05-20 01:03:04,978 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-05-20 01:03:04,979 INFO     Can not write log, openpty() failed (/dev/pts not mounted?)
2009-05-20 01:03:04,980 INFO     grep: /proc/self/status: No such file or directory
2009-05-20 01:03:08,350 INFO     Copying to disk images
2009-05-20 01:03:15,482 INFO     Installing bootloader
2009-05-20 01:03:15,526 INFO     Cleaning up
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

---

### Post by honeydew on 2009-11-26
I am currently encountering the same issue.. trying to build jaunty virtual machines on a jaunty virtual machine

---

