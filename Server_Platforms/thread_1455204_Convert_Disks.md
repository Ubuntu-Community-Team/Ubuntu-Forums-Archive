---
title: "Convert Disks"
date: 2010-04-15
forum: Server Platforms
---

### Post by Vegan on 2010-04-15
Is there any tool to convert disks from say ex3 to ext4 or NTFS to ext4 etc. It would be easier when dealing with such a plethora of disk formats.

universality is a plus.

---

### Post by FuturePilot on 2010-04-15
You can convert Ext3 to Ext4 but you can't convert NTFS to Ext4. Those are two completely different file systems for two completely different operating systems.

[https://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4]("https://ext4.wiki.kernel.org/index.php/Ext4_Howto#Converting_an_ext3_filesystem_to_ext4")

---

### Post by HermanAB on 2010-04-15
You can backup and reformat.

If the disk is half full, then you can shrink the NTFS partition and create an ext3 partition, then copy the data and finally delete the NTFS partition and grow the ext3 partition.  However, the probability of something going wrong is high.

---

### Post by Vegan on 2010-04-15
I was simply wondering what options are available. I am slowly finding new ways to leverage Linux making it far more helpful.

---

