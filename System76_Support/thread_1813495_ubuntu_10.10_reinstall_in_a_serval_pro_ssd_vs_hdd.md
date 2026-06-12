---
title: "ubuntu 10.10 reinstall in a serval pro ssd vs hdd"
date: 2011-07-27
forum: System76 Support
---

### Post by patjennings on 2011-07-27
Hi I am just writing because  i  am in the market for a new desktop replacement. I have a lemur as my main computer now and absolutely love it, so system 76 is definitly on top of my list. I really like the stats of the serval professional but am conflicted about whether to get the ssd or hdd option. I have heard the ssd is faster and less likely to break because of no moving parts, but have never used one before. I intend on using ubuntu 10.10 as it is my preferred os , so when reinstalling 10.10 is it  as straight forward as installing the os from the live disk the same way you would on a hdd or are there any extra steps. If it is not as easy I would probably opt for the cheaper hdd. I use ubuntu because it is easy and it usually just works for me. Any info would be appreciated. Thanks in advance.

---

### Post by luwenliang0611 on 2011-07-28
These things looked pretty good, and some that I can learn, and I hope to learn more on it!

---

### Post by pqwoerituytrueiwoq on 2011-07-30
personally i would use a ssd and a hdd
store all programs on the ssd and your stuff (and frequently changed files) on the hdd
```
SSD:
   /
HDD:
   /home
   /var
   /tmp
```
some people prefer to put /tmp on the ram

SSD=small and fast
HDD=large and slow

SSDs have a shorter life than a HDD but can handle more physical abuse
the reason for the shorter life span is that a ssd has a write limit

My fstab file
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb /               ext4    discard,errors=remount-ro,noatime,nodiratime 0       1
# /home was on /dev/sda5 during installation
UUID=5153a0b4-bfe4-4a91-82c9-f6cbfd5b2018 /home           ext4    defaults                             0       2
# /mnt/HardDisks was on /dev/sda6 during installation
UUID=51b2b46b-891c-490c-b8a6-a878595194b6 /mnt/HardDisks  ext4    defaults                             0       2
# /var was on /dev/sda1 during installation
UUID=5cae72de-be5c-4586-90ec-c65ce056555b /var            ext4    defaults                             0       2
# /tmp was made a ram disk after installation
tmpfs                                     /tmp            tmpfs   defaults,noatime,mode=1777           0       0
# swap was on /dev/sda7 during installation
UUID=4455f38b-2151-4243-831e-ebc2298b865f none            swap    sw                                   0       0

```

---

### Post by PabloH on 2011-07-30
If you can live with the smaller size and extra expense, get the SSD. It is sooo much faster. You can put a regular HD in the other drive bay (replacing optical media) or use ESATA or USB-III to access a larger external platter drive when needed (or use the network and mount a network drive).

The SSD does have a write limit, but the Intel drives are tested very heavily. Look at the drives MTBF rate. It is very high. Know that the larger the SSD drive, the longer it will last (more sustained writes it can absorb). 

I compile and write all my data to a 160GB SSD, and I give it little in the way of special treatment (almost a gig of data a day). A year later, no issues. Even with heavy usage, a large sized Intel SSD should last you five years.

---

### Post by patjennings on 2011-07-31
Thanks for the response everyone, right now I think i am leaning to the hdd despite the added speed of the ssd that everyone is talking about. The price and size are the main reasons, the extra steps in setting it up a very small reason. I do alot of reinstalls with my remastersys cds because I am always playing with new distros, and trying things out. This might ware out the ssd if I am understanding correctly. The truth is at this point I am spoiled with how much faster my computer is than everyone else i know, a little more speed at the price is not that important to me. Compared to all my friends who have windows and macs I am doing pretty good.

---

### Post by isantop on 2011-08-01
If you do decide to go with both (SSD and HDD), then we recommend *against* putting your /home partition on a separate disk, as it will cause problems if one is removed or the drive configuration changes, and your system would not be bootable as a result.

---

