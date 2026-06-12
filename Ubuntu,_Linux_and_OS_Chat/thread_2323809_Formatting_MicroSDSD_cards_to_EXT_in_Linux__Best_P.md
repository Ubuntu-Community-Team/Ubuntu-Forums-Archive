---
title: "Formatting MicroSD/SD cards to EXT in Linux | Best Practice?"
date: 2016-05-08
forum: Ubuntu, Linux and OS Chat
---

### Post by neu5eeCh on 2016-05-08
So, my daughter is having occasional troubles (copying/moving) with her MicroSD card and my guess is that it has to do with the exfat file system being a non-native file system (in linux).

I've been reading about reformatting SD cards to ext4 that come with a number of provisos -- most notably turning off journaling. I was just wondering if any of you have reformatted their SD card, have already thought through all this, and what's best practice?

Switching off journaling:

[http://superuser.com/questions/799233/why-i-cannot-format-a-microsd-to-ext4](http://superuser.com/questions/799233/why-i-cannot-format-a-microsd-to-ext4)

>  Try formatting without journaling and it should work:```


  mke2fs -t ext4 -O ^has_journal /dev/sdf1

```  Being an SD card, you probably don't want journaling enabled. 

This site:

[https://blogofterje.wordpress.com/2012/01/14/optimizing-fs-on-sd-card/](https://blogofterje.wordpress.com/2012/01/14/optimizing-fs-on-sd-card/)

Goes a step further:


```
**mkfs.ext4 -O ^has_journal -E stride=2,stripe-width=1024 -b 4096 -L [Volume Name]  /dev/[directory]**
```

Any other thoughts?

---

### Post by Bucky Ball on 2016-05-08
Just to the MicroSD card issue firstly. Do you have exfat-utils and exfat-fuse installed? I use sd cards all the time without issue (but I have found it was only necessary to install the exfat stuff mentioned for sdxc cards).

To format them, I simply use Gparted. Works for me just like making a partition on any other drive. Be aware that if you are using sdxc cards you may need to stick with exfat for them to operate at all.

You may find this of interest, [from here:]("http://www.lexar.com/support/sdxc-faqs")

>  What is SDXC?

SDXC&#8482; (SD Extended Capacity) is an SD&#8482; memory card format that is based on the SDA 3.0 specification. Today, SD and SDHC&#8482; cards, which are based on the SDA 2.0 specification, can reach capacities up to 32GB. The SDA 3.0 specification, on the other hand, enables SD cards to "extend" beyond this 32GB capacity limit and reach higher capacities: from 32GB up to 2TB.

SDXC memory cards use the newer "exFAT" file system that is more efficient for SDXC's large capacities, while SD and SDHC memory cards use the FAT32 file system. This difference is the reason that the new SDXC format is NOT backwards compatible with host devices that only take SD (128MB to 2GB) or SDHC (4GB to 32GB) cards.

---

### Post by sudodus on 2016-05-08
If you use the SD card for an installed system you had better switch off journaling. If you use it only to store files and move files between computers, you will probably not read and write too often, and you can consider to keep the journaling, which makes the system more robust.

I think the first method you describe (the simpler command line) should be enough.

If you have an ext4 file system already, you can turn journaling on and off with ***tune2fs***. There are also other tweaks, that are worthwhile. See this link

[Installation/UEFI-and-BIOS#Final_system_tweaks](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks)

---

### Post by neu5eeCh on 2016-05-08
Great! My thanks to both of you. I'll follow up your links. :)

**Edit:** And, yes, thanks, exfat-utils and fuse are installed. The problem occurs when copying from a Fat32 USB to the SD card. She gets an input/output error. I can successfully copy the files from the USB to SD card using Windows. (But it's only a handful of files that are problematic -- PDFs being among them).

---

### Post by mc4man on 2016-05-08
If having permissions on the card is desired then ext* would be fine. Otherwise it could be a hassle to use, I'd just use FAT myself

---

### Post by neu5eeCh on 2016-05-08
> **mc4man said:**
> If having permissions on the card is desired then ext* would be fine. Otherwise it could be a hassle to use, I'd just use FAT myself

The trouble is that she's getting input/output errors and it only  happens when using her Linux laptop (the same files copy without errors  on Windows). This makes me think Linux would be happier with a native  file system.

---

### Post by SeijiSensei on 2016-05-08
If you don't want journalling, then just format the device as ext2.
```
sudo mkfs -t ext2 /dev/sdb1
```

---

