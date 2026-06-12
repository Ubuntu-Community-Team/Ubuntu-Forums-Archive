---
title: "Recover Windows From Linux"
date: 2012-05-24
forum: Virtualisation
---

### Post by xvan on 2012-05-24
I don't know if this should be posted here, but it's a good discovery I just made.

Trying to free some space from my Windows partition y deleted the C:/BOOT folder.

I donwnloaded a Vista recovery iso but hadn't a CD to burn it.

As I couldn't make grub2 nor UNetbootin boot my windows iso, I gave VirtualBox a chance:
This is what I did:

Make a virtual disk that uses the real partition as indicated [here]("http://en.gentoo-wiki.com/wiki/Running_a_VirtualBox_Guest_from_a_Real_Partition"):

```
#List partitions:
sudo VBoxManage internalcommands listpartitions -rawdisk /dev/sda
#Make virtual disk:
sudo VBoxManage internalcommands createrawvmdk -filename myos.vmdk -rawdisk /dev/sda -partitions 1,3,4
```

I run virtualbox as root, and created a VM with the proper windows version an optical disk device and the vmdk just created.

Run the virtual machine, F12 for boot options, load the iso and boot from CD.

Let the recovery disk make it's magic.

I think this could be done to install any full OS in a real partition.

---

