---
title: "/etc/mdadm.conf - is it necessary?"
date: 2012-03-17
forum: Server Platforms
---

### Post by Krupski on 2012-03-17
Hi all,

I was working on my server (Ubuntu 11.04 64 bit with mdadm) and had temporarily renamed the config file to "_mdadm.conf" and forgot to change it back.

But the system booted and worked anyway!

So I removed it totally from /etc/mdadm as a test and the system still boots!

So, it seems as if it's not needed. Please let me know if it's needed and why (like maybe special situations)?

Thanks!

-- Roger

---

### Post by Cheesehead on 2012-03-17
mdadm is used to configure software RAID arrays.

Depending on the type of RAID array you have (or don't have anymore), individual disks may still be bootable.

If you don't use RAID (anymore), then you can safely remove it.

Personally, I use RAID for data only, and a separate, non-RAID volume for booting the system.

---

### Post by Krupski on 2012-03-17
> **Cheesehead said:**
> mdadm is used to configure software RAID arrays.

Depending on the type of RAID array you have (or don't have anymore), individual disks may still be bootable.

If you don't use RAID (anymore), then you can safely remove it.

Personally, I use RAID for data only, and a separate, non-RAID volume for booting the system.

My file server is five 2.0TB drives in a RAID-5 array. I boot from a small, separate SSD drive. The RAID array is only for data.

My question was that the system booted and ran just fine WITHOUT mdadm.conf... which made me wonder why it's there.

---

### Post by Cheesehead on 2012-03-18
It's there to provide your RAID array. Based on how you describe your setup, you probably need it.

Your system (except for the RAID arrays) should work fine without it...but your arrays won't work at all without it. Depends on how you originally created and configured your arrays.

One easy way of checking if your arrays are still working properly is: 'cat /proc/mdstat'

---

### Post by rubylaser on 2012-03-19
The metadata is written to the superblocks on your hard drives, which allows mdadm to automatically assemble them even without the mdadm.conf file as long as nothing ever goes wrong.  The file exists to tell mdadm the proper way to assemble your arrays.  To make a long story short, you need a mdadm.conf file.

---

