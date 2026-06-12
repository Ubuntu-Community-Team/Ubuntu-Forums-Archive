---
title: "Installing on Fake-RAID6 w/2TB drives"
date: 2014-09-25
forum: Server Platforms
---

### Post by michaelebsch on 2014-09-25
I have been working on installing 14.04 x64 Server on a new machine with 8 new 2TB hard drives. So far I have gone through a couple dozen variations of what different users have posted in the forums. I understand there is a limitation with GPT tables on drives 2TB and up which requires the use of a BIOS Boot area. Here is where there is far too much confusion and the lack of a confirmed successful setup for me to follow. I am trying to run all of the 8 drives in a RAID6 array. My last partitioning attempt was as folows:

sda1 - 1.0 MB (Reserved BIOS boot area)
sda2 - 8096 MB (Swap Area)
sda3 - 2.0 TB (Raid)

sdb1 - 2.0 TB (Raid)
sdc1 - 2.0 TB (Raid)
sdd1 - 2.0 TB (Raid)
sde1 - 2.0 TB (Raid)
sdf1 - 2.0 TB (Raid)      
sdg1 - 2.0 TB (Raid)
sdh1 - 2.0 TB (Raid)     [sda3 /sdb1/sdc1/sdd1/sde1/sdf1/sdg1/sdh1]---- RAID6 / 8 Devices / 0 Spares ---- Partition format XFS / mount point = / (root)

I get up to the Grub installation and then it fails with: "Unable to install GRUB in /dev/sdb - Executing 'grub-install /dev/sdb' failed."

I am not sure if I need to create a BIOS boot area on each drive and set those up in a RAID as well, because creating them individually on each drive without a RAID configuration for that partition just throws a lot of errors while writing the changes to disk. If I had enough money and SATA ports left I would just throw a couple 250GB drives in RAID1 just for the OS and leave the 2TB drives for the large array, but it is not an option given the budget and time constraint now. Just need to work with what I have. If someone could just provide the partition setup I need to make this work that would be great, thank you.

---

### Post by Michael_McKenney on 2014-09-25
If you want RAID 6, get a 8 port PCIe SATA RAID controller.  I have seen them for $200-$800.  I have a LSI Logic 8708EM2 SAS/SATA Raid controller.  I run 15K SAS drives on it.  You can then use your onboard SATA for smaller drives and keep your RAID 6 array separate on its own controller for speed and reliability.

---

### Post by michaelebsch on 2014-09-25
I appreciate the suggestion, but two problems:

1. I don't have the budget for a hardware RAID controller, and really not desire to use one at the moment since I know this is possible with linux "fake-raid" once I get the proper info.
2. Even using a hardware controller still puts the partition sizes up high enough that the same GPT issue comes into play and I am back to square one. 

I have been looking at some of the Areca 16 to 24 port cards for another one of my servers, but that one is running fine off of a small set of RAID1 configured drives and uses the 2TB drives solely for storage. So expanding the RAID on that one will require more ports which leads to the card. This server is for someone that has already agreed to the budgeted amount for the hardware. Can't very well go back and suggest hundreds in upgrades to the hardware.

---

### Post by Michael_McKenney on 2014-09-25
What limitations?  A LSI Logic lower end SATA controller can handle 240 drives.  The only limitation is 16 drives per array on lower end controllers.  RAID 6 would be 28GB on 16x2 TB drives.  Cabling is expensive.  Software RAID 6 would keep your CPU very busy on parity calculations.  Usually a budget can be changed, if a better solution is available.  Hardware RAID gives you more options and expansion.

---

### Post by michaelebsch on 2014-09-25
Lets say I went with 4- 1TB drives in a RAID10 format for the OS on the hardware controller, this because the price of good 1TB drives versus smaller drives now are cheaper overall. In that raid array the OS would see the available space as 2TB and have the same GPT issues with GRUB I am having at this point with the linux fake-raid. Now I could go with a group of 250GB drives in the same setup and get around this, but I do know the person this is going to quite well and that kind of budget change would be a deal breaker and I would be eating the cost of this. This is why I stated from the get go, "[COLOR=#000000]Just need to work with what I have[/COLOR]". If I knew he had the budget to work with for that I would do just what you suggested without question, it is a good way to go.

---

### Post by Michael_McKenney on 2014-09-25
I always start a server with a good RAID controller on production builds.  Hard drives are easy to add later as space is needed.  Software RAID has too many issues for me to want to deal with.  I rather do JBOD configuration over it.   My SAS RAID at home was $2200 for the drives, controller, battery, and cables.  Cabling was $300.  I can add up to 4 drives per cable without expanders.  Changing from RAID 1 to RAID 10 is just adding two drives.  Configuring RAID 1 and then adding it to the original RAID 1.  I don't worry about drive size drift on the controller.  It is set to reduce RAID 1 by up to 1 GB to match the first RAID 1 size.  

My only concern with your configuration is failure rates.  As you add drives, you increase your MTBF failure rate.  On my RAID controller I can add spares like I do in the Data Center SAN.  Did you look at a NAS chassis over doing internal hard drives?

---

### Post by michaelebsch on 2014-09-25
You are completely right with the planning etc.... I built this one with a far lower budget. Help a friend with a small business yadayada.....so this one came in at $1200. Should he ever hit the upper limits of this storage then I we hoped he would have the budget to move up to a much higher quality build and migrate the data over. 

On another note I did get the install to complete by adding this:

[COLOR=#000000]sda1 - 1.0 MB (Reserved BIOS boot area)[/COLOR]
[COLOR=#000000]sda2 - 8096 MB (Swap Area)[/COLOR]
[COLOR=#000000]sda3 - 2.0 TB (Raid)[/COLOR]

[COLOR=#000000]sdb1 - 1.0 MB (Reserved BIOS boot area)[/COLOR][COLOR=#000000]
sdb2 - 2.0 TB (Raid)[/COLOR]
[COLOR=#000000]
[/COLOR][COLOR=#000000]sdc1 - 1.0 MB (Reserved BIOS boot area)[/COLOR]
[COLOR=#000000]sdc1 - 2.0 TB (Raid)

[/COLOR][COLOR=#000000]sdd1 - 1.0 MB (Reserved BIOS boot area)[/COLOR]
[COLOR=#000000]sdd2 - 2.0 TB (Raid)[/COLOR]
[COLOR=#000000]
[/COLOR][COLOR=#000000]sde1 - 1.0 MB (Reserved BIOS boot area)[/COLOR][COLOR=#000000]
sde2 - 2.0 TB (Raid)[/COLOR]
[COLOR=#000000]
[/COLOR][COLOR=#000000]sdf1 - 1.0 MB (Reserved BIOS boot area)[/COLOR][COLOR=#000000]
sdf2 - 2.0 TB (Raid) [/COLOR]
[COLOR=#000000]
[/COLOR][COLOR=#000000]sdg1 - 1.0 MB (Reserved BIOS boot area)[/COLOR][COLOR=#000000]
sdg2 - 2.0 TB (Raid)[/COLOR]
[COLOR=#000000]
[/COLOR][COLOR=#000000]sdh1 - 1.0 MB (Reserved BIOS boot area)[/COLOR]
[COLOR=#000000]sdh2 - 2.0 TB (Raid) [sda3 /sdb2/sdc2/sdd2/sde2/sdf2/sdg2/sdh2]---- RAID6 / 8 Devices / 0 Spares ---- Partition format XFS / mount point = / (root)[/COLOR]

[COLOR=#000000]But now it hangs during OS starup at "adding the swap area to /dev/sda2". Been stuck there for 30 minutes with steady hard drive activity. Debating if this a fail for this setup or if I should just wait and see where it goes. Unfortunately it is in my personality to obsessively exhaust all possibilities before admitting defeat and changing my strategy. [/COLOR]

---

### Post by Michael_McKenney on 2014-09-25
I would wait for a crash and see.  The problem with RAID 5 and 6 are parity calculations and writes.  It can really slow down RAID.  I only do RAID 10.  Only the new 3Par SAN is good enough for RAID 5 and 6.  The controllers have 1 GB cache and higher end bus.  I have seen 8 drive RAID 5 arrays get 80 MB/s write performance.  Parity kills performance.   I would talk to the client about a NAS or RAID controller.   You will also want to configure swap partitions.  On my Windows servers in the data center, I put 128 MB pagefile on C: and create a 2 x RAM pagefile partition with the VM.  If I expand the RAM on the VM, I can add another pagefile partition.   When I built my workstation at home, I added a RAID 1 pair just for temp and paging files along with the target for CAD and Photoshop.  No apps are installed to it.  It really improved performance.

I just thought of something.  I never put /tmp or /swap on RAID 5 or 6.  It is single drive or RAID 1 only.  In Windows, paging can cause lags and corruption on RAID 5.  Microsoft best practice is RAID 1 or single drive for temp and paging files.  You can do RAID 10, if you have hardware RAID 10.

---

