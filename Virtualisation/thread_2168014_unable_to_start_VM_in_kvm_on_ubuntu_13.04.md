---
title: "unable to start VM in kvm on ubuntu 13.04"
date: 2013-08-16
forum: Virtualisation
---

### Post by Allen_Chan on 2013-08-16
Hi All,

I am just starting to play with KVM. I am trying to follow instructions from different websites. It looks like the VM is created properly but i cannot start.
Please help.

root@home-server:~# cat /etc/debian_version 
wheezy/sid

root@home-server:~# uname -a
Linux home-server 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

root@home-server:~# ubuntu-vm-builder kvm quantal \
>                   --domain newvm \
>                   --dest newvm \
>                   --arch amd64 \
>                   --hostname testVM \
>                   --mem 1024 \
>                   --user john \
>                   --pass doe \
>                   --bridge br0 \
>                   --components main,universe,restricted \
>                   --addpkg linux-image-generic \
>                   --addpkg acpid \
>                   --addpkg vim \
>                   --addpkg openssh-server \
>                   --addpkg avahi-daemon \
>                   --libvirt qemu:///system;

2013-08-15 22:46:52,740 INFO    : Calling hook: preflight_check
2013-08-15 22:46:52,741 INFO    : Calling hook: set_defaults
2013-08-15 22:46:52,741 INFO    : Calling hook: bootstrap
2013-08-15 22:51:42,869 INFO    : Calling hook: configure_os
Extracting templates from packages: 100%
2013-08-15 22:52:55,969 INFO    : Done.
2013-08-15 22:53:18,914 INFO    : Running depmod.
2013-08-15 22:53:19,252 INFO    : update-initramfs: deferring update (hook will be called later)
2013-08-15 22:53:19,255 INFO    : Examining /etc/kernel/postinst.d.
2013-08-15 22:53:19,256 INFO    : run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
2013-08-15 22:53:19,257 INFO    : update-initramfs: Generating /boot/initrd.img-3.5.0-37-generic
2013-08-15 22:53:25,642 INFO    : Updating certificates in /etc/ssl/certs... 151 added, 0 removed; done.
2013-08-15 22:53:25,642 INFO    : Running hooks in /etc/ca-certificates/update.d....done.
2013-08-15 22:53:26,214 INFO    : invoke-rc.d: policy-rc.d denied execution of start.
2013-08-15 22:53:27,062 INFO    : invoke-rc.d: policy-rc.d denied execution of start.
2013-08-15 22:53:27,764 INFO    : invoke-rc.d: policy-rc.d denied execution of start.
2013-08-15 22:53:29,014 INFO    : Running depmod.
2013-08-15 22:53:29,350 INFO    : update-initramfs: deferring update (hook will be called later)
2013-08-15 22:53:29,358 INFO    : Examining /etc/kernel/postinst.d.
2013-08-15 22:53:29,358 INFO    : run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.5.0-37-generic /boot/vmlinuz-3.5.0-37-generic
2013-08-15 22:53:29,359 INFO    : update-initramfs: Generating /boot/initrd.img-3.5.0-37-generic
2013-08-15 22:53:33,967 INFO    : Creating SSH2 RSA key; this may take some time ...
2013-08-15 22:53:34,181 INFO    : Creating SSH2 DSA key; this may take some time ...
2013-08-15 22:53:34,184 INFO    : Creating SSH2 ECDSA key; this may take some time ...
2013-08-15 22:53:34,368 INFO    : invoke-rc.d: policy-rc.d denied execution of stop.
2013-08-15 22:53:34,369 INFO    : 
2013-08-15 22:53:34,369 INFO    : Warning: Fake initctl called, doing nothing
2013-08-15 22:53:34,369 INFO    : 
2013-08-15 22:53:34,369 INFO    : Warning: Fake initctl called, doing nothing
2013-08-15 22:53:35,758 INFO    : invoke-rc.d: policy-rc.d denied execution of force-reload.
2013-08-15 22:53:35,764 INFO    : invoke-rc.d: policy-rc.d denied execution of start.
2013-08-15 22:53:36,336 INFO    : 
2013-08-15 22:53:36,336 INFO    : Creating config file /etc/default/grub with new version
2013-08-15 22:53:36,473 INFO    : device node not found
2013-08-15 22:53:36,474 INFO    : device node not found
2013-08-15 22:53:36,475 INFO    : device node not found
2013-08-15 22:53:36,476 INFO    : device node not found
2013-08-15 22:53:36,507 INFO    : device node not found
2013-08-15 22:53:36,508 INFO    : device node not found
2013-08-15 22:53:36,509 INFO    : device node not found
2013-08-15 22:53:36,510 INFO    : device node not found
2013-08-15 22:53:36,542 INFO    : device node not found
2013-08-15 22:53:36,544 INFO    : device node not found
2013-08-15 22:53:36,545 INFO    : device node not found
2013-08-15 22:53:36,546 INFO    : device node not found
2013-08-15 22:53:36,580 INFO    : device node not found
2013-08-15 22:53:36,581 INFO    : device node not found
2013-08-15 22:53:36,582 INFO    : device node not found
2013-08-15 22:53:36,583 INFO    : device node not found
2013-08-15 22:53:36,618 INFO    : device node not found
2013-08-15 22:53:36,620 INFO    : device node not found
2013-08-15 22:53:36,621 INFO    : device node not found
2013-08-15 22:53:36,622 INFO    : device node not found
2013-08-15 22:53:36,658 INFO    : device node not found
2013-08-15 22:53:36,660 INFO    : device node not found
2013-08-15 22:53:36,661 INFO    : device node not found
2013-08-15 22:53:36,661 INFO    : device node not found
2013-08-15 22:53:36,700 INFO    : device node not found
2013-08-15 22:53:36,701 INFO    : device node not found
2013-08-15 22:53:36,702 INFO    : device node not found
2013-08-15 22:53:36,703 INFO    : device node not found
2013-08-15 22:53:36,710 INFO    : device node not found
2013-08-15 22:53:38,350 INFO    : 
2013-08-15 22:53:38,350 INFO    : Current default time zone: 'Etc/UTC'
2013-08-15 22:53:38,351 INFO    : Local time is now:      Fri Aug 16 05:53:38 UTC 2013.
2013-08-15 22:53:38,351 INFO    : Universal Time is now:  Fri Aug 16 05:53:38 UTC 2013.
2013-08-15 22:53:38,351 INFO    : 
Extracting templates from packages: 100%
2013-08-15 22:54:09,925 INFO    : gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
2013-08-15 22:54:09,926 INFO    : gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
2013-08-15 22:54:09,926 INFO    : gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
2013-08-15 22:54:09,927 INFO    : gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
2013-08-15 22:54:09,927 INFO    : gpg: Total number processed: 4
2013-08-15 22:54:09,927 INFO    : gpg:              unchanged: 4
2013-08-15 22:54:17,893 INFO    : invoke-rc.d: policy-rc.d denied execution of stop.
2013-08-15 22:54:22,261 INFO    : invoke-rc.d: policy-rc.d denied execution of restart.
2013-08-15 22:54:31,998 INFO    : Cleaning up
2013-08-15 22:54:31,999 INFO    : Calling hook: preflight_check
2013-08-15 22:54:32,014 INFO    : Calling hook: configure_networking
2013-08-15 22:54:32,020 INFO    : Calling hook: configure_mounting
2013-08-15 22:54:32,023 INFO    : Calling hook: mount_partitions
2013-08-15 22:54:32,023 INFO    : Mounting target filesystems
2013-08-15 22:54:32,023 INFO    : Creating disk image: "/tmp/tmp8uFTT4" of size: 5120MB
2013-08-15 22:54:32,028 INFO    : Adding partition table to disk image: /tmp/tmp8uFTT4
2013-08-15 22:54:32,061 INFO    : Adding type 4 partition to disk image: /tmp/tmp8uFTT4
2013-08-15 22:54:32,062 INFO    : Partition at beginning of disk - reserving first cylinder
2013-08-15 22:54:32,082 INFO    : Adding type 3 partition to disk image: /tmp/tmp8uFTT4
2013-08-15 22:54:32,085 INFO    : [0] ../../libparted/filesys.c:148 (ped_file_system_type_get): File system alias linux-swap(new) is deprecated
2013-08-15 22:54:32,091 INFO    : Creating loop devices corresponding to the created partitions
2013-08-15 22:54:32,094 INFO    : Creating file systems
2013-08-15 22:54:32,096 INFO    : mke2fs 1.42.5 (29-Jul-2012)
2013-08-15 22:54:32,702 INFO    : mkswap: /dev/mapper/loop0p2: warning: don't erase bootbits sectors
2013-08-15 22:54:32,702 INFO    :         on whole disk. Use -f to force.
2013-08-15 22:54:35,110 INFO    : Calling hook: install_bootloader
2013-08-15 22:54:41,488 INFO    : Removing update-grub hooks from /etc/kernel-img.conf in favour of
2013-08-15 22:54:41,488 INFO    : /etc/kernel/ hooks.
2013-08-15 22:54:41,536 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2013-08-15 22:54:41,592 INFO    : Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
2013-08-15 22:54:41,592 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2013-08-15 22:54:41,594 INFO    : Testing for an existing GRUB menu.lst file ... 
2013-08-15 22:54:41,594 INFO    : 
2013-08-15 22:54:41,595 INFO    : Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) /usr/sbin/update-grub: line 1094: read: read error: 0: Bad file descriptor
2013-08-15 22:54:46,346 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2013-08-15 22:54:46,400 INFO    : Searching for default file ... found: /boot/grub/default
2013-08-15 22:54:46,401 INFO    : Testing for an existing GRUB menu.lst file ... 
2013-08-15 22:54:46,401 INFO    : 
2013-08-15 22:54:46,401 INFO    : Could not find /boot/grub/menu.lst file. 
2013-08-15 22:54:46,401 INFO    : Generating /boot/grub/menu.lst
2013-08-15 22:54:46,428 INFO    : Searching for splash image ... none found, skipping ...
2013-08-15 22:54:46,506 INFO    : Found kernel: /boot/vmlinuz-3.5.0-37-generic
2013-08-15 22:54:46,558 INFO    : Updating /boot/grub/menu.lst ... done
2013-08-15 22:54:46,558 INFO    : 
2013-08-15 22:54:46,679 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2013-08-15 22:54:46,733 INFO    : Searching for default file ... found: /boot/grub/default
2013-08-15 22:54:46,735 INFO    : Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
2013-08-15 22:54:46,780 INFO    : Searching for splash image ... none found, skipping ...
2013-08-15 22:54:46,808 INFO    : Found kernel: /boot/vmlinuz-3.5.0-37-generic
2013-08-15 22:54:46,851 INFO    : Replacing config file /run/grub/menu.lst with new version
2013-08-15 22:54:46,863 INFO    : Updating /boot/grub/menu.lst ... done
2013-08-15 22:54:46,863 INFO    : 
2013-08-15 22:54:46,929 INFO    : Searching for GRUB installation directory ... found: /boot/grub
2013-08-15 22:54:46,932 INFO    : Calling hook: install_kernel
2013-08-15 22:54:48,312 INFO    : Calling hook: post_install
2013-08-15 22:54:48,312 INFO    : Calling hook: unmount_partitions
2013-08-15 22:54:48,312 INFO    : Unmounting target filesystem
2013-08-15 22:54:51,668 INFO    : Calling hook: convert
2013-08-15 22:54:51,668 INFO    : Converting /tmp/tmp8uFTT4 to qcow2, format newvm/tmp8uFTT4.qcow2
2013-08-15 22:54:53,691 INFO    : Calling hook: fix_ownership
2013-08-15 22:54:53,691 INFO    : Calling hook: deploy




root@home-server:~# virsh 'list --all'
 Id    Name                           State
----------------------------------------------------
 -     testVM                         shut off

root@home-server:~# virsh start testVM
error: Failed to start domain testVM
error: internal error process exited while connecting to monitor: W: kvm binary is deprecated, please use qemu-system-x86_64 instead
qemu-system-x86_64: -drive file=/root/newvm/tmp8uFTT4.qcow2,if=none,id=drive-ide0-0-0,format=qcow2: could not open disk image /root/newvm/tmp8uFTT4.qcow2: Permission denied


I have tried to change the permission of the file.

root@home-server:~/newvm# ls -lah
total 604M
drwxr-xr-x 2 root root 4.0K Aug 15 22:54 .
drwx------ 6 root root 4.0K Aug 15 22:55 ..
-rwxrwxrwx 1 root root 604M Aug 15 22:54 tmp8uFTT4.qcow2

---

### Post by TheFu on 2013-08-16
> **Allen_Chan said:**
> 
root@home-server:~/newvm# ls -lah
total 604M
drwxr-xr-x 2 root root 4.0K Aug 15 22:54 .
drwx------ 6 root root 4.0K Aug 15 22:55 ..
-rwxrwxrwx 1 root root 604M Aug 15 22:54 tmp8uFTT4.qcow2

If you look at the parent directory, you can see the permissions issue. Only root has read access.  On ubuntu, there is a virtualization group, libvirtd, so if you are a member of that group and setup the virtual HDD repository to let that group have control, life will be good.  Further, if you are a member of that group, then you can remotely manage VMs (create, run, modify, destroy, delete) using **virt-manager** from any machine in the world.  Of course, it runs over SSH, so that will need to be configured.

I have no idea how it works on Debian.

---

### Post by Allen_Chan on 2013-08-16
I chowned -R the parent directory to group libvirtd however after running the virsh command, the permissions is reset.

root@home-server:~# ls -lah newvm/
total 604M
drwxr-xr-x 2 libvirt-qemu libvirtd 4.0K Aug 15 22:54 .
drwx------ 6 root         root     4.0K Aug 15 22:55 ..
-rwxrwxrwx 1 libvirt-qemu libvirtd 604M Aug 15 22:54 tmp8uFTT4.qcow2

root@home-server:~# virsh start testVM
error: Failed to start domain testVM
error: internal error process exited while connecting to monitor: W: kvm binary is deprecated, please use qemu-system-x86_64 instead
qemu-system-x86_64: -drive file=/root/newvm/tmp8uFTT4.qcow2,if=none,id=drive-ide0-0-0,format=qcow2: could not open disk image /root/newvm/tmp8uFTT4.qcow2: Permission denied




root@home-server:~# ls -lah newvm/
total 604M
drwxr-xr-x 2 libvirt-qemu libvirtd 4.0K Aug 15 22:54 .
drwx------ 6 root         root     4.0K Aug 15 22:55 ..
-rwxrwxrwx 1 root         root     604M Aug 15 22:54 tmp8uFTT4.qcow2

---

### Post by TheFu on 2013-08-16
I was wrong.

I created a new VM as a test today. Did it through virt-manager using my own account (which is part of the libvirtd group).
```
-rw-------  1 root root 10485760000 2013-08-16 18:21 NewVM.img
```  However, the parent and grandparent dirs ARE owned by my normal account.

That KVM server is running 10.04. I don't use non-LTS systems here, so can't say anything about your specific release. Is there a reason you don't want to use **virt-manager**?  I did it all manually with Xen.  It is much easier to get the options correct with virt-manager. Plus there is lots of control (specific CPU models, disk cache modes, virtio, lots more).  I also manage a few 12.04 VM hosts with the same client.

On a 12.04 VM host, the perms are:```

drwx--s--x 3 root root 4096 Apr 23 18:37 images/
```  I doubt I would have changed that unless it wasn't mandatory.  I love file and directory permissions.  Inside that directory the image file ownership varies ...
```
-rw-rw---- 1 root         root     18253611008 Feb  3  2013 alfresco.img
-rw-rw---- 1 root         root      4294967296 May  4 07:28 chat.img
-rw-rw---- 1 root         root      8589934592 Feb  9  2013 dms44.img
-rw-rw---- 1 libvirt-qemu libvirtd  4294967296 Jun 16  2012 mon45.img
-rw-rw---- 1 libvirt-qemu kvm       4294967296 Aug 16 18:26 spammer.img
-rw-rw---- 1 libvirt-qemu kvm      15401484288 Aug 16 18:26 ubudesk.img
-rw-rw---- 1 libvirt-qemu kvm       6442450944 Aug 16 18:26 xen41.img
-rw-rw---- 1 libvirt-qemu kvm      27917287424 Aug 16 18:26 zcs43.img

``` 
All these are KVM VMs and they all work and can be managed remotely. Interesting.  

Now, I'm thinking there is an issue with your VM creation or settings. Sorry to send you on a wild chase in the wrong direction.  I've never used vm-builder (or whatever the name is), but I can ask some questions.
* did you already install the OS and login ... ever?
* did grub get written to the vdisk?
* have you removed the virtual ISO file from the VM for booting?
* can you add a virtual IMG file and boot it that way?  Perhaps with a gparted utility ISO?

Just some ideas. If you can't get a utility ISO running, then we ahve a VM settings problem.

---

### Post by Allen_Chan on 2013-08-16
I dont mind trying anything that works. The first few guides that i read used ubuntu-vm-builder and vmbuilder so thats what i went with.
Can you share sample syntax that you used to get your kvm images working?

Thanks

---

### Post by Allen_Chan on 2013-08-16
All my interactions is on the CLI since i am running Ubuntu Server with no X configured. I believe i saw that virt-manager is a GUI?

---

### Post by TheFu on 2013-08-16
> **Allen_Chan said:**
> All my interactions is on the CLI since i am running Ubuntu Server with no X configured. I believe i saw that virt-manager is a GUI?

Yes, it is a GUI - you don't run it on the server, you run it on your desktop.  You do have a Linux desktop, right?
The client connects to the KVM server through ssh, so be certain that a normal ssh connection from your client to the server works with keys. Ask if you dno't understand  or just look for a tutor that includes ssh-copy-id inside.  On the server, I do not connect as root. Rather, I connect as my normal ID.  That ID is in the groups spelled out previously.  If you've ever used VMware Player, workstation or virtualbox, you'll understand virt-manager. It really is bonehead easy, once you have it setup.

Managing 20-50 physical hosts with virt-manager should be easy.  Much more than that and you'll want to use more automation.

---

