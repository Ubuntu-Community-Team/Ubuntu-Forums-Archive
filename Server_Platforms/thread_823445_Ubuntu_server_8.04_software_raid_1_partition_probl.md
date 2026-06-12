---
title: "Ubuntu server 8.04 software raid 1 partition problem"
date: 2008-06-09
forum: Server Platforms
---

### Post by dismalfear on 2008-06-09
Hi

I have installed ubuntu server 8.04 on a brand new machine with 2 x 750GB seagate SATA drives. This will only be a fileserver.

I followed the following article in setting up the software RAID 1 during the installation process.
[http://bobbyallen.wordpress.com/2008/05/19/installing-ubuntu-with-a-software-raid1-configuration/]("http://bobbyallen.wordpress.com/2008/05/19/installing-ubuntu-with-a-software-raid1-configuration/")
AND [http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/")

I created 3 partitions:

1. 10GB mount point: "/"
2. 1GB mount point: "swap"
3. 739GB mount point "/addwork3". This is where 

Everything works fine, the system is able to boot and only the 3 RAID partitions are visible

The problem comes in when I actually check the disk size and usage with, "df -h /addwork3"

it reports the following
[B]size = 683G
used = 198M
avail = 649G
use% = 1%[/B]

Now the problem is that there is nothing on the partition. But it there is 56GB difference between the partition size as I created it and the reported size with "df -h". whats worse is that the available space is even less, but the it says that only 198MB is used.

Have anybody else experienced this problem, and if so how do I fix it?

---

### Post by robgolding63 on 2008-06-09
The space is used for formatting information - you can't get round it. At least you know it's not a problem, but it's normal.

I have a 500GB external drive for backups, and I can only store ~470GB of data, due to formatting.

Hope this helps!

Rob

---

### Post by dismalfear on 2008-06-09
Hi Rob

Thanx for the reply. Well if that is the case then we'll just have to live with the diskspace disappearing into space. The reason why i'm worried about this is because its almost 90GB that I cannot use.

---

### Post by Vaderdarth211 on 2008-06-09
That's way too much space, You should be loosing like maybe 5% of the drive or less. I don't know why, but that's all I can tell you.

Good Luck

---

### Post by dismalfear on 2008-06-10
Thats what I thought as well. I did however calculate that on my root partition and swap, there is 7 - 7.5% which is cannot be used. Now on the other partition there is also a 7.5% difference between the partition size of 739GB and the actual size displayed of 683GB.

BUT there is another 34GB that is missing.

I cant find any info on this problem so it seems as if it's only me.

So if thos of you who have setup software RAID 1 with ubuntu server gutsy can check your partition sizes and let me know what percentage you guys are losing, that would be great!

---

### Post by hyper_ch on 2008-06-10
Another thing is, when you buy a 750GB drive you won't get 750 GB (750 x 1024 x 1024 x 1024) but 750 X 1000 X 1000 X 1000 bytes.

750 GB = 805306368000 bytes
750 "GB" = 750000000000 bytes --> 698.5 GB

And out of that 698.5 GB you need to have a part for inodes.

---

### Post by dismalfear on 2008-06-10
Thank you very much Hyper_ch.

Using that and doing the further maths, then everything seems to work out.

---

### Post by hyper_ch on 2008-06-10
in some countries you can sue them because 750 "GB" does not equal 750 GB

---

### Post by Vaderdarth211 on 2008-06-10
> **hyper_ch said:**
> in some countries you can sue them because 750 "GB" does not equal 750 GB


Not in the US anymore.

---

