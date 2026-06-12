---
title: "Configuring RAID5 in Ubuntu Server 14.04.3 LTS"
date: 2016-02-25
forum: Server Platforms
---

### Post by dubhan.mcnamee on 2016-02-25
Hi All,
   
  I have am trying trying to install Ubuntu Server 14.04.3 LTS on a Lenovo ThinkServer RD650.
  I have already configured the server RAID to RAID5 and all disks are within this.
   
  I have entered gone through the usual install screens and entered the required network configuration settings.
  The part I am getting stuck with is the operating system picking up the SAS RAID disks. 

**1st install attempt.**
1.I tried to use 'Guided - use entire disk' in the 'Partition disks' section, which I thought would configure all of the drives
   in my RAID5 hardware array.
 
2. I used lsblk to looked at the drives after install.  sda seemed fine and had its swap space, sdb showed but could not 
be used.
=========================================================================================


**  **      **2nd Install Attempt**      

   

  I read up on Software Array configuration from the official Ubuntu documentation:
  [https://help.ubuntu.com/lts/serverguide/advanced-installation.html](https://help.ubuntu.com/lts/serverguide/advanced-installation.html)
  and referred to a couple of videos on Youtube (including The Urban Penquin) to try and assist.
   

  All pointed in the direction of 'Manual' partitioning of disks, I then follow the steps 

as instructed from the official Ubuntu documentation and Youtube videos. 
  

  It configured sda for physical volume use but it would not allow me to do this for sdb.

  I chose EXT4 for the setup of sdb instead.  However, after finishing going through the partitioning screens, the last screen
  'Partitions formatting' for sdb partition began to progress, this seemed to freeze at 33% and was still at this percentage overnight and
  this morning.  I will attempt a 'Manual' partition again today.
   
  Does anyone have any instructions/experience on how to set this up correctly so in the installation process  (for RAID5) so it picks up all disks/partitions
  in my server array, and has some allocated SWAP space?
   
  Thanks in advance,
  Dubhan

---

### Post by darkod on 2016-02-25
You are mixing things up. If you use the server raid controller/card and configure one or more raid5 arrays, then they are presented to the OS as simple disks. You do NOT raid them further with software raid. The raid is already done and that's it.

You use mdadm software raid only if the system is passing on the disks to the OS as simple disks, which in this case it is not.

If you created one raid5 array you will have only /dev/sda and that's it. If you created two arrays, you will have /dev/sda and /dev/sdb, etc.

I prefer mdadm raid but many servers are designed not to pass the disks as simple, instead you are obligated to use their raid. If this is your case too, you will have to either use the built-in raid card or see if there is a way to reflash it into non-raid mode. This option exists for many cards/controllers and makes the card only pass the disks as simple, it loses all raid capability (you can flash it back to raid mode in most cases if you decide to in the future).

As for guided or manual methods to partition your server, I always prefer manual because it gives you more options and full control. The guided method will install everything in one root partition, but you might want to separate the system into more partitions, etc... It's up to you.

PS. Some onboard controllers are more fakeraid than HW raid. Check this because creating the raid and how it works might differ a lot. It all depends on the specific case with your server.

---

### Post by dubhan.mcnamee on 2016-02-25
Hi Darkod,

Thats exactly what I am after, one raid5 array with just /dev/sda.  I just the free space in one partition.
The purpose of the server is just for file/data backups of big data, that are quickly filling up the existing Linux server.
The existing server was set up by a 3rd party provider before I started on this project.

I have attached soem screenshots of where I am up to in the install (.odt file).

Darkod can you confirm what 'mdadm raid' is and how it can be implemented when installing the server?


Many thanks,

Dubhan

---

### Post by darkod on 2016-02-25
mdadm is the SW raid in linux, the package is called mdadm. But you need to go step back, the screens don't show much. How does your raid controller work and how do you have it set up? Can it pass the disks without any raid or not?

Also, it shows two disks (which might be two arrays). How many physical disks do you have in the server? Because you can only do raid5 with three members or more.

---

### Post by MAFoElffen on 2016-02-26
@Darkod

I see his Lenovo 720ix raid controller (SATA 6Gb/s / SAS 12Gb/s), which is great. It can handle up to 26 drives. Supported in Linux since RHEL 5 through current. It has a very good track record... Modes: 0, 1, 10,5,6,50,60,JBOD. Uses the LSI SAS 2208 Dual-Core ROC, so works with the LSI MegaRAID Management Suite. Lenovo has a linux CLI tool for download from their support site.

@OP
I used to do hardware RAID exclusively. Now- Love mdadm. Support it. Use it. (But I still have some iron here on Hardware RAID... but I have "options" now.)

IMHO-- The only thing mdadm would give you over that hardware raid card is to be able to grow and shrink arrays. That part is very handy. If fact, I really love mdadm for it's flexibility. Your RAID card deals with physical drives as members. Linux Software Raid deals with partitions as members, so is a bit more flexible. You do not use them together. (just one or the other).

If you, for some reason, were to decide to do software RAID with your server and your RAID card, you would pass the drives through the card, setting the drives as jbod. (Named for: **J**ust a **B**unch **O**f **D**rives)

---

### Post by dubhan.mcnamee on 2016-02-26
Hi Darkod,

I have attached some screenshots (apologies they are a bit grainy due to max file upload size in forum) from ThinkServer Deployment Manager (TDM) showing the RAID.
The server has a total of 8 x 300GB SAS drives.

@MAFoElffen
The drives can be set to JBOD's.  Do you suggest I change the configuration on all 8 drives to JBOD?

You mention *'Your RAID card deals with physical drives as members. Linux Software  Raid deals with partitions as members, so is a bit more flexible. You do  not use them together. (just one or the other).'*
How do I skip the partitioning bit in the Ubuntu Server OS setup if already configured in the server RAID?

Please let me know what direction I should be heading in.

Thanks,
Dubhan

---

### Post by darkod on 2016-02-26
Why are you posting images inside text documents? You can attach images directly, that's much better for viewing too.

On the last image I can see two disk groups (but the text can't be read much). If those two disk groups mean two arrays, then the OS installer showing you sda and sdb fits perfectly. It seems what you have is two raid5 arrays of 4 disks each. Not counting the parity, with disks of 300GB that would give you around 900GB for each array. That is what the OS installer is showing you in the first images you posted.

First you have to decide what do you want to use, the server raid or the linux SW raid. I prefer the SW raid but if you prefer using the server raid that's fine too. Depending which option you go with, your next steps are something like:
Option 1 - Server raid
- Destroy these two arrays and create one single big array from all 8 disks. You said you want one big space and now it seems you have it divided in two, so you have to sort that out. But note that 8 disks are quite high number to be used in raid5 which has only single disk redundancy. It is not impossible to get two failures in which case your array will fail (because it can support only one filed member).
- After you create one big array start the ubuntu server installer again, and you can ask questions if you need help for the partitioning.

Option 2 - mdadm SW raid
- According to what has been said, destroy these two arrays and set the raid mode to JBOD. This should pass the disks directly.
- When you reach the OS installing phase we can help you configure the mdadm raid.

That's it, in very short... :)

PS. Trying to read the text in the last image again, it seems it is saying the Drive Group is used just to group the disks, and inside it virtual drives are created (in other words arrays). If I understand it correctly, you don't need to destroy both groups. You just need to destroy the second group and add all disks from it into the first group. You probably need to do this regardless if you decide to use raid5 or JBOD because the setting seems to be set on the group itself. So, after you have all 8 disks in just one group, and depending if you decided to go with server raid or SW raid, select the raid5 or JBOD mode/setting for that group to create "virtual drive". To add to the above comment about 8 disks being too many for raid5, you can consider using raid6 which can handle two failed members at the same time.

---

### Post by dubhan.mcnamee on 2016-02-29
Hi Darkod,

I have now resolved the issue and got my arrat set up correctly with RAID5 and using all the disk in the array. :P :popcorn::KS

I destroyed/cleared the original arrays and then when running the install of Ubuntu Server, I selected
Guided - Use Entire Disk.

Can I now have this thread closed off as 'Solved'?

Thankyou for all the assistance,
Dubhan

---

### Post by darkod on 2016-02-29
If you have it solved then you can mark it as Solved in Thread Tools above the first post.

---

