---
title: "Hard Drive Compatibility (Panp4n)"
date: 2011-05-01
forum: System76 Support
---

### Post by Derath on 2011-05-01
I was just wondering, is there a hardware limitation on against the hard drive in the panp4n? I know there is for memory, but I was unsure if there was for the hard drive. I am considering buying a 1TB WD drive (particularly [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136545")) and just wanted to check beforehand.

Thanks!
Derath/Jordan

---

### Post by Derath on 2011-05-01
So a little research, and it seems the 1tb is actually 12.5mm thick, and may not work, so if it doesn't would [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136546") 9.5mm work?

---

### Post by isantop on 2011-05-02
The HDD bay in your Pangolin should support any 9.5mm drive.

---

### Post by Derath on 2011-05-02
Ah, that's what I was afraid of... no 1TB for me then, looks like I'll shoot for the 750GB. Thanks!

---

### Post by Derath on 2011-05-17
While I know this is solved, I just wanted to document what I did to migrate a hard drive here, in case anyone else needs the info.

So I purchased a 750Gb hard drive to replace the 320G (10G sda1, 4g sda2, 306g sda3) that came with it, I hadn't thought too much on specifics at this time, just knew I would use Clonezilla and gParted Live CDs.

Once I got the new drive in, swapped drives inside the laptop (750gb now installed), and put the old 320 into a USB enclosure. Ran Clonezilla, copied the whole drive (like ghosting), started with gparted, resized the last partition (now should have 10g sda1, 4g sda2, and 736 sda3). Started the laptop and was greeted by the blinking cursor in the top left, okay no biggie, just need to reinstall grub2. Started the system off the USB drive, chrooted to the 750gb, and ran grub-install.

This is where the problem starts, I kept getting an error message when running grub install, specifically:

```
grub-setup: warn: This msdos-style partition label has no post-MBR gap; embedding won't be possible!
grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists.
            However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: If you really want blocklists, use --force.

```

So, used --force to get grub into the mbr, now the system will boot, but still need to --force every grub-install...

-------------------------------------------------------------------

**_****SOLUTION****_** 
(As well as what I SHOULD have done in the first place):

Started the laptop with gparted, blew away all the partitions on the 750, re-created them empty (to find that "optimal block size" is now 8mb, which threw everything off previously). After partitioned and formatted (now 20gb sda1, 4gb sda2, ~724gb [664GB reported] sda3), used gparted to go ahead and copy the partitions individually (rather than clone the whole disk).

When I start up, grub is there to greet me, and everything's fine, other than some lost gbs due to block sizing... Oh well, I still have plenty of room to fill

---

