---
title: "NTFS or ext3 for access from XP and feisty?"
date: 2007-08-11
forum: Windows
---

### Post by Kilgore_Trout on 2007-08-11
Hello All,

After getting somewhat familiar with ubuntu over the past year, I now find that I have to dual-boot with XP in order to use certain programs for work.

I have 2 hard drives in my system: one with the OS's and one for storage.  I would like to be able to access the storage drive from XP or Feisty Fawn.

After some research, it appears that instead of being stuck with FAT32 to accomplish this, there are now methods for XP to read/write ext3 (ext2 at least) ([ext2IFS]("http://www.fs-driver.org/faq.html")) and likewise for ubunto to read/write NTFS ([ntfs-3g]("http://www.ntfs-3g.org/")).

Does anyone have experience with either of these tools?  And is there a relative advantage to using one over the other?  (Stability, speed, etc.)  If it matters, the bulk of my computing time will probably be spent in XP, but I plan on backing up to an external drive from ubuntu.

Thanks

ps. I wasn't sure if this is the right place to post this, could somebody point me in the right direction if not?

---

### Post by odiseo77 on 2007-08-11
Hi, I have a similar situation to yours; what I've done is to make a NTFS partition for storage, installed ntfs-3g on ubuntu, et voilà, I have read-write access to this partition now... other people might suggest you using an ext3 partition for storage and installing some program on windows to have access to this partition, but, in my opinion, this could be dangerous because if you get some virus or something on windows, it could damage all the data on your ext3 partitions (including ubuntu's partition)... just my opinion (don't like the idea to have access to linux from windows).

---

### Post by Kilgore_Trout on 2007-08-11
Thanks odiseo,

This is an excellent point.  I am most concerned about stability and security, not so much speed at this point.

Have you had any trouble with ntfs-3g?

---

### Post by kulturloseramerikaner on 2007-08-11
Although I've heard that the driver that allows 'Nix to read/write to NTFS isn't quite as reliable as the one that allows Windoze to read/wrote to ext3, I have to agree.  Why put your secure OS in the hands of one w/ security holes a truck could navigate?

---

### Post by odiseo77 on 2007-08-11
Well, I've been using ntfs-3g for about a week only (I used to storage my data on a FAT32 partition before), and I haven't had any issue so far; ntfs-3g seems pretty stable to me :)

EDIT: oh, and it's quite easy to install and configure, all you have is to install it with apt-get, and change ntfs for ntfs-3g in your ntfs partition entry on /etc/fstab, and you're done.

---

### Post by HermanAB on 2007-08-11
Hmm, ntfs-3g is much preferable over FAT32.

Just my tuppence worth,

Herman

---

### Post by Kilgore_Trout on 2007-08-11
Sounds good to me, thanks much for the help.

---

