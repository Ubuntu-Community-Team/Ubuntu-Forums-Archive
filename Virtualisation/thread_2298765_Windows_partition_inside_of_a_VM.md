---
title: "Windows partition inside of a VM"
date: 2015-10-13
forum: Virtualisation
---

### Post by crastopher on 2015-10-13
Alright, not sure if this is completely possible at this point, nor have I ever heard of it, but here goes nothing..

Alright, to break it down, here's my hard drive:

>Partition   | File  | System |   Mount    Label
>/dev/sda1 |  nfts |           | system reserve
>/dev/sda2 |  nfts |           |    Windows Install
>/dev/sda3 |  ext4|     /     | Ubuntu 14.04
>/dev/sda4 | swap|           |    Swap


I remote into my machine quite frequently form work via Teamviewer. However, I sometimes like to remote into W10 to apply updates to the few games I play on Windows. Is it possible to run my windows partition as a VM within Ubuntu? Basically, I want to be able to make changes to my Windows Install without ever actually booting into windows.

---

### Post by SeijiSensei on 2015-10-14
No, the virtual machine will have its own complete OS and is insulated from the host operating system.  A VM is another complete "machine" running on top of the host.

---

### Post by dik232 on 2015-10-15
There's this, but I've not tried it myself

[Use a real Windows 7 partition in Virtualbox / KVM / VMware Player under Linux]("http://fds-team.de/cms/articles/2013-12/use-a-real-windows-7-partition-in-virtualbox-kvm-vmware-player-u.html")

---

### Post by KillerKelvUK on 2015-10-17
So I'm going to slightly disagree with Sensei's post...

You can pass an entire disk through to a VM and the guest OS will just use this as normal, the resulting filesystem will look as it would if it were applied from a non-virtualised OS.  Whether you could successfully take your existing windows drive (sda2) an migrate that into a new VM within Ubuntu will be a challenge (prob a fun one getting the virt hardware close enough)...probably easier just the wipe the drive, pass it though clean to a new vm and re-install windows.  Now as to whether this is best practice or not then the answer is NO or at least don't give the vm write access to the disk...me I'm more cavalier :-)

[https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Virtualization_Administration_Guide/sect-Virtualization-Adding_storage_devices_to_guests-Adding_hard_drives_and_other_block_devices_to_a_guest.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Virtualization_Administration_Guide/sect-Virtualization-Adding_storage_devices_to_guests-Adding_hard_drives_and_other_block_devices_to_a_guest.html)

---

