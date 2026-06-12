---
title: "Best way of changing from 2 * RAID 1 to RAID 10"
date: 2017-07-09
forum: Server Platforms
---

### Post by david_silvester on 2017-07-09
Hi guys,

I have a server running Ubuntu 14.04.1 LTS. It is used as a data backup server.

My current setup is:

2 * 2TB drives in RAID 1 array - I made 3 partitions here - one for swap drive, one for operating system and one for data backups.
2 * 4TB drives in RAID 1 array - this is just one partition and its also for data backups.

It is software based RAID and I set it up via mdadm - I dont know if I am using the right terminology here because it was quite some time ago that I configured everything.

the server has 4 drive bays and they are all in use, as per the above.

Now I want to change a couple of things, namely I want to purchase 2 more 4TB drives (To increase my storage capacity) and secondly I want to configure the 4 * 4TB drives in a RAID 10 array - the reason being so that everything appears as a single drive and also because I understand RAID 10 is going to give me the best in terms of reliability and performance.

My two questions are - 

1.Is the above plan a good one, or is there any better way of setting it up (Note my requirements are just to have more space than I currently have but also whilst spending as little as possible).
2.What is the best way of doing this? Can I somehow do it without having to reload my system? Can I do it gradually so I don't have to back up the data to an external source? I know this might be a silly question, I am guessing that because I need all four bays for RAID 10 I am going to have to backup everything then completely reload. BUT seeing as its linux I know there are normally lots of options!!!!

Thanks in advance for any help guys

---

### Post by david_silvester on 2017-07-10
Thinking more about this I wonder if its best just to plug in an external drive, copy all of my backups over to it using rsync, reloading the server and then copying back the backups?

---

### Post by deadflowr on 2017-07-10
*Thread moved to **Server Platforms**.*
You'll probably get a better answer, or at least an answer, here.

---

### Post by david_silvester on 2017-07-10
> **deadflowr said:**
> *Thread moved to **Server Platforms**.*
You'll probably get a better answer, or at least an answer, here.

Ah, thanks very much for that. I think I saw server platforms AFTER I made the post. Thanks for moving it, much appreciated :-)

---

### Post by david_silvester on 2017-07-11
I am now thinking of just reloading and restoring the data.

If I were to reload the system using new drives, could I just pull out the old drives (that were part of raid 1 mdadm) and then attach them to the freshly loaded system and copy back the data using rsync or something?

Will a new install of ubuntu recognize a single drive that was part of the mdadm array or is there anything I need to do beforehand?

---

### Post by darkod on 2017-07-11
By 'reload' you mean reinstalling the OS? How is that related to reshaping of raid1 array to raid10?

You never mentioned you also want to reinstall the OS.

You can try to reshape the array from 2-disk raid1 into 4-disk raid10. But in any case it is recommended to have full backups before starting that procedure. And if you do have the space to make full backups, it is probably much better to destroy the raid1 array and simply create new raid10 array and put the data back (from the backup).

---

### Post by david_silvester on 2017-07-11
> **darkod said:**
> By 'reload' you mean reinstalling the OS? How is that related to reshaping of raid1 array to raid10?

You never mentioned you also want to reinstall the OS.

You can try to reshape the array from 2-disk raid1 into 4-disk raid10. But in any case it is recommended to have full backups before starting that procedure. And if you do have the space to make full backups, it is probably much better to destroy the raid1 array and simply create new raid10 array and put the data back (from the backup).

Sorry yes I meant reinstall the os. Because I have only 4 disk bays I thought reinstalling os would be the only option.

Didn't realise I could potentially change from raid 1 to raid 10 without reinstalling.

Anyway, based on your advise I think I will reinstall os if it's the preferable option.

---

### Post by darkod on 2017-07-11
Yes, mdadm arrays can be reshaped. You do that with the --grow option. Research it on the internet. But the process will probably be long on 4TB disks and might also do intensive read/write on the disks (I'm not sure how intensive it is). So, if you can do full backups, then delete the raid1 array, then make new raid10 array and put the data back, that is the easier option.

This does not mean reinstalling the OS. Are you planning to reinstall because you have only 4 HDD slots in total, so you need to remove the 2TB disks before putting the new 4TB disks?

---

### Post by david_silvester on 2017-07-11
OK I did not realize that. I will research the --grow command.

Regarding the reinstallation of the OS, the reason I was planning (Thinking I had no choice but to) reinstall is because I currently have 4 physical hard drive bays in the server, I have 2 * raid 1 arrays that have data on them and I need to make a new single RAID 10 array (Which I understand needs 4 disk minimum) and I am planning to use two drives from my existing setup (The second raid 1 array is made up of 2 * 4TB drives). So I am thinking to myself that I need to put two new 4tb drives in, make a single raid 10 array from the 4 * 4tb disks thus how can I keep the OS in tact?

If there was a way to set up the raid array from scratch without having to reinstall the os that would be fantastic. I did start looking at cloning tools, for example clonezilla but as far as I could tell it was not possible to clone from one type of raid to another.

So if its possible to do this without reinstalling the os how would I do it? Can I manually back up everything and restore one I install the new drives? And I would have to recreate grub / bootloader I guess?

Excuse me if I am not using the correct terminology etc. Even though I have been using ubuntu for a good few years I have only done basic setups and definitely consider myself still to be a beginner.

---

### Post by darkod on 2017-07-11
There is a way to avoid reinstalling, but not sure if it is worth the work... Plus by reinstalling you could use 16.04 instead of the current 14.04. It depends whether you would prefer that or not...

To keep the current OS the strategy would be this one:
- If you have 4x 4TB disks in the device, the OS has to be on them, for example raid1 of 32GB partitions (if your current root partition array is smaller than 32GB, otherwise you have to make the new partitions at least as big as the current ones)
- You copy all data from the 4TB disks to the backup location
- You delete the current raid1 array on the 4TB disks and you create the 32GB (or whatever size) partitions on them, then you create the big partitions for the data arrays
- You add these 32GB partitions to your current raid1 root array, at that point they sync and you have OS made of 4-disk raid1
- At this moment you can remove the 2TB disks, the OS will boot and run from the 4TB disks
- You add the new 4TB disks, and make the same partitions on them
- You add their 32GB partitions and make again 4-disk raid1 OS array
- From the 4x big data partitions you create raid10 array
- You copy the data back to the big data array

That is how you will keep the OS and still create new raid10 array.

Do not forget this, mdadm works with partitions, not disks (it can work with disks too but most often use is with partitions). That allows you great flexibility to create arrays of one type from one partitions, and other type from other. So in this situation you can have for example 4x 32GB for raid1 with four members for OS, and 4x 4TB partitions for raid10 array. mdadm won't complain.

---

### Post by david_silvester on 2017-07-11
Wow, I love Linux, compared to windows its so flexible.

If you dont mind can i explain my setup in a little more detail to see if the above is still feasible PS I am not certain if this is all correct, but i think it is - 

first array - 2 * 2tb disks in raid 1. In this array I have 3 partitions - md0 - this is boot partition, its 7.3gb in size (50% used), md1 - swap partition, I think this is 10gb, md2 - this is data partition and its remainder of the space.
second array - 2 * 4tb disks in raid 1. In this array its just a single partition taking entire space - md127 (Dont know why it got that number).

So I guess its a bit more complicated than i first explained, in that I need to remove the first to drives (the ones that contain the OS) and replace those two with the two new 4tb drives and then configure the 4 4tb drives into raid 10.

So based on that setup could it still be done the way that you are suggesting?

I have advantages and disadvantages for both, from my point of view - it would be nice to reload so that I can go through the full setup once again, because i like having perfect notes on how servers are set up, but on the other hand I have a few different backup programs in different locations that back up to this server so re-installing the OS could potentially be quite a big job... I guess if its not TOO long winded to keep the OS in tact I would prefer it - for an easy life.

PS thanks so much for your help I really appreciate it.

---

### Post by david_silvester on 2017-07-11
One more thing as well - the server does have its own on board raid, would there be any great benefit in switching to that, over software raid?

---

### Post by darkod on 2017-07-12
You can't move to bios raid or HW raid without complete reinstall. Because setting up those types of raid now will delete all data on all disks. BIOS raid is not really recommended over SW raid. HW raid can sometimes be better, depending on the raid card, but still on linux mdadm SW raid is widely used.

Your setup sounds exactly like I thought it was. So what I explained earlier is possible.

---

### Post by david_silvester on 2017-07-12
Hi Darko,
OK I understand, thanks for clearing up regarding bios / hardware / software.

OK great, so the plan you suggested is exactly what I need.

I am going to try to follow it but i might come back with some more questions if i get stuck, if you dont mind ?

---

### Post by david_silvester on 2017-07-12
Just spent some time going through my setup so that I fully understand it myself.
Then I looked at your guide and tried to understand how I can follow it.

Can you confirm if I have this right (And I have a few questions) - 

1.Back up all data from existing 4tb raid 1 array. OK I am fine with this part.
2.Delete the array currently on the 4tb disks. This is array md127. OK fine with this part.
3.Create a new partition on the 4 tb disks. The size should exactly match my existing root partition, or it just has to be as big as my current root partition? And to confirm, I am just creating partitions here, not making them part of an array yet? I guess I will also need to create partition to match the swap partitions I have on my 2tb disks?
4.Create a second partition on the 4tb disks, taking the remainder of the free space. This will be where I store the data.
5.Add the root partitions to current raid 1 root array and let them sync.  this makes a 4 disk raid 1 array. This is effectively an identical copy of the data on each of the 4 partitions right?
6.remove the 2tb disks and confirm it boots ok on the remaining 4tb disks. Technically speaking the raid 1 root array will be in degraded state now? As two of its disks are missing?
7.add new 4tb disks and make same partitions on them - one for root, one for swap, one for data.
8.add these new partitions to the respective arrays. So now I have 4 disk raid 1 array for root, swap and data.
9.create raid 10 array from the 4 big partitions - so I can leave root and swap in a 4 disk raid 1 array, and just make the big partition raid 10 right? So mdadm will handle this conversion from 4 copies of the data to spanning two copies of the data across the 4 disks?

And then I just need to research the commands to perform each of those steps right?

Just trying to understand how its all going to work first, because I guess there is less chance of me getting it wrong if I understand what I am trying to achieve.

---

### Post by darkod on 2017-07-12
3. The size of the new partitions should be equal or bigger than current. You can't add a smaller partition. If you want to make root bigger, this is the chance, you can create bigger partitions. Correct, first you are only creating the partitions and NOT formatting them or anything. Just simple partition. Yes, you have to match swap partitions too.

5. Yes. Don't forget to also install grub if it is currently not installed on the 4TB disks. It is needed to boot from them when the 2TB disks are removed.

6. Yes, it should boot in degraded although sometimes this can give you some issues. But the OS will be there, not to worry.

8. No, do not add the big data partitions to the raid1 that already exists. Besides, you destroyed md127 in step 2, remember? There is no raid1 for the data to add them to. So, you create the 4-disk raid1 arrays for root and swap, but for the big data array you create new blank raid10 out of the 4 partitions right away. Because the data was already copied and then deleted, so it is like making new blank array from scratch. Only the OS you don't want to delete, so you are doing the 2-disk to 4-disk conversion.

9. Not necessary, as explained in step 8.

---

### Post by david_silvester on 2017-07-13
Thanks for confirming all of that. And thanks for taking so much time to explain all of it - really appreciate your help.

---

### Post by Michael_McKenney on 2017-07-15
I would consider backing up first and think about hardware RAID 10 over software RAID 10.  You need 4 identical drives to make it work properly.   Mixing and matching drives in RAID can cause performance issues.   Hardware RAID makes it easier to replace drives.

---

### Post by david_silvester on 2017-07-17
^^ Thanks for the input Michael.

I am considering both options at the moment - either backing up and then re-shaping to raid 10 or starting again with a fresh install.

---

