---
title: "vmware machine does not boot when one drive in RAID array is removed"
date: 2011-06-13
forum: Server Platforms
---

### Post by brighty22 on 2011-06-13
Hi,

I decided to create a virtual machine, to get to know ubuntu server a bit better, before installing it on what will be a home server. The current setup has 4*2GB virtual HDDs, and these RAID arrays, created when I installed ubuntu:
[LIST]
[*]RAID1 /boot ~100MB
[*]RAID5 swap  ~500MB
[*]RAID5 /     ~5GB
[/LIST]
Each spans all 4 disks. If I remove any one of the virtual HDDs, the system boots, GRUB counts down to 0 and disappears, however after that there's just a black screen. No prompts, no errors, nothing. If I then terminate the machine using vmware, re-attach the disk, then boot it, the machine starts normally.

During ubuntu installation, I set the system not to boot when the RAID array is degraded; although I've read that it should boot into initramfs after 30 seconds, or give a prompt.

This is the first time I've set up RAID, so any help would be great...

Thanks :)

---

