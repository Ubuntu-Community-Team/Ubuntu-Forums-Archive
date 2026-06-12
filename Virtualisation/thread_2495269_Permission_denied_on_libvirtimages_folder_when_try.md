---
title: "Permission denied on libvirt/images folder when try to boot the VM"
date: 2024-02-13
forum: Virtualisation
---

### Post by mtech2023 on 2024-02-13
I was getting a permission denied on Could not open '/var/lib/libvirt/images/servername-sda when try to boot the VM which was migrated from VMware. I am using virt-v2v tool. 
but once I remove the disk and re-add it, it can boot up fine. It make me wonder it may not be a permission issue. 
Also this only happened when VM was migrating from VMware using virt-v2v. I have no issue with a new build VM in KVM.
The Ubuntu version is 23.04. 
Dose anyone has similar issue or any idea how to fix this?

error:

Error starting domain: internal error: process exited while connecting to monitor: 2024-02-13T15:21:41.609882Z qemu-system-x86_64: -blockdev {"driver":"file","filename":"/var/lib/libvirt/images/servername-sda","node-name":"libvirt-2-storage","auto-read-only":true,"discard":"unmap"}: Could not open '/var/lib/libvirt/images/servername-sda': Permission denied



Thank you.

---

### Post by TheFu on 2024-02-13
23.04 support ended.  Non-LTS releases really have a usuable 6-month support period.

Move to a supported release.  Today, the best choice for running KVM/QEMU would be the most recent LTS, which is 22.04.

If you suspect permissions issues and have some that work and some that don't, why not look at the permissions for the files that work and the files that don't work?  If they are the same, then it is something else causing the problem and you can move on.

---

### Post by mtech2023 on 2024-02-13
the reason i am using 23.04 is because the libvirt version on 22.04 has a bug. I will need to update the libvirt version to 8.7.0.1, but i could not find the way to update it, besides upgrade to 23.04. 

I did check the permission on libvirt/image folder. It seems i have enough permission. 
# file: home/ubuntu
# owner: ubuntu
# group: ubuntu
user::rwx
user:libvirt-qemu:r-x           #effective:r-x
group::r-x                      #effective:r-x
mask::r-x
other::---

---

### Post by TheFu on 2024-02-13
> **mtech2023 said:**
> the reason i am using 23.04 is because the libvirt version on 22.04 has a bug. I will need to update the libvirt version to 8.7.0.1, but i could not find the way to update it, besides upgrade to 23.04. 

I did check the permission on libvirt/image folder. It seems i have enough permission. 
# file: home/ubuntu
# owner: ubuntu
# group: ubuntu
user::rwx
user:libvirt-qemu:r-x           #effective:r-x
group::r-x                      #effective:r-x
mask::r-x
other::---

What's wrong with using **ls -al**?  Using ACLs often causes issues.  With KVM/QEMU and libvirt, I'd expect these permissions:
```
-rw-r--r-- 1 libvirt-qemu kvm   4667998208 Sep 23  2021 srv-2004-image.qcow2
-rw-rw---- 1 libvirt-qemu kvm     16361472 Mar 24  2020 super_grub2_disk_hybrid_2.04s1.iso
-rw-rw---- 1 libvirt-qemu kvm  36507222016 Feb  9 17:16 Win7Ult-Data2.img
-rw-rw---- 1 libvirt-qemu kvm  63166218240 Feb  9 17:16 Win7Ult-os.img

```
Definitely not ubuntu:ubuntu.  That's broken.  BTW, those files are in the default location on the VM host:  /var/lib/libvirt/images/.   Home directories are not the place for VMs using KVM.

I actually use LVM with most of my VMs, so no image files or any file system on the VMhost at all. The LV isn't mounted to the VM host.  The LV block storage is passed into the VM as block storage. The **ls** output above is for a few remaining "play" VMs and helpful ISOs that can be booted from to do more stuff.

---

### Post by MAFoElffen on 2024-02-14
Wait...

I use KVM on 20.04, 22.04, 23.10 & DEV 24.04. Just what "bug" are you referring to that has you at 23.04 and holding, without upgrading the interim release version to 23.10 to stay within the interim release support schedule?

And as TheFu Said, (in other words):

[LIST=1]
[*]The files should be owned by libvirt-qemu:kvm. 
[*]The permission should be set to 660. 
[*]You should be a member of the kvm & libvirt groups. 
[/LIST]

---

### Post by TheFu on 2024-02-14
And just for clarification, the end-user isn't running any KVM/QEMU VMs.  There's a daemon controlled by the libvirt-qemu user that manages the VMs.  My VMs are all running under the libvirt-qemu userid when I check the process table. For example, 

```
libvirt+    4401       1  0 Feb05 ?        00:40:28 qemu-system-x86_64 -enable-kvm -name .................
```

I'd be surprised if Proxmox was different.

---

### Post by MAFoElffen on 2024-02-14
+1 --- Having them owned by a user, then using an ACL to add them to what is usually native, is not what I would do. I would do that the other way, if desired. Adding a User to the native groups is what is the desired and accepted practice.
> **TheFu said:**
> I'd be surprised if Proxmox was different.
Being Proxmox is Debian Based using KVM & LXC, with their customized Debian kernel... I would say it follows the same conventions.

I just couldn't get into the, that Proxmox took over everything, and made it harder to customize what I wanted to tweak and tune. It added an undesired layer that I didn't want... (It was the same way with O-Virt).

I gave it a try. I gave it a chance. It didn't meet my requirements, by some imposed limitations. I moved on past the hype.

---

### Post by mtech2023 on 2024-02-14
> **MAFoElffen said:**
> Wait...

I use KVM on 20.04, 22.04, 23.10 & DEV 24.04. Just bug are you referring to that has you at 23.04 and holding, without upgrading the interim release version to 23.10 to stay within the interim release support schedule?

And as TheFu Said, (in other words):

[LIST=1]
[*]The files should be owned by libvirt-qumu:kvm.
[*]The permission should be set to 660.
[*]You should be a member of the kvm & libvirt groups.
[/LIST]


I checked the permission on the each disk under KVM default folder. it looks like when I use virt-v2v to migrate VM from VMware. the disk file is owned by the root (Node-sda),  but if I remove the disk using virt-manager and re-add the disk. the file will be owned by livert-quem and kvm which i can boot up VM just fine. Is this the by design, b/c VM is migrating from VMware and i use sudo virt-v2v command? 

ubuntu@noble123:~$ sudo ls -al /var/lib/libvirt/images
total 129384696
drwxr-x--x+ 2 root         root        4096 Feb  8 19:54 .
drwxr-xr-x  8 root         root        4096 Jan 26 15:15 ..
-rw-r--r--  1 root         root  4191682560 Feb  8 19:56 Node-sda **********************
-rw-rw-r--  1 libvirt-qemu kvm   5651695616 Nov 30 21:16 en-us_windows_server_2019_x64_dvd_f9475476.iso
-rw-rw-r--  1 libvirt-qemu kvm   2133391360 Nov 30 20:00 ubuntu-22.04.3-live-server-amd64.iso
-rw-------  1 libvirt-qemu kvm  26847870976 Feb 14 16:36 ubuntu22.04-sda
-rw-------  1 libvirt-qemu kvm  42956488704 Feb 14 16:42 win2k22-sda


#########################################################################
after re-add the disk from virt-manager

ubuntu@noble123:~$ sudo ls -al /var/lib/libvirt/images
-rw-r--r--  1 libvirt-qemu kvm   4193255424 Feb 14 16:42 Node-sda*************************
-rw-rw-r--  1 libvirt-qemu kvm   5651695616 Nov 30 21:16 en-us_windows_server_2019_x64_dvd_f9475476.iso
-rw-rw-r--  1 libvirt-qemu kvm   2133391360 Nov 30 20:00 ubuntu-22.04.3-live-server-amd64.iso
-rw-------  1 libvirt-qemu kvm  26847870976 Feb 14 16:36 ubuntu22.04-sda
-rw-------  1 libvirt-qemu kvm  42956488704 Feb 14 16:42 win2k22-sda

---

### Post by TheFu on 2024-02-14
According to the virt-v2v manpage, 
```
           When you run virt-v2v -o rhv as root, virt-v2v attempts to create files and
           directories with the correct ownership.  If you run virt-v2v as non-root, it will
           probably still work, but _you will need to manually change ownership_ after virt-v2v has
           finished.

```
You should fix the user, group, and permissions.  It isn't THAT hard. Script it.

---

### Post by mtech2023 on 2024-02-16
It seems the following method fix my issue. 
sudo vim /etc/apparmor.d/libvirt/libvirt-<code_hash>
---------
and add line with your disk file: "  /var/lib/libvirt/images/disk.img rwk,  " 

I think it probably i ran virt-v2v as root user, but when try to start the VM using virt-manager using my account. Once I add line, it fixed my issue. Thank you uvaal for the solution.

Now I am thinking if  I can run the virt-v2v without sudo. I probably won't get the permission issue.
Anyone know how to run virt-v2v as non-root user?

---

