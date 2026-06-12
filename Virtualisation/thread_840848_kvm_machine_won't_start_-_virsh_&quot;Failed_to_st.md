---
title: "kvm machine won't start - virsh &quot;Failed to start domain&quot;"
date: 2008-06-25
forum: Virtualisation
---

### Post by scottburton11 on 2008-06-25
Using the Ubuntu guide on Kernel Virtual Machines:

[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

I am trying to define a basic JeOS vm using ubuntu-vm-builder and it won't start in virsh.

```

kvmadmin@xserve7:/media/sda1/kvm$ virsh --connect qemu:///system
Connecting to uri: qemu:///system
Welcome to virsh, the virtualization interactive terminal.

Type:  'help' for help with commands
       'quit' to quit

virsh # list --all
 Id Name                 State
----------------------------------
  - ubuntu               shut off

virsh # start ubuntu
error: Failed to start domain ubuntu

virsh # 

```
No more details are provided. The virtual machine's log is empty. Nothing is printed in syslog.

Here's how I use ubuntu-vm-builder script to define a simple vm:

```

kvmadmin@xserve7:/media/sda1/kvm$ sudo ubuntu-vm-builder kvm hardy --libvirt qemu:///system

```


Everything works, except I get an error on the GRUB installation stage:

```

Setting up grub (0.97-29ubuntu21) ...


       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,0)
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=b1e5dc37-8d7f-4869-8b58-3da40002d418'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. 
Generating /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-16-server
Updating /boot/grub/menu.lst ... done

Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=b1e5dc37-8d7f-4869-8b58-3da40002d418'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-16-server
Updating /boot/grub/menu.lst ... done

Searching for GRUB installation directory ... found: /boot/grub
umount target
Connecting to uri: qemu:///system
Domain ubuntu defined from /tmp/vm-builder-QfQGoI2731

Done.  Images are in /media/sda1/kvm/ubuntu-vm-hardy-amd64.

```

Has some trouble with GRUB but nothing severe. I don't know about the "Unable to resolve UUID" bit. 

Does anyone know what's going on here?

---

### Post by scottburton11 on 2008-06-25
OK duh. 

Virtualization wasn't enabled in the BIOS. 

My bad.

Back to work, people.

---

