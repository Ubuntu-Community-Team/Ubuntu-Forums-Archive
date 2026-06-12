---
title: "Using sfill -l -l on Ubuntu with SSD"
date: 2015-02-18
forum: Security
---

### Post by sergey25 on 2015-02-18
Hi. I'd like to erase empty space on my SSD (afaik, on SSD I need to erase only one time to make deleted information unrecoverable). It's Samsung 840 Pro 256gb. So, I have runned sudo sfill -l -l /home/ but it's working more than 30 mins.

The questions are:
1) am I doing everything right? I mean won't this command perform 35 rewrites and somehow corrupt my SSD
2) maybe here is any other way to erase empty space which is special for ssds?

---

### Post by HermanAB on 2015-02-20
Patience, young padawan...  SSDs are excruciatingly slow when writing.

The best solution is to encrypt your SSD with LUKS.  That way, if you need to erase it, just hit yourself upside the head with a brick to forget the password.

---

### Post by bashiergui on 2015-02-21
Sfill will do what you want but yes, it will overwrite free space 35 times. As long as you're not running sfill routinely it won't impact your ssd much. 

You might check out this thread which discusses some pitfalls in wiping only free space. [http://superuser.com/questions/19326/how-to-wipe-free-disk-space-in-linux](http://superuser.com/questions/19326/how-to-wipe-free-disk-space-in-linux)

---

### Post by oldfred on 2015-02-21
SSD do not overwrite existing data like hard drive. They have to have erased the block first. That is why we use trim to speed up the write, so it does not have to do erase first.
You probably can just delete everything and run trim, but these all suggest using hdparm and its tools:

 Erase SSD
[https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing](https://wiki.archlinux.org/index.php/SSD_Memory_Cell_Clearing)
[https://www.thomas-krenn.com/en/wiki/SSD_Secure_Erase](https://www.thomas-krenn.com/en/wiki/SSD_Secure_Erase)
[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

---

