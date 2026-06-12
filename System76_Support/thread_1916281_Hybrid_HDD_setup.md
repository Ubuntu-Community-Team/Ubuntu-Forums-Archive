---
title: "Hybrid HDD setup"
date: 2012-01-27
forum: System76 Support
---

### Post by Therion87 on 2012-01-27
I'm thinking about getting a new Serval laptop with:

Nvidia GeForce GTX 560M Graphics with 1.5GB GDDR5 Video Memory
2nd Generation Intel Core i7-2860QM Processor ( 8MB L3 Cache, 2.50GHz )
16 GB Dual Channel DDR3 SDRAM at 1600MHz - 4 X 4GB
8X DVD±R/RW/4X +DL Super-Multi Drive 
                                                        Intel Centrino Ultimate-N 6300 - 802.11A/B/G/N Wireless LAN Module 

and I'm considering getting the, 500 GB 7200rpm SATA Hybrid Hard Drive with 4 GB SSD, how would you install a new operating system to utilize the SSD properly? Would you mount the /boot to it only or everything but, /home? And is the 4GB SSD large enough to complish this?

---

### Post by ubuntu27 on 2012-01-28
I never owned a Hybrid HD, but, it seems that you don't need to do a special install. 

The SSD part of the Hybrid HD will be used as time goes on. **The Hybrid saves the most frequently used files** regardless of the operating system or partitions on the hard drive.

[SSD vs HDD ]("http://ubuntuforums.org/showthread.php?t=1891800&highlight=hybrid")

---

### Post by isantop on 2012-01-30
> **ubuntu27 said:**
> I never owned a Hybrid HD, but, it seems that you don't need to do a special instal. 

The SSD part of the Hybrid HD will be used as time goes on. **The Hybrid saves the most frequently used files** regardless of the operating system or partitions on the hard drive.

[SSD vs HDD ]("http://ubuntuforums.org/showthread.php?t=1891800&highlight=hybrid")

This is just about 100% accurate. It requires no OS or user intervention. The entire setup is automatic.

---

### Post by Therion87 on 2012-01-30
I heard that you install the / filesystem to the SSD and mount the /home to the HDD for storage purposes. This will give you a huge performance boost as far as booting and running programs becasue they will be ran from the SSD which has far better performance than the HDD which will just be used for file storeage. Is this true and is that the proper setup?

---

### Post by MoebusNet on 2012-01-30
My hybrid HDD shows up in Gparted as a single 500Gb drive. I have read that the 4Gb SSD acts as a large cache for the drive.

The scenario you discuss would apply to a 2-drive setup with a separate SSD and HDD.

---

### Post by Therion87 on 2012-01-30
Ok that was the questions I was asking. It basically becomes the linux swap?

---

### Post by isantop on 2012-01-31
No, it stores sections on the disk that are frequently accessed. Particularly static data that is read more often than written, like the OS, common programs, maybe a few files.

By the way, we recommend against keeping partitions on two separate drives. If for any reason the drive with /home can't be mounted, you won't be able to log in. Additionally, it doesn't provide as large of a performance boost as you might think. Programs will load quickly off of the SSD, but it will then load the configuration files stored in your home folder from the slow HDD.

Instead, I recommend keeping /home on the SSD and using the HDD as storage. You might consider linking ~/Documents, ~/Music, ~/Downloads, etc. to folders on the hard drive. This will keep your configuration files together on the SSD and still allow you to log in if the HDD won't mount. You also won't take as large of a performance hit vs. using an SSD only.

---

### Post by Therion87 on 2012-01-31
Ok thanks for the replies.

---

