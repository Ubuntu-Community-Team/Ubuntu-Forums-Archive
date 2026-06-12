---
title: "VMware ESXi:  Need to copy guest to a larger disk."
date: 2014-05-27
forum: Virtualisation
---

### Post by 1clue on 2014-05-27
Hi,

I have VMware ESXi (the free version) hosting an Ubuntu Server 12.04 guest.  The guest was stupidly (by me) installed onto a too-small disk.

I've resized the disk but the partition table is still too small.  So instead I want to create a new virtual disk, create partitions, mount them and then do a file-by-file copy to the new setup.

Rather than the ridiculous default partition scheme I want to set up something reasonable.  Since the default is MBR partition table I'll stick with that to avoid hassles, but there's no way I'm going to use an extended partition when there are only 3 partitions.

So I want / and /boot and swap, and what I was thinking is this:

[LIST=1]
[*]Boot from system rescue cd
[*]mkdir /mnt/old
[*]mkdir /mnt/new
[*]mount /dev/whatever-root-is /mnt/old
[*]mount /dev/whatever-boot-is /mnt/old/boot
[*]mount /dev/whatever-newroot-is /mnt/new
[*]mount /dev/whatever-newboot-is /mnt/new/boot
[*]cd /mnt/old
[*]cp -rax . /mnt/new/
[/LIST]

Then chroot into /mnt/new, re-run grub and reboot.

Any problems with this approach?

Thanks.

Afterthought:  What I would rather do is make a GPT partition table, set up LVM and go that route.  I somehow think that's going to turn into a lot of problems.

Thanks.

---

### Post by TheFu on 2014-05-29
After resizing a vHDD, did you run gparted from a bootable.iso to resize the partitions?

---

### Post by 1clue on 2014-05-30
I made a new VM with a non-stupid partitioning scheme and am copying things over.

---

