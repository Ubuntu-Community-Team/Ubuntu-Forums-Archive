---
title: "Partition over 2TB works until reboot... then limited to around 800gb?"
date: 2007-12-26
forum: Server Platforms
---

### Post by pgjensen on 2007-12-26
ubuntu 7.10 x64 server install with EFI GUID Partition support in kernel

here is what i've done:

parted /dev/sda
made it gpt and 5tb partition
rebooted

parted /dev/sda shows 5tb partition, all good :)

mkfs.xfs /dev/sda1
mount /dev/sda1 /storage
df --- shows 5tb, all good :)

reboot

mount /dev/sda1 /storage
df --- **SHOWS 800GB**

cfdisk of /dev/sda shows 800gb EFI and 4tb of free space (as i assume it should since it's limitiations on partiiton size)



**** i also did this with a truecrypt volume (created the 5tb truecrypt volume, then formatted it and it worked until reboot).  cfdisk /dev/mapper/truecrypt0 shows only 800gb of free space on that device too?  somehow not reading the gpt partition table correctly?


kernel is 2.6.22.9 64-bit
does this for xfs, jfs, reiserfs, ext3



what am i doing wrong for it to show 800gb post-reboot?  won't work again until i delete the partition, create a new one, and format it.  then stops after reboot again.

---

### Post by lswest on 2007-12-26
i'd say there seems to be a module or process which allows partitions to be greater than 800GB isnt running after boot, and only after you run GParted and create the partition using the create tool.  Not sure what the process could be, but maybe the info can help you figure it out?

---

### Post by pgjensen on 2007-12-26
the problem is with ubuntu

it installs parted 1.7.1 which has a known issue with GPT tables and not doing the ms-dos fake partition correctly, so upon reboot it corrupts and doesn't work.


i installed 1.8.8 with deb packages from [https://launchpad.net/~pgquiles/+archive](https://launchpad.net/~pgquiles/+archive) and got it to work


[/thread]

---

