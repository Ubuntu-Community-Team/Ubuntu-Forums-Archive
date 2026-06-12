---
title: "CHS vs LBA in RAID5"
date: 2011-02-13
forum: Server Platforms
---

### Post by adlabens on 2011-02-13
I've purchased a couple of 1 tb drives that I've used as backups to my ~750 gb RAID5 array (4 disks, 250 gb each).  The two 1 tb drives I've purchased are the same model #, but it has been discontinued, tho there's a "comparable" (size, quality, cache, rpm, interface) drive available from the same mfgr.  But, they won't tell me CHS (Cylinders, heads, sectors) so that I can confirm it will be compatible when I want to upgrade my RAID5 to 1 tb drives from the current 250 gb drives.  

**If all the drives have the same capacity & are all LBA, do I need to care whether CHS matches or not???**

I'm currently running Ubuntu Server 8.04 LTS, and will probably be upgrading to 10.10 LTS within a few months.

Thank you!!!

---

### Post by elico on 2011-02-13
software raid array based on disk size and not on the CHS and this stuff.
so if you will want to use raid5 you will get the array in the size of the smallest driver in the array so..
your are ok to buy compatible drives.

---

### Post by adlabens on 2011-02-14
> **elico said:**
> software raid array based on disk size and not on the CHS and this stuff.
so if you will want to use raid5 you will get the array in the size of the smallest driver in the array so..
your are ok to buy compatible drives.

So, if there are 4 different drives that are from 4 different mfgrs, and they are all the same 1 tb size, with 33 mb cache, 7200 RPM, SATA3 interface, then they should all work and provide 1 tb space available to the RAID5 array (4 drives in array should yield 3 TB space).  **Is that right???**

I'm just making sure before I buy another with a different model # but the other parameters being the same.

Thanks,
David

---

### Post by elico on 2011-02-14
yes.
what you should know is that some HD size is a bit different from others which means the maximum loss you will get is less space let say 30-50 MB loss because one of the drives has less space then the others.

---

### Post by adlabens on 2011-02-14
Great!  I was seriously contemplating giving away the pair of 1 tb drives and ordering 4 of the exact same thing, all at once.  Now, I can simply add two more 1 tb drives and have the performance I need.

BTW, these are WD Caviar Black 1 tb drives, and the old model # has been discontinued, but there's a new one.  I believe that the only stated difference is that the old ones have 5 year warrantees and the new ones have but 3.  Otherwise, same cache, same nominal size, same rpm, same interface, etc.  This is good news.  Thank you for the confirmation (besides, who cares about 50 mb when you're talking terabytes - except maybe the first hard drive I bought was just 5 mb & it cost ... $500.00!!!).

---

