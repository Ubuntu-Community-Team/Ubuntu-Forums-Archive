---
title: "Boot degraded raid 5"
date: 2011-09-26
forum: Server Platforms
---

### Post by beavemcgeave on 2011-09-26
Hi guys,

Edit: I've tried it again this morning and it's working!! So please ignore the first part but please feel free to comment on the last two questions I had at the bottom.

I'm trying to set up 4 2TB hard drives with software raid 5 for a new server installation. I've followed [this]("https://help.ubuntu.com/community/Installation/SoftwareRAID") guide  but it seems out dated and I believe I need a grub bios partition for my GPT partitioned HD (without it I can't install grub).

I've been able to create 3 partitions on each disk as followed:
1. grub bios
2. raid volume (for root install)
3. raid volume (for swap)

I have then created a raid 5 array for the raid volumes formatting the first as ext4 for root install and second as swap.

Grub boot loader is installed to each of the grub bios partitions (I assume). The system boots and is working.

My problem is when I take a hd out to test if it will still boot, it will get to grub option menu then the screen will go blank when the os is booted.

I have changed /etc/initramfs-tools/conf.d/mdadm setting to BOOT_DEGRADED=true.

Is there something missing from my set up?

I also have two other questions for my set up.
1. Is installing grub to each hard drive the best practice or can I create another raid5 array and just install it once?

2. When a drive fails, will I have to create the partitions on the new hard drive or will mdadm perform this when it repopulates the data?

Thank you for any help.

---

