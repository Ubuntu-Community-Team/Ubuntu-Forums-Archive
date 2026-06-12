---
title: "raid 1 and 5 result in grub rescue prompt"
date: 2010-12-12
forum: Server Platforms
---

### Post by smullie on 2010-12-12
Hi All,

I have 4 2Tb drives.
I have created the following partitions

disk 1
2gb bios grub
1gb for raid 1 /boot
25 gb for raid 1 /
1.9TB raid 5 for /home

disk 2
2gb bios grub
1gb for raid 1 /boot
25 gb for raid 1 /
1.9TB raid 5 for /home

disk 3
2gb not in use
1gb for spare raid 1 /boot
25 gb for spare raid 1 /
1.9TB raid 5 for /home

disk 1
2gb swap
1gb for spare raid 1 /boot
25 gb for spare raid 1 /
1.9TB raid 5 for /home

So i have 
MD0 for /boot (Disk 1 and 2 with 2 spare: disk 3 and 4)
MD1 for /root (Disk 1 and 2 with 2 spare: disk 3 and 4)
MD2 for /home (disk 1 to 4)

On disk 1 and 2 the bios grub partition
On disk 4 swap

All is created when installing server 10.04.1 when ask for partitioning. I use manual.

After installing (without errors) i have to reboot. The system boots and give me a grub rescue prompt.

What can i do to fix this?

When i installed 8.04 this way all was working fine (i used no bios grub partition, but i have red it was necessary on the grub2)

All help is appiciated

---

### Post by smullie on 2010-12-13
I have found it:
I had another disk connected to the system. When disconnected this the boot went fine.

This post can be closed.

---

