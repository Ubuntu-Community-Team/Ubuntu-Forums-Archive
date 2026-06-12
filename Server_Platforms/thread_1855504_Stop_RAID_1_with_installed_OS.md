---
title: "Stop RAID 1 with installed OS"
date: 2011-10-06
forum: Server Platforms
---

### Post by YoshiHNS on 2011-10-06
I'm running a HP Proliant Microserver that I want to use as a file server on the network. I have 2 x 500GB RE4 drives that I set up in RAID 1 using the Ubuntu Server 11.04 install CD. I partitioned the drives into 3 partitions. One partition is root (EXT4), one is swap, and the other is NTFS (window file share). I got everything working and the RAID seems to be in order.

I loaded GPARTED in GNOME just to see what it said about the setup so far. Saw a couple flags on the drives. So for the hell of it, I decided to see if I could stop the RAID and verify each HD was set up right. That is, disasseble the raid back into individual drives with their partitions, check that the partitions are correct and sizing and that, and then rebuild the array again. I don't have any data (aside from OS) on the drives yet or anything special configured, so I don't have much to lose. And I'm looking at this as more of an academic exercise than anything else.

For reasons that make sense, I cannot stop the raid that has the swap or root partition on it. I was able to stop the NTFS partition no problem. I tried seeing if I flagged a disk as failed and removed it from the array if it would let me stop it then, thinking that, well, if a RAID only has 1 active disk, then it's not really a RAID array, is it. Still no go.

Other notes is that I do have a 250Gig drive and a spare RE4 drive that are available for use.

So what I'm looking for.

1) Is there a way to stop the array if it is the one your OS is installed on? Haven't tried a Live CD yet, but I can see that working. Maybe an option in GRUB?

2) Is it practical to have the OS on the RAID? Figured if a HD is going to crash, it will be the entire drive and not just a partition, so I might as well have the OS mirrored as well to save it. Still trying to educate myself on what would needed to be done if the OS (on a separate drive) crashed.

Any comments appreciated.

---

