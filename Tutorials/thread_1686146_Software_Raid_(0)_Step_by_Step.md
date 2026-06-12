---
title: "Software Raid (0) Step by Step"
date: 2011-02-11
forum: Tutorials
---

### Post by dark_harmonics on 2011-02-11
[SIZE="6"]Software Raid (0) Step by Step[/SIZE]

**Purpose:** I have found many tutorials on Linux software RAID, however the steps I used to achieve this were not documented in any thread or post that i could find. I felt that these steps were worthy of documentation with the purpose of helping others users like me who are trying to get software RAID working in linux.

**Before you begin:** 
- [SIZE="4"][COLOR="Red"]This process will wipe any data that exists on the hard drives. If you have data on these devices, back it up before beginning this procedure.  [/COLOR][/SIZE] 
- Also, it is preferred that the hard disks are the same size for this.

**Detailed Steps:**
[LIST=1]
[*]**Install your hard drives**
Install the hard drives you want to RAID. In this tutorial I am creating a RAID which uses 4 hard drives in a RAID 0 Stripe. 

[*]**Download and Burn the Alternate Ubuntu install CD**
Download the alternate installer from [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download"). For example: I choose the link for ubuntu-10.10-alternate-amd64.iso.torrent because I wanted a 64 bit install. Burn this image to a CD or DVD with brassero(ubuntu) or imgburn (windows). Mac users can use the built in disk utility to burn the image. 

[*]**Boot to the installer CD and select the Install option from the menu**

[*]**Select Manual Partitioning**
When you arrive at the Partition Disks menu option, select Manual Partitioning.

[*]**Delete any existing partition on the disks**
This step will remove any data that existed on the disks. Select each partition that exist on all the disks and select the delete partition option. All disks should be completely clear before continuing to the next step

[*]**Create the /Boot Partition on the first disk**
Select the first disk's free space. The first drive is usually labeled SDA(SATA). Select the Create Partition option. Set the size of the partition to 0.5gb. Partition it as EXT4 and assign it to /boot. Return to the main partitioning menu.

[*]**Create the primary RAID partitions on each drive**
- For each drive in the RAID create the primary partition. Select the remaining free space on the first drive and select create partition. 
- For the size of the partition you'll want to leave some space at the end of the partition for the swap. 

[I]Here is an example of how to figure out how much space:
Size of the remaining free space=245gb
Size of memory (typically swap is the same size as the memory)= 8gb
Number of hard drives in the array=4
So we want 8 total GB of swap accross 4 hard drives. Each drive will need 2gb for swap (8/4=2). For this example 245gb-2gb is 243gb.[/I]

- Set the total space of this partition to 243 in this example, set it as a primary partition, and format it as ext4. 
- [COLOR="Red"]Select each drive and repeat this process.[/COLOR]
 

[*]**Partition the Swap space on each drive**
- Select each drive's remaining free space to create the swap partitions. 
-Select create partition, use the remaining space (it will default to this), set it to a primary partition and select swap as the type.
-[COLOR="red"]Perform this for each Drive that will be in the RAID array.[/COLOR] 

When you are finished the partition situation will look like this:

SDA
[INDENT]SDA1 Primary 0.5gb  /boot   ext4[/INDENT]
[INDENT]SDA2 Primary 243gb  nomountpoint  ext4[/INDENT]
[INDENT]SDA3 Primary 2gb Swap[/INDENT]
SDB
[INDENT]SDB1 Primary 243.5 nomountpoint ext4[/INDENT]
[INDENT]SDB2 Primary 2gb Swap[/INDENT]
SDC
[INDENT]SDC1 Primary 243.5 nomountpoint ext4[/INDENT]
[INDENT]SDC2 Primary 2gb Swap[/INDENT]
SDD
[INDENT]SDD1 Primary 243.5 nomountpoint ext4[/INDENT]
[INDENT]SDD2 Primary 2gb Swap[/INDENT]

[*]**Create the root RAID Array**
- Select the Configure Software RAID option from the partitioning menu.
- Select Create New MD Device and set it as RAID 0
- Select the SDA2, SDB1, SDC1, SDD1 partitions. If your partition numbers are different this is ok. You want to select the large partitions from each drive here. 
- Finish creating the RAID.
- Select the raid (MD0) and select create partition
- Use all of the space and set it to a Primary partition.
- Format it as EXT4 and use it as / (root)

[*]**Create the Swap RAID**
- Select the Configure Software RAID option from the partitioning menu.
- Select Create New MD Device and set it as RAID 0
- Select the SDA3, SDB2, SDC2, SDD2 partitions. If your partition numbers are different this is ok. You want to select the small partitions you made for the swap.  
- Finish creating the RAID.
- Select the RAID (MD1) and select create partition.
- Use all of the space and set it to a Primary partition.
- Make sure it is formatted as Swap and use it as Swap.
[/LIST]

Congratulations you have created the software RAID! Finish the ubuntu installer as normal by entering your username other information. Reboot to test your new software RAID.

Ref: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
Ref: [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by Jon Hanna on 2012-07-11
> **dark_harmonics said:**
> **Create the /Boot Partition on the first disk**
Select the first disk's free space. The first drive is usually labeled SDA(SATA). Select the Create Partition option. Set the size of the partition to 0.5gb. Partition it as EXT4 and assign it to /boot. Return to the main partitioning menu.
While experimenting with this last night, I decided to go against the advice stated here and elsewhere, and include /boot in the RAID itself. I set up a small RAID0 /boot, and it worked like a charm.

I did have the underlying partitions marked as bootable before setting up the RAID. I don't know if that actually mattered though (I doubt it, I was experimenting in a very lets-see-if-I-do-this manner).

Since the above was written in the days of Maverick (and another page that comes up if searching for this was with Lucid) and I was using Precise, maybe this is a matter of what version you're installing.

---

### Post by Jon Hanna on 2012-07-16
> **Jon Hanna said:**
> Since the above was written in the days of Maverick (and another page that comes up if searching for this was with Lucid) and I was using Precise, maybe this is a matter of what version you're installing.
What I've read since suggests it was actually a matter of different BIOSes.

---

### Post by maqiqi on 2012-07-16
haha  so long~~

---

