---
title: "RAID,  LVM OR just fstab?"
date: 2010-09-03
forum: Server Platforms
---

### Post by Off Topic on 2010-09-03
Im setting up a video server on my HP Mediasmart server with 10.04.  Might do a FTP server in the future.

Im not concerned about backing up the files.  What I want is a single file/folder that sees the hard drives as one large pool of storage space. 

I dont want to go back to Windows Home Server on this box.

---

### Post by apeganz on 2010-09-03
I have made really good experiences with mdadm raid for a similar purpose. aside from having one huge storage space it also gives me a very nice speed bump compared to single disks.
lvm may be simpler to extend later cause it can handle disks of different sizes more easily, but I think you'd rather lose performance than gain it.
of course you can always combine the 2. a friend of mine did this and it works fine, but he had to put a lot of effort in it.
fstab alone can't solve the problem afair.
personally, I'd go with the raid.

my2c,
Alex

---

### Post by BkkBonanza on 2010-09-03
Do you want every file in the one folder? Or are you ok with sub-folders? 

If subfolders are ok then you can simply mount existing drives/partitions in the one folder as sub-folders (unlike older versions of Windows which have drive letters) using fstab.

If you need everything in one folder level then you can use use LVM to combine drives/partitions into one logical unit.

Using raid is separate discussion about whether you want to improve performance and/or have redundancy. But it has some disadvantages too.

---

### Post by Off Topic on 2010-09-04
> **apeganz said:**
> I have made really good experiences with mdadm raid for a similar purpose.

my2c,
Alex

That looks like a winner to me,  Thanks.

---

### Post by BkkBonanza on 2010-09-04
Hope you look into it before jumping in. You have to have same size drives or you end up wasting space on the the larger ones. And with striping if one drive fails then the other drive's data becomes useless as well; and if not striping then you gain redundancy but lose space. There are always pros and cons with raid and if you just want to combine space it isn't the -simple- answer.

---

### Post by Off Topic on 2010-09-04
Im not interested in redundancy,  its for a video server.  If a hard drive pukes its not the end of the world.

I simply want one large storage pool over 4 hard drives.  I know I could do this by reinstalling Windows Home Server but I dont want to.

---

### Post by Hitechdev on 2010-09-04
I used freenas for FTP and other storage solutions. LVM is the only way to go.

---

### Post by Off Topic on 2010-09-04
> **Hitechdev said:**
> I used freenas for FTP and other storage solutions. LVM is the only way to go.

Ill look into that.  Thanks.

---

### Post by BkkBonanza on 2010-09-04
As a video server I don't think drive performance is the key issue so I doubt that using raid for striping is the best option. The reason I say this is that in a striped set if one drive fails then the whole set's data is broken since each file is split across multiple drives (which give better speed). With striping the striped set is the size of the smallest partition in the set. The other space can be used but not in the same set (same folder).

If you use LVM you can combine the drives but one drive failing doesn't break the other drive's contents. I'm just clarifying this so you can decide. It may not be critical if you lose data since it's just video, but the difference between losing one drive of data and losing all drives data simultaneously is perhaps quite a bit of time/work to rebuild.

---

### Post by Off Topic on 2010-09-04
Thanks for the replys.  Ill have to do some reading to see if I want RAID or LVM on this server.

Right now I only have a single 500G hard drive.  In the next week or so Ill add a 2TB hard drive and move the 1.5TB drive from the other server.  

The end plan is to have 4 2TB hard drives in the server,  but Im starting out with 1 500G drive with the file system partitioned off with the remainder as storage,  and then a new 2TB drive and the 1.5TB drive from the other server.

Redundancy isnt an issue,  its only movies after all.  Adding and then upgrading hard drives would be the issue.

Hopefully I made some sense with my plan for the server.

---

### Post by BkkBonanza on 2010-09-04
Ah well, this pretty much tells you. 

With raid you have to set it all up at once. With LVM you can add them as needed. 

With raid you would have to store all your current files somewhere while you create the raid array with a new drive added. And repeat this backup process for each added drive. Or re-acquire the movies each upgrade.

With LVM you just add the new drive and do the commands to create and add it's space to the LVM logical volume and the new space is available for use.

---

### Post by Off Topic on 2010-09-04
> **BkkBonaza said:**
> Ah well, this pretty much tells you. 

With raid you have to set it all up at once. With LVM you can add them as needed. 

With raid you would have to store all your current files somewhere while you create the raid array with a new drive added. And repeat this backup process for each added drive. Or re-acquire the movies each upgrade.

With LVM you just add the new drive and do the commands to create and add it's space to the LVM logical unit and the new space is available for use.

OKay,  LVM looks more like what Im after,  after all.

I only have the 1 drive in the server right now and  I may re install this weekend just because.

Thanks again for the replys.

---

### Post by BkkBonanza on 2010-09-04
The simplest LVM setup, especially if you plan to reinstall the OS, is to choose LVM right during the install. It can be added after, but it's more work to figure out.

There are lots of tutorials around but browse through a few first because some of them make it difficult, and you only need to do a few steps when you want to add a new drive.

Good luck.

---

### Post by Off Topic on 2010-09-04
Im pretty sure I installed the OS with LVM Guided. 

Thanks again.

---

### Post by Off Topic on 2010-09-04
On a just because,  I re installed Ubuntu Server for this box.  Chose LVM guided installation,  security updates automatically,  OpenSSH,  and Samba server.  When thats done Ill install a minimal desktop,  setup remote desktop,  and install webmin.  I have no idea if the remote desktop will work when I put the hard drive back in the Mediasmart Server.  A coworker is willing to make me a VGA cable to install on the box so in the future I can see what the unit is doing even if I dont have remote access. Im sure Im forgetting something here.

---

