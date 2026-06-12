---
title: "KVM problem with official documentation"
date: 2015-06-09
forum: Server Platforms
---

### Post by Mas_Musa on 2015-06-09
Hi,
I've been following the official documentation found at:[https://help.ubuntu.com/community/KVM/CreateGuests](https://help.ubuntu.com/community/KVM/CreateGuests)
However I've run into aome difficulty with the end of the script where it looks like the command doesn't work. Below is the code I've used.
```
ubuntu-vm-builder kvm trusty \ 
                 --domain mydomain.local \
                  --dest 11010 \
                  --arch amd64 \
                  --hostname 11010 \
                  --mem 512 \
                  --user myuser \
                  --pass abc123 \
                  --ip 192.168.3.200 \
                  --mask 255.255.255.0 \
                  --net 192.168.3.0 \
                  --bcast 192.168.3.255 \
                  --gw 192.168.3.1 \
                  --dns 192.168.3.26 \
                  --mirror http://mirrorservice.org/sites/archive.ubuntu.com/ubuntu \
                  --components main,universe \
                  --addpkg acpid \ 
                  --addpkg vim \
                  --addpkg openssh-server \
                  --addpkg avahi-daemon \
                  --libvirt qemu:///system ;
```

Here is the output 
```
2015-06-09 14:46:27,971 INFO    : logging to file: /tmp/tmpWoisE62015-06-09 14:46:28,000 INFO    : Calling hook: preflight_check
2015-06-09 14:46:28,004 INFO    : Calling hook: set_defaults
2015-06-09 14:46:28,004 INFO    : Calling hook: bootstrap
2015-06-09 14:47:48,244 INFO    : Calling hook: configure_os
2015-06-09 14:47:55,319 INFO    : invoke-rc.d: policy-rc.d denied execution of start.
2015-06-09 14:47:56,553 INFO    :
2015-06-09 14:47:56,553 INFO    : Current default time zone: 'Etc/UTC'
2015-06-09 14:47:56,555 INFO    : Local time is now:      Tue Jun  9 13:47:56 UTC 2015.
2015-06-09 14:47:56,555 INFO    : Universal Time is now:  Tue Jun  9 13:47:56 UTC 2015.
2015-06-09 14:47:56,555 INFO    :
Extracting templates from packages: 100%
2015-06-09 14:48:31,821 INFO    :
2015-06-09 14:48:31,821 INFO    : Current default time zone: 'Etc/UTC'
2015-06-09 14:48:31,824 INFO    : Local time is now:      Tue Jun  9 13:48:31 UTC 2015.
2015-06-09 14:48:31,824 INFO    : Universal Time is now:  Tue Jun  9 13:48:31 UTC 2015.
2015-06-09 14:48:31,824 INFO    : Run 'dpkg-reconfigure tzdata' if you wish to change it.
2015-06-09 14:48:31,824 INFO    :
2015-06-09 14:48:32,120 INFO    : invoke-rc.d: policy-rc.d denied execution of stop.
2015-06-09 14:48:35,289 INFO    : invoke-rc.d: policy-rc.d denied execution of stop.
2015-06-09 14:48:35,781 INFO    : invoke-rc.d: policy-rc.d denied execution of start.
2015-06-09 14:48:36,018 INFO    : invoke-rc.d: policy-rc.d denied execution of restart.
2015-06-09 14:48:36,427 INFO    : invoke-rc.d: policy-rc.d denied execution of start.
2015-06-09 14:48:37,174 INFO    : invoke-rc.d: policy-rc.d denied execution of restart.
2015-06-09 14:48:42,153 INFO    : Cleaning up
2015-06-09 14:48:42,154 INFO    : Calling hook: preflight_check
2015-06-09 14:48:42,155 INFO    : Calling hook: configure_networking
2015-06-09 14:48:42,197 INFO    : Calling hook: configure_mounting
2015-06-09 14:48:42,202 INFO    : Calling hook: mount_partitions
2015-06-09 14:48:42,202 INFO    : Mounting target filesystems
2015-06-09 14:48:42,202 INFO    : Creating disk image: "/tmp/tmpysaEVk" of size: 5120MB
2015-06-09 14:48:42,260 INFO    : Adding partition table to disk image: /tmp/tmpysaEVk
2015-06-09 14:52:42,582 INFO    : Adding type 4 partition to disk image: /tmp/tmpysaEVk
2015-06-09 14:52:42,583 INFO    : Partition at beginning of disk - reserving first cylinder
2015-06-09 14:56:42,826 INFO    : Adding type 3 partition to disk image: /tmp/tmpysaEVk
2015-06-09 14:56:42,834 INFO    : [0] ../../libparted/filesys.c:148 (ped_file_system_type_get): File system alias linux-swap(new) is deprecated
2015-06-09 15:00:43,094 INFO    : Creating loop devices corresponding to the created partitions
2015-06-09 15:00:43,117 INFO    : Creating file systems
2015-06-09 15:00:43,144 INFO    : mke2fs 1.42.9 (4-Feb-2014)
2015-06-09 15:00:43,451 INFO    : mkswap: /dev/mapper/loop0p2: warning: don't erase bootbits sectors
2015-06-09 15:00:43,452 INFO    :         on whole disk. Use -f to force.
2015-06-09 15:00:45,706 INFO    : Calling hook: install_bootloader
2015-06-09 15:00:52,057 INFO    : Removing update-grub hooks from /etc/kernel-img.conf in favour of
2015-06-09 15:00:52,057 INFO    : /etc/kernel/ hooks.
2015-06-09 15:00:52,168 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2015-06-09 15:00:52,234 INFO    : Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
2015-06-09 15:00:52,236 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2015-06-09 15:00:52,240 INFO    : Testing for an existing GRUB menu.lst file ...
2015-06-09 15:00:52,240 INFO    :
2015-06-09 15:00:52,241 INFO    : Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) /usr/sbin/update-grub: line 1094: read: read error: 0: Bad file descriptor
2015-06-09 15:00:54,840 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2015-06-09 15:00:54,905 INFO    : Searching for default file ... found: /boot/grub/default
2015-06-09 15:00:54,908 INFO    : Testing for an existing GRUB menu.lst file ...
2015-06-09 15:00:54,908 INFO    :
2015-06-09 15:00:54,909 INFO    : Could not find /boot/grub/menu.lst file.
2015-06-09 15:00:54,909 INFO    : Generating /boot/grub/menu.lst
2015-06-09 15:00:54,988 INFO    : Searching for splash image ... none found, skipping ...
2015-06-09 15:00:55,151 INFO    : grep: /boot/config*: No such file or directory
2015-06-09 15:00:55,242 INFO    : Updating /boot/grub/menu.lst ... done
2015-06-09 15:00:55,243 INFO    :
2015-06-09 15:00:55,419 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2015-06-09 15:00:55,484 INFO    : Searching for default file ... found: /boot/grub/default
2015-06-09 15:00:55,487 INFO    : Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
2015-06-09 15:00:55,611 INFO    : Searching for splash image ... none found, skipping ...
2015-06-09 15:00:55,642 INFO    : grep: /boot/config*: No such file or directory
2015-06-09 15:00:55,737 INFO    : Updating /boot/grub/menu.lst ... done
2015-06-09 15:00:55,737 INFO    :
2015-06-09 15:00:55,782 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2015-06-09 15:00:55,811 INFO    : Calling hook: install_kernel
2015-06-09 15:01:03,472 INFO    : grep: /proc/cpuinfo: No such file or directory
2015-06-09 15:01:03,473 INFO    : This kernel does not support a non-PAE CPU.
2015-06-09 15:01:03,479 INFO    : dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-53-generic_3.13.0-53.89_amd64.deb (--unpack):
2015-06-09 15:01:03,479 INFO    :  subprocess new pre-installation script returned error exit status 1
2015-06-09 15:01:03,491 INFO    : Examining /etc/kernel/postrm.d .
2015-06-09 15:01:03,493 INFO    : run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
2015-06-09 15:01:03,495 INFO    : run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
2015-06-09 15:01:03,533 INFO    : Errors were encountered while processing:
2015-06-09 15:01:03,533 INFO    :  /var/cache/apt/archives/linux-image-3.13.0-53-generic_3.13.0-53.89_amd64.deb
2015-06-09 15:01:03,734 INFO    : E: Sub-process /usr/bin/dpkg returned an error code (1)
2015-06-09 15:01:03,735 INFO    : Cleaning up
2015-06-09 15:01:07,032 ERROR   : Process (['chroot', '/tmp/tmp6UHUsg', 'apt-get', '--force-yes', '-y', 'install', 'linux-image-virtual']) returned 100. stdout: Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  linux-image-3.13.0-53-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
  linux-headers-3.13.0-53-generic
The following NEW packages will be installed:
  linux-image-3.13.0-53-generic linux-image-virtual
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.1 MB of archives.
After this operation, 42.3 MB of additional disk space will be used.
Get:1 http://mirrorservice.org/sites/archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.13.0-53-generic amd64 3.13.0-53.89 [15.1 MB]
Get:2 http://mirrorservice.org/sites/archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-virtual amd64 3.13.0.53.60 [2348 B]
Fetched 15.1 MB in 6s (2175 kB/s)
Selecting previously unselected package linux-image-3.13.0-53-generic.
(Reading database ... 11781 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-53-generic_3.13.0-53.89_amd64.deb ...
Selecting previously unselected package linux-image-virtual.
Preparing to unpack .../linux-image-virtual_3.13.0.53.60_amd64.deb ...
Unpacking linux-image-virtual (3.13.0.53.60) ...
, stderr: grep: /proc/cpuinfo: No such file or directory
This kernel does not support a non-PAE CPU.
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-53-generic_3.13.0-53.89_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-53-generic_3.13.0-53.89_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Traceback (most recent call last):
  File "/usr/bin/ubuntu-vm-builder", line 24, in <module>
    uvb.main()
  File "/usr/lib/python2.7/dist-packages/VMBuilder/contrib/cli.py", line 228, in main
    hypervisor.install_os()
  File "/usr/lib/python2.7/dist-packages/VMBuilder/hypervisor.py", line 70, in install_os
    self.call_hooks('install_kernel', self.chroot_dir)
  File "/usr/lib/python2.7/dist-packages/VMBuilder/distro.py", line 67, in call_hooks
    call_hooks(self, *args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/VMBuilder/util.py", line 159, in call_hooks
    getattr(plugin, func)(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/VMBuilder/plugins/ubuntu/distro.py", line 190, in install_kernel
    self.suite.install_kernel(destdir)
  File "/usr/lib/python2.7/dist-packages/VMBuilder/plugins/ubuntu/dapper.py", line 307, in install_kernel
    run_cmd('chroot', destdir, 'apt-get', '--force-yes', '-y', 'install', self.kernel_name(), env={ 'DEBIAN_FRONTEND' : 'noninteractive' })
  File "/usr/lib/python2.7/dist-packages/VMBuilder/util.py", line 120, in run_cmd
    raise VMBuilderException, "Process (%s) returned %d. stdout: %s, stderr: %s" % (args.__repr__(), status, mystdout.buf, mystderr.buf)
VMBuilder.exception.VMBuilderException: Process (['chroot', '/tmp/tmp6UHUsg', 'apt-get', '--force-yes', '-y', 'install', 'linux-image-virtual']) returned 100. stdout: Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  linux-image-3.13.0-53-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
  linux-headers-3.13.0-53-generic
The following NEW packages will be installed:
  linux-image-3.13.0-53-generic linux-image-virtual
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 15.1 MB of archives.
After this operation, 42.3 MB of additional disk space will be used.
Get:1 http://mirrorservice.org/sites/archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.13.0-53-generic amd64 3.13.0-53.89 [15.1 MB]
Get:2 http://mirrorservice.org/sites/archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-virtual amd64 3.13.0.53.60 [2348 B]
Fetched 15.1 MB in 6s (2175 kB/s)
Selecting previously unselected package linux-image-3.13.0-53-generic.
(Reading database ... 11781 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-53-generic_3.13.0-53.89_amd64.deb ...
Selecting previously unselected package linux-image-virtual.
Preparing to unpack .../linux-image-virtual_3.13.0.53.60_amd64.deb ...
Unpacking linux-image-virtual (3.13.0.53.60) ...
, stderr: grep: /proc/cpuinfo: No such file or directory
This kernel does not support a non-PAE CPU.
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-53-generic_3.13.0-53.89_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-53-generic /boot/vmlinuz-3.13.0-53-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-53-generic_3.13.0-53.89_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


vmbuilder.sh: 18: vmbuilder.sh: --addpkg: not found



```
Any help would be greatly appreciated.

---

### Post by cariboo on 2015-06-10
Why not use the repositories directly from the main server?

---

### Post by Mas_Musa on 2015-06-10
I've tried using the repositories from the main servers and the mirrors and local server and get the same error.

---

