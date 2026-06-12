---
title: "Recommended hardware for a media server/NAS"
date: 2008-10-05
forum: Server Platforms
---

### Post by Xianath on 2008-10-05
Hi all,

I'm planning to set up a NAS/media server to feed my TV's MPEG2/4 decoder over UPnP/DLNA. I do not want to use hardware RAID but hardware media transcoding would be great. I am currently looking for hardware recommendations before I get to software. Specifically, here are some questions:

1) Motherboard. Is is worth pursuing the GA-EP45-DQ6 for its 10 SATA2 ports or should I go with a more modest board and use PCI or PCIe SATA boards? Also, would there be any benefit in bonding/teaming the four NICs and can the NIC hardware help in any way (like in some Broadcom NICs)?

2) Is there any benefit from multiple CPU cores to any of the following kernel components: software RAID, disk I/O, network stack, CIFS. In other words, would it make sense to go with a higher clock dual-core or a lower clock quad eg. the C2D E8500 vs. C2Q Q8200

3) Is there any worth in looking for a Linux-compatible MPEG2/4 card or should I just go with CoreAVC and hope it works in Linux mplayer as advertised?

4) It is my understanding that all SATA hard drives should be hot-swappable, and libata fully supports hotswap. Should I invest in a server case with hot-swappable trays, or can I just pop the hood and yank the disk? I'm hoping I won't have to do this too often :)

5) Is it better to have matching brand and model disks so they have similar performance, or a mix so that they are less likely to fail at similar times?

6) I am shooting for 10 disks but may expand this to 14 or even 18. Is it reasonable to expect software RAID5 to provide enough bandwidth for 1080p 4.1 playback?

I know these are a lot of questions but it looks like I'll be investing in this about a small car's worth and being a newbie enthusiast, could definitely use all the help I can get :) Thank you for your time.

Cheers,
Peter

---

