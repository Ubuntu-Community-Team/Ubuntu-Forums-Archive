---
title: "Using Raid with the Server"
date: 2006-06-05
forum: Server Platforms
---

### Post by Graham Brown on 2006-06-05
Hi All!,
I'm new to this forum so please have patience!
I would like to set up the server software, (6.06) on a PCI PC with atwo disc Raid array. Does anyone have knowledge of a Raid SATA controller card which will work?
I have not set up a sever before, and so I would like to make sure that the disc controller 'will not get in the way'
Appreciate any suggestions.
Regards,
Graham.

---

### Post by juicybananahead on 2006-06-05
[QUOTE=Graham Brown]Hi All!,
I'm new to this forum so please have patience!
I would like to set up the server software, (6.06) on a PCI PC with atwo disc Raid array. Does anyone have knowledge of a Raid SATA controller card which will work?
I have not set up a sever before, and so I would like to make sure that the disc controller 'will not get in the way'
Appreciate any suggestions.
Regards,
Graham.[/QUOTE]
I'm using software (mdadm) RAID 5 with three SATA II drives and it was dead easy to set up! If you're going to have a lot of CPU cycles spare, consider software RAID as a cheap, efficient alternative to a RAID controller card.

---

### Post by linuxone on 2006-06-05
Hi,

[QUOTE=Graham Brown]I would like to set up the server software, (6.06) on a PCI PC with atwo disc Raid array. Does anyone have knowledge of a Raid SATA controller card which will work?[/QUOTE]

depending on the server load I won't recommand a software raid. A software raid might be (is) usable on small servers with less load. But on a real production server with important data I always recommend to use a hardware raid only.

Basicly Adaptec cards should be supported. Furthermore Highpoint and 3Ware controllers. Myself I'd get an 3Ware controller, I have good experiences with these, but they could be real expensive.

Important: check if your selected controller card really is supported from Linux - before you buy it! There exist many web pages with specific notices about this theme .... for example:

[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

The kernel doc is a good source, too.

Thomas

---

### Post by LordHunter317 on 2006-06-05
Hardware RAID for two disks is likely overkill.  The cheapest HW RAID controllers for SATA are $250 USD.  Doubtful any performance gains you'd see on only two disks are worth the cost.

Anything cheaper than that is "fakeraid" that is:[list][*]Probably not supported by the kernel[*]Software RAID anyway[/list]The only reason to ever support or use them over MD is so you can share a RAID between Windows and Linux.

---

### Post by haircut on 2006-06-06
[QUOTE=linuxone]depending on the server load I won't recommand a software raid. [/QUOTE]

Can you expand on this comment please. I guess we also need more details from the thread starter as to the use of the server.

When you say "Server Load" I guess you mean data transfer, this being new files added and old files being moved/deleted.

I'm currentlly running software RAID1 on 2 80G SATA drives. I decided on software RAID as I wasn't doing any critical data transfer, I wanted a simple way of backing up a diskdrive. The Server is going to be loaded up, as in CPU load but not data transfer.

So Graham Brown, I guess it all depends on what you are doing, unless you have already decided on a RAID controll to do the job.

---

### Post by DarthOverlord on 2006-06-06
[QUOTE=haircut]Can you expand on this comment please. I guess we also need more details from the thread starter as to the use of the server.

When you say "Server Load" I guess you mean data transfer, this being new files added and old files being moved/deleted.

I'm currentlly running software RAID1 on 2 80G SATA drives. I decided on software RAID as I wasn't doing any critical data transfer, I wanted a simple way of backing up a diskdrive. The Server is going to be loaded up, as in CPU load but not data transfer.

So Graham Brown, I guess it all depends on what you are doing, unless you have already decided on a RAID controll to do the job.[/QUOTE]

I have an ECS board with NVRAID.  From what I researched it looks like I can't use the motherboard raid because it is not supported.  So I guess  I will need to use software raid.  

How hard is it to set up software raid 1. I want to use SATA 320 GB WD drives.  Do I keep the raid shut off in Bios?  Can I set this up as my secondary storage drive and put Ubuntu on another drive?  I also would like to keep the RAID 1 in FAT32.  

Any help in this would be much appreciated.

---

### Post by Graham Brown on 2006-06-06
[QUOTE=haircut]Can you expand on this comment please. I guess we also need more details from the thread starter as to the use of the server.

When you say "Server Load" I guess you mean data transfer, this being new files added and old files being moved/deleted.

I'm currentlly running software RAID1 on 2 80G SATA drives. I decided on software RAID as I wasn't doing any critical data transfer, I wanted a simple way of backing up a diskdrive. The Server is going to be loaded up, as in CPU load but not data transfer.

So Graham Brown, I guess it all depends on what you are doing, unless you have already decided on a RAID controll to do the job.[/QUOTE]

Thanks for the info, my main reason for the raid setup is to provide secure data storage, (mirror mode) it will be a simple, home system, so cpu cycles should be low. Later on I could be interested in including a mail/internet function to the server. I must admit that I have not considered the software raid option.
Graham.

---

### Post by chatuser on 2006-06-06
I have configured several RAID 1 mirrors following these instructions, I hope this link will be useful:

[http://www.debian-administration.org/users/philcore/weblog/4](http://www.debian-administration.org/users/philcore/weblog/4)

---

### Post by DarthOverlord on 2006-06-06
[QUOTE=chatuser]I have configured several RAID 1 mirrors following these instructions, I hope this link will be useful:

[http://www.debian-administration.org/users/philcore/weblog/4](http://www.debian-administration.org/users/philcore/weblog/4)[/QUOTE]

Thanks.  I looked at it quickly, it looks more like setting up RAID 1 for the Ubuntu install.  I want my data on a seperate FAT32 set of disks.  That way, I can migrate it to either a Windows or Mac system if needed.

---

