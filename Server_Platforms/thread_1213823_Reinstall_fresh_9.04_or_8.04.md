---
title: "Reinstall fresh 9.04 or 8.04?"
date: 2009-07-15
forum: Server Platforms
---

### Post by Raymond Day on 2009-07-15
Hi. I want to just start all over. I have Ubuntu server and it's been running for years now. I think upgraded 3 times over it's self. I have some problums and know more about it now.

I have the 8.04 DVD to install it. But just checked and they have 9.04 out now. But it says 9.04 maintained until 2010 but 8.04 till April 2013.

What should I go with?

After I install it I want to try and get all my settings and files back on it. I have a hard drive were I can install it on and not over wight the old one so I can copy things. Like samba config and Apach settings. Things like that. It there even a guide text some place to say how to do this?

I guess 9.04 is not a good one or what because they stop maintaining it in 2010? Or is one comming out soon that will maintain post that? I could wait a little longer. But like to get it working good again soon.

-Raymond Day

---

### Post by n8bounds on 2009-07-15
This is mostly a matter of opinion, but has a lot to do with what you intend to do with the server. Web servers usually have web developers that like the latest apache and php versions. For almost everything else it probably comes down the hardware supported by the kernel. 8.04.2 will have older kernels. If they work fine on you hardware, and theres no specific package versions you need out of the non-LTS, there's no real reason to use anything but the LTS.

Another thing to consider is file system support. 8.04 does not support EXT4. If you intend to make a single volume larger than 16TB, this might be a consideration. If you can live with XFS or another non-ext fs, then you're still ok with the LTS.

---

### Post by Wim Sturkenboom on 2009-07-15
> 
Web servers usually have web developers that like the latest apache and php versions
Not me, but that's probably because I also have to maintain them. So the fact that I don't have to upgrade every 18 months would be far more benificial than the latest and greatest of apache and php.

Further I agree.

---

### Post by Raymond Day on 2009-07-15
I down loaded the ubuntu-9.04-server-amd64.iso. I am backing up my server with True Image Backup. Then I can use the drive to install ubuntu server. Then mount the TIB as a drive. It's still checking the backup. Says 3 hours left right now. I have to go to work soon and will see what I can do when I get back home tonight from work.

I like to format it in reiserfs is there a way to do that? It will be on a 1TB SATA drive.

I will check back here in about 8 hours from now and hope can install the ubuntu-9.04 with reiser File System at the start.

-Raymond Day

---

