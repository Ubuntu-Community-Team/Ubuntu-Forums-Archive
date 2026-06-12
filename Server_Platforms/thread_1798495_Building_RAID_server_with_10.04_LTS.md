---
title: "Building RAID server with 10.04 LTS"
date: 2011-07-06
forum: Server Platforms
---

### Post by linuxnizer on 2011-07-06
Hi there,
  I've been running my dedicated server on Ubuntu 10.04 for 300 days non-stop so far (touch wood:)). I'm planning to purchase a dedicated server to host many large sites. The specs are Sandybridge Xeon with 16 bay x 2TB storage using RAID5 (Adaptec RAID 51645).
  I don't have experience with RAID, but I read that ext4 can only support filesystem up to 16TB, my plan for the system is to have 32TB of storage. How can I make Ubuntu run this configuration?

Also, can Ubuntu 10.04 recognize the Adaptec card? Going through Adaptec website there is no mention of drivers for Ubuntu (although many other distros are available).

Cheers,
Abdul

---

### Post by rubylaser on 2011-07-06
(16) 2TB disks in a RAID5 would be insane, if you want to protect your data (rebuild times in the event of a disk failure will be lengthly and you could lose another disk causing your whole array to fail).  I would suggest at a minimum RAID6, or even better, RAID10.

Also,  (16) 2TB disks in RAID5 would only give you 30TB after parity, 28TB in RAID6, or 16TB in RAID10.  Here's a [comparison]("http://superuser.com/questions/266950/what-filesystem-should-i-use-for-a-large-amount-of-disk-space-in-linux-32tb") of various linux filesystems for large arrays.

---

### Post by linuxnizer on 2011-07-06
Thanks Ruby for the suggestion, I still need to know if Ubuntu can support filesystem larger than 16TB & if Ubuntu can support Adaptec RAID cards.

---

### Post by rubylaser on 2011-07-06
Yes to both.  That link my my previous post shows some of the shortcomings of each common filesystem, XFS is probably your best bet, unless, you want to use ESXi as the hypervisor, and use a [ZFS SAN]("http://www.napp-it.org/napp-it/all-in-one/index_en.html") for your fileshares for your web servers. Here's a link to Adaptec's Tech Specs for that [card]("http://www.adaptec.com/en-us/products/controllers/hardware/sas/performance/sas-51645/").

---

### Post by linuxnizer on 2011-07-06
Thanks again rubylaser, I'm not planning to run any Virtual servers, it's a bunch few storage hungry sites on this server.

* First point, I already checked Adaptec website for linux support  ([http://www.adaptec.com/en-us/_common/linux/](http://www.adaptec.com/en-us/_common/linux/)) couldn't find Ubuntu.

* Second point, I read that XFS is not as stable as ext4 (many places I can't remember now). Is this true?

Cheers,
Abdul

---

### Post by rubylaser on 2011-07-06
Ubuntu is Linux, so if it runs on the other versions of Linux, you "should" be fine.  Why don't you contact Adaptec or the seller to confirm?  I would personally be looking at this [card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816151094") instead.  It uses the fastest I/O processor currently avaialable, the ROC 800mhz, and it says it supports Linux, the 2.6.37 kernel supports it. Although, it is more pricey, it would allow you to expand to up to 24 drives in the future if you choose to.

XFS is stable and proven, but it can have a problem with power outages, or trying to do fscks on large arrays (the link from my first post).  EXT4 will not work in your case as the maximum filesystem that EXT4 can currently create is 16TB.  This is a good post about [XFS]("http://ubuntuforums.org/showpost.php?p=9941716&postcount=4").

---

### Post by linuxnizer on 2011-07-06
Thanks again,
  I did extensive search on RAID cards, Adaptec is the best in terms of quality/speed/price. the 51645 is about [$870 only ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816103217")(comes with dual core 1.2Ghz CPU). I don't need 24 ports since the 3U server I have can only accept 16 drives. 

  Also, I did contact Adaptec yesterday, still waiting for their response. 

I guess I need to more research on the filesystem part. Or just get the server loaded and play with it.

Cheers,
Abdul

---

