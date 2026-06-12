---
title: "Oh No not another RAID Post"
date: 2024-03-15
forum: Server Platforms
---

### Post by sgt-mike on 2024-03-15
---------BLUF-------------------
I attempted to follow this guide to reduce the number of drives within the current RAID 5 to 6 Active drive and then have a spare. [URL="https://www.stevewilson.co.uk/sysadmin/reducing-raid-5-disks-with-mdadm/"]https://www.stevewilson.co.uk/sysadmin/reducing-raid-5-disks-with-mdadm/
[/URL]The article is very well written but somewhere I'm failing to actually make it work. The first question is there something omitted that I'm unaware of?
MDADM.conf?

What my error was that MDADM kept looking for the 2 other drives after following the article. I did catch the part about shrinking the filesystem before issuing MDADM the new number of drives  

that never seemed to take. Which after seeing the results I wound up adding the drive (sdb1 the only seagate drive, the remainder are all Toshiba's the exact model numbers , last drive is /dev sdi1 ) back to the RAID5 and right now is running fine with no issues with 8 drives except the seagate still have the errors with smart. 

Currently I have only used 918.93 GiB of 3.13 TiB Available so in my mind it Should have worked easily
.

```
-----------Background------Informatttion----------------------------------- 
The  system is Ubuntu 22.04 server running headless (Dell Optiplex 790 SFF  32 Gb Ram with a extra Sata non-Raid card 8 port) to run as a media  server.

Operating System is on /dev/sda and not in the MDADM Raid 5 Configuration.

Before  anyone posts it,   I know RAID is NOT a Backup, but rather a collection  of drives into one big drive (laymans terms). 
My data is backed in a  different location.

The background on the RAID 5 is I set it up  with 8 drives (500 GB /465 accessible)  had I really thought about it I  
would have set up as 6 active with a spare.

In the current situation I have 1 drive (sdb) which is starting to get errors within Smart so I have a desire to remove it.
But do Have some 1TB drives enroute and I was going to grow the Raid (/dev/md0) one by one to a 6 drive Raid 5 with spare.  
My thoughts was that it would be easier to reduce the number of drives with 500 gibs then slowing grow the array with the 
inbound 1 TiB drives 
```

here is my current MDADM.conf
```
# mdadm.conf
#
# !NB! Run update-initramfs -u after updating this file.
# !NB! This will ensure that initramfs has an uptodate copy.
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This configuration was auto-generated on Fri, 16 Feb 2024 18:45:30 +0000 by mkconf
ARRAY /dev/md0 uuid=58952835:75d234f4:d4201fb9:d535d0c4


```

The actual easiest Solution may just very well disassemble the existing Raid install the new drives and just simply redo it as I now think I should have setup originally. Which I was after the learning experience of manipulating the array. 
Thoughts/ and any advice would be great Thank you for looking this over.

---

### Post by darkod on 2024-03-15
First of all, mdadm.conf is not very relevant for shrinking. The ARRAY definition in that file basically just tells to assemble an array with all members (superblocks) with specific UUID present.

You need to start with filesystem size and array size. So please post in code tags the output of:
```
df -h
sudo mdadm -D /dev/md0
sudo blkid
```

After that I believe we can work on it step by step.

---

### Post by sgt-mike on 2024-03-15
df-h

```
[mike@bastion:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           3.2G  1.3M  3.2G   1% /run
/dev/sda2       228G   14G  202G   7% /
tmpfs            16G     0   16G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
/dev/md0        3.2T  919G  2.1T  31% /mnt/Movies
/dev/sda1       1.1G  6.1M  1.1G   1% /boot/efi
tmpfs           3.2G  4.0K  3.2G   1% /run/user/1000

```

sudo mdadm -D /dev/md0
```
          Version : 1.2
     Creation Time : Thu Mar  7 22:57:49 2024
        Raid Level : raid5
        Array Size : 3417774080 (3.18 TiB 3.50 TB)
     Used Dev Size : 488253440 (465.63 GiB 499.97 GB)
      Raid Devices : 8
     Total Devices : 8
       Persistence : Superblock is persistent

       Update Time : Fri Mar 15 13:27:24 2024
             State : clean 
    Active Devices : 8
   Working Devices : 8
    Failed Devices : 0
     Spare Devices : 0

            Layout : left-symmetric
        Chunk Size : 512K

Consistency Policy : resync

              Name : bastion:0  (local to host bastion)
              UUID : 58952835:75d234f4:d4201fb9:d535d0c4
            Events : 5325

    Number   Major   Minor   RaidDevice State
       8       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1
       6       8      113        6      active sync   /dev/sdh1
       7       8      129        7      active sync   /dev/sdi1

```

sudo blkid

```

/dev/sdf1: UUID="58952835-75d2-34f4-d420-1fb9d535d0c4" UUID_SUB="11b04334-ee6f-7979-758a-ca40418867fc" LABEL="bastion:0" TYPE="linux_raid_member" PARTUUID="25f66cae-01"
/dev/sdd1: UUID="58952835-75d2-34f4-d420-1fb9d535d0c4" UUID_SUB="2862b7ca-4892-eb20-e890-15322117dcbe" LABEL="bastion:0" TYPE="linux_raid_member" PARTUUID="2e85756f-01"
/dev/sdb1: UUID="58952835-75d2-34f4-d420-1fb9d535d0c4" UUID_SUB="1642bc34-f63e-14e0-945e-c5c5fef3beab" LABEL="bastion:0" TYPE="linux_raid_member" PARTUUID="1a9b49b7-01"
/dev/sdi1: UUID="58952835-75d2-34f4-d420-1fb9d535d0c4" UUID_SUB="4ca84bfd-7b6b-0bb7-678d-a306a9af1b12" LABEL="bastion:0" TYPE="linux_raid_member" PARTUUID="0f61245b-01"
/dev/md0: UUID="9aa3afa3-1658-48d6-a4c2-3cb0fb6ef7eb" BLOCK_SIZE="4096" TYPE="ext4"
/dev/sdg1: UUID="58952835-75d2-34f4-d420-1fb9d535d0c4" UUID_SUB="7f764be4-1680-e152-3fb8-0a3e6464642f" LABEL="bastion:0" TYPE="linux_raid_member" PARTUUID="a9a61446-01"
/dev/sde1: UUID="58952835-75d2-34f4-d420-1fb9d535d0c4" UUID_SUB="322ca567-3577-138c-a074-cc3ebcf76426" LABEL="bastion:0" TYPE="linux_raid_member" PARTUUID="47ad3a9c-01"
/dev/sdc1: UUID="58952835-75d2-34f4-d420-1fb9d535d0c4" UUID_SUB="6de3e8c1-03c4-7a23-0195-650b2583050d" LABEL="bastion:0" TYPE="linux_raid_member" PARTUUID="e4d7e781-01"
/dev/sda2: UUID="394dfb40-ea1d-4f5f-90b8-b5be8be855b9" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="4ea80dba-eb83-4dd9-96cf-fc96fad05f24"
/dev/sda1: UUID="1074-E197" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="cbcc1d37-4cd8-4c52-8a7f-b057a92db558"
/dev/sdh1: UUID="58952835-75d2-34f4-d420-1fb9d535d0c4" UUID_SUB="5a789c85-8839-c9fb-ff62-bd96fece5cd1" LABEL="bastion:0" TYPE="linux_raid_member" PARTUUID="a269eb9b-01"
/dev/loop1: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop0: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"

```

Glad to hear that MDADM.conf is not really involved in the reducing drives within the array. It was just a thought

I'll attach the SMART Report just as a FYI the raw read write report is what is getting me
```

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(    0) seconds.
Offline data collection
capabilities: 			 (0x73) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 101) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x1035)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       136966680
  3 Spin_Up_Time            0x0003   099   098   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1121
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -       68971556
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       7768 (193 66 0)
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1079
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   075   045   045    Old_age   Always   In_the_past 25 (Min/Max 25/27)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       159
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       103
193 Load_Cycle_Count        0x0032   094   094   000    Old_age   Always       -       12054
194 Temperature_Celsius     0x0022   025   055   000    Old_age   Always       -       25 (0 14 0 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   092   092   000    Old_age   Offline      -       7674 (28 61 0)
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       8565115506
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       6168688394
254 Free_Fall_Sensor        0x0032   001   001   000    Old_age   Always       -       2

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     32341         -
# 2  Short offline       Completed without error       00%     32336         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

---

### Post by TheFu on 2024-03-16
Don't let your RAID HDDs spin down. That's bad for data integrity.

Also, if you use mdadm, I'd use LVM on the RAID device to gain some flexibility in storage allocations, then put the file system(s), sized as needed, inside each LV you create.  Always start small and only size an LV for your use in the next 3 months.  Growing an LV while the devices are up and being used is trivial, but only if there is unallocated space in the VG that an LV can pull from. Takes about 5 seconds, including extending the file system (assuming ext4).  Reducing an LV later is a huge hassle.

Or use ZFS in RAIDz configuration, but ZFS is more specific about how disks are used (or I just don't understand it anymore).

I'd be worried a bit about that Raw_Read_Error_Rate. At least your cables don't seem bad.  On my disks, these are the numbers from the most recent tests.
```
smart.2024-03-05.sda:  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       7
smart.2024-03-05.sdb:  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
smart.2024-03-05.sdc:  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
smart.2024-03-05.sdd:  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
smart.2024-03-05.sde:  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       1
smart.2024-03-12.sda:  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       10
smart.2024-03-12.sdb:  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
smart.2024-03-12.sdc:  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
smart.2024-03-12.sdd:  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
smart.2024-03-12.sde:  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       1
```
These disks are mostly 7+ yrs old.

In another system, 
```
smart.2024-03-04.sda:  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
smart.2024-03-04.sdb:  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
smart.2024-03-04.sdc:  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
smart.2024-03-04.sdd:  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
smart.2024-03-04.sde:  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
smart.2024-03-04.sdf:  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       8
smart.2024-03-04.sdg:  1 Raw_Read_Error_Rate     0x000f   113   089   006    Pre-fail  Always       -       113825801
smart.2024-03-04.sdh:  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
smart.2024-03-11.sda:  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
smart.2024-03-11.sdb:  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
smart.2024-03-11.sdc:  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
smart.2024-03-11.sdd:  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
smart.2024-03-11.sde:  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
smart.2024-03-11.sdf:  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       8
smart.2024-03-11.sdg:  1 Raw_Read_Error_Rate     0x000f   115   089   006    Pre-fail  Always       -       95679048
smart.2024-03-11.sdh:  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0

```
sdg was bought in 2007-ish. It was used in a RAID array for about 5 yrs, then became a scratch disk for temporary processing.  I stopped using it last year, but haven't pulled it from the system yet. I really need to do that.
```
Model Family:     Seagate Barracuda 7200.10
Device Model:     ST3320620AS
smart.2024-03-11.sdg:  9 Power_On_Hours          0x0032   001   001   000    Old_age   Always       -       [COLOR="#FF0000"]107002[/COLOR]
```
That's 12.2 yrs spinning. ZERO Reallocated_Sector_Ct for all the drives above in both systems.

I run short SMART tests weekly and long tests once a month.

---

### Post by darkod on 2024-03-16
Good, I see you use partition as raid members (like /dev/sdb1) and not the whole unpartitioned disk (like /dev/sdb). That is a good best practice with mdadm but some people don't follow it. When using disks always try to partition them and use as partitions, even if that means creating one single big partiton to span the whole disk.

As you can see from df your filesystem size is 3.2TB. And from mdadm -D your array size is also 3.17TiB and each member size is 465GiB. For raid5 that makes sense, the array size is 7x the size of the member size, because the 8th member is the parity. And your filesystem currently has the maximum size, the total array size, which is normal.

If I understood correctly, you want to remove two raid members. One to completely remove it, the other to serve as spare.

To shrink the array to 6 members means only 5x members will be used for data (one is for parity). Which means your new array size and filesystem size maximum value will be approx 5x 465GiB = 2325GiB.

As explained in that article you linked, the first important step is to unmount and shrink the filesystem first. Your current used size is only 919GiB so that is good. So go ahead and shrink the filesystem to the minimum value or to any value between 919GiB and 2325GiB.

For example as per the article:
```
sudo umount /dev/md0
sudo resize2fs -pM /dev/md0
```

If you don't want to shrink it to minimum then grow it again, you can select another safe value in between, like 1800GiB. In that case it would be something like:
```
sudo resize2fs -p /dev/md0 1800G
```

That operation might take some hours so go ahead while preparing the mdadm shrink commands.

---

### Post by darkod on 2024-03-16
Related to the mdadm shrink, the new size will be 5x members for data, and in mdadm -D you have the size of each member = 488253440. So according to that you first need to temporary shrink the array size to 5x 488253440 = 2441267200.

But you don't have to calculate this number, and just in case I'm wrong you can do what they did in the tutorial, run the grow command first which will tell you to what value to resize the array first. The order of the commands should be something like:

```
sudo mdadm --grow /dev/md0 --raid-devices=6 (you get the minimum array size from here)
sudo mdadm --grow /dev/md0 --array-size 2441267200
sudo mdadm --grow /dev/md0 --raid-devices=6
```

After that process completes you will still have array with 8 members but only 6 will be active and 2 will be spare. I couldn't find any command how to control the spares during the grow (because you want to remove specific disk, sdb), so I think the spares will be random. Or the last two members of the array will be marked as spares, which would be sdh1 and sdi1.

To remove sdb you will have to fail it and remove it:
```
sudo mdadm /dev/md0 --fail /dev/sdb1
sudo mdadm /dev/md0 --remove /dev/sdb1
```

After this process is finished you should have the array with 6 members and 1 spare. Remove the sdb1 superblock to avoid any confusions in the future and you are good to go.

```
sudo mdadm --zero-superblock /dev/sdb1
```

The last remaining thing is to grow the filesystem to the new maximum size and mount it.
```
sudo resize2fs -p /dev/md0
sudo mount /dev/md0
```

---

### Post by sgt-mike on 2024-03-16
@ Dakrod 
I think where I was not getting the results I wanted to  achieve was I failed sdb (1) first after unmounting  then ( or rather  before) attempted to reduce the array.  
I am in the thought  /assumption that is would be a bad idea to fail sdb (the only seagate  drive in the array is the one with the errors the other all read zero on  that line) and sdc (which will become the spare) at the same time. 
But  would be ok / best practice to fail sdb  rebuild  with the altered n  amount of 7, once clean then fail sbc and then issue the n=6  after  rebuild or probably correct term resync and then add sdc back as the  spare. 
Or am I assuming wrong ? and sbc and sdc can be failed together as the array is greater than 4 members?


" Related to the mdadm shrink, the new size will be 5x  members for data,  and in mdadm -D you have the size of each member = 488253440. So  according to that you first need to temporary shrink the array size to  5x 488253440 = 2441267200."   

I was actually thinking right around that  size maybe a bit smaller. But the 465 gibs (488253440) x 5 make sense or like I said even a bit  smaller then grow to full size of the 5 disks with the 6th member for parity. .  (2400000000 was what I thought without math)

" If I understood correctly, you want to remove two raid members. One to completely remove it, the other to serve as spare."

Yes Sir that would be correct. 


@ TheFu 
LOL yes that is why I was attempting to pull sdb (the smart report is of that drive) from the array. 

hopefully that my post was clear sometimes I get wordy and give too much information which causes confusion.

---

### Post by darkod on 2024-03-16
As far as I see in mdadm -D sdb1 is not marked as failed yet. Despite any smart errors.

So, you have two ways to proceed.

1). Ignore the smart info for now, and shrink the array from 8 to 6 members (I would do it in one go, instead of 8 -> 7 -> 6 because in one go means one reshape operation). This process would be like I explained above.

2). Fail and remove sdb1 first. And then work on the shrink/reshape. But in this case take into account that with failing sdb1 your raid5 is working with the minimum 7 members present. Any possible disk failure during the reshape will probably make the array fail. In case another disk fails before the reshape is completed. This is a risk.

It is also a small risk doing the reshape when sdb1 member is already showing smart errors, but at least it is still reported as active in mdadm, not failed.

So, it would be up to you which way you want to go. :)

I didn't quite understand what you tried to do. Are you saying the reshape failed because you failed sdb1 first? I haven't tried doing reshapes with failed member, maybe it really doesn't work, it might not accept doing the operation when one member is failed. If that is true it would leave you only option 1) I guess. Doing the reshape with sdb1 present and hoping that it will stick it out.

---

### Post by sgt-mike on 2024-03-16
when I attempted to reduce the number of drives in the array, which I failed sdb then attempted to downsize the array. which for some reason I never noticed that I should have resized then fail/remove drive. when I failed the drive (sdb) I did remove the superblock I then attempted to change the number of members in the array.  even after attempts to reshape mdadm kept looking for that 8th member. and never would be clean but rather stayed in clean /degraded status.  at this point I figured it best to put sdb back in.  Ask for help and re-attempt  

I'll re attempt this sometime today or tomorrow.

yes I know that no drive has failed yet just trying to get ahead of a possible failure.

---

### Post by TheFu on 2024-03-16
> **sgt-mike said:**
>  
yes I know that no drive has failed yet just trying to get ahead of a possible failure.

+1 !    If it were me and there wasn't a trivial way to do it, I'd have ensured I had excellent backups for the data, then wiped the array and started over with a fresh **mdadm create** to the size I wanted. I'd also load LVM, for the reason already spelled out, then I'd restore the data.  LVM + mdadm were made for each other.  While LVM **can** provide multiple different RAID levels using forked code from mdadm, I find the resulting LVM objects funky.  I'd rather keep them in layers.

HDD ---> Partition ---> mdadm Array ---> LVM ---> PVs ---> VGs ---> LVs ---> File system

While all those layers may appear to add overhead, somehow they don't impact performance more than even 1% while providing 500% more flexibility.

---

### Post by darkod on 2024-03-16
I assumed you want to use this as a learning opportunity too. Otherwise and as you already said you have backup of the data, like TheFu says, much faster and better way is to dynamite the array and create a new one with the size and disks you want. And you can use the process to introduce LVM like mentioned too.

I used mdadm + LVM before I changed it, and was very happy with it when using it. I now use snapraid + mergerfs but that is mainly because I wanted to use fully my disks of different sizes. That is a different story. :)

---

### Post by sgt-mike on 2024-03-16
Darko stated:
"I assumed you want to use this as a learning opportunity too. "
YES Yes.
The media server is really a home lab. 
And it just makes sense to me to learn this process versus waiting until a drive failure

I know I alluded to the fact that I have 1 TB Drives enroute, but didnt push the fact that I will change over to them vs the 500gb's, I'm sure that the fastest and easiest way is to dynamite the array and just stick the new drives in and assemble the way I want the array to sit then transfer the media over once everything is clean. 

I will probably sit down tomorrow and start the learning process (changing the array) after I have read your advice 3 or 4 times. I'll shift the out going drives into my linux NFS server also running headless. 

Another thing I didn't state was the drives are housed in a Back-plane that uses 6 - 2.5" drives into a single 5.25 bay. I had a couple of reasons for this as it is the easiest way to get a bunch of drives into a SFF chasiss vs 3.5" drives. Another was exactly what TheFu was stating was spin ups  my understanding is that the laptop drive are better suited for this, is that true or fiction IDK.

---

### Post by TheFu on 2024-03-16
Avoid laptop HDDs for RAID use.

I'd only use 2.5in HDDs in a RAID if they are SAS connected and enterprise class.

On the laptop where I still have an HDD, the initial, shipped HDD was a 320G WD-Blue.  After 3 yrs, I moved that to a 500G WD-Black.  About 5 yrs later, it started showing some SMART issues, so I moved everything into a 1TB WD-Black ... which is still what it has.  OTOH, I haven't booted that 2nd-Gen Core i5 in a long time and haven't used it seriously in about a decade. The 500G Black is here in a USB3 enclosure somewhere being used for scratch needs and sneakernet.

All my newer laptops either came with an SSD or I pulled the shipped HDD and put it on a shelf for the warranty period, before putting it into a USB3 enclosure.

I use 4 HDD drive cages that fit in 3x5.25in slots and have a huge, quiet, 120mm Noctura fan.  2 systems have that.  The fan keeps those HDDs cool, pulling outside air across them. Drive cooling is important when they are densely mounted.  Same order as my other post:
```
$ sudo hddtemp /dev/sd[a-h]
/dev/sda: WDC WD8002FZWX-00BKUA0: [COLOR="#FF0000"]50°C[/COLOR]
/dev/sdb: WDC WD20EFRX-68AX9N0: 35°C
/dev/sdc: TOSHIBA DT01ACA200: 36°C
/dev/sdd: Hitachi HUA723020ALA641: 39°C
/dev/sde: WDC WD20EFRX-68AX9N0: 36°C
```
Can you guess which is NOT mounted in the hot-swap drive cage?

```
$ sudo hddtemp /dev/sd[a-h]
/dev/sda: HGST HUS726T4TALA6L4: 40°C
/dev/sdb: HGST HMS5C4040ALE640: 38°C
/dev/sdc: HGST HMS5C4040ALE640: 39°C
/dev/sdd: WD easystore 25FB: S.M.A.R.T. not available
/dev/sde: WD easystore 25FB: S.M.A.R.T. not available
/dev/sdf: WDC WD40EFRX-68WT0N0:  drive supported, but it doesn't have a temperature sensor.
/dev/sdg: ST3320620AS:  drive supported, but it doesn't have a temperature sensor.
/dev/sdh: WDC WD8002FZWX-00BKUA0: 43°C
```
Can you guess which is NOT mounted in the hot-swap drive cage?  Hint:  The easystore HDDs are external USB3 with powered enclosures ... used only for backups.  The last 3 are in an external drive array, eSATA connected. Looks like one of the WD-Red HDDs is having issues ... but not yet dying.

Anyway, some things to consider.  2.5in laptop drives aren't meant to be used 24/7 and definitely not in an array situation.  In a RAID array, if any of the drives is spun down, you have to wait for the slowest to spin up. If anything bad happens related to the spin-up/down, expect data loss.  The only thing I'd consider worse would be using USB connected HDDs for RAID or even primary storage.  I've been burned. Never again.

---

### Post by MAFoElffen on 2024-03-17
I used to use recertified SAS drives in that T720... But they are sill spendy. I no longer use SAS drives = I can't afford them (and SATA SSDs are now cheaper). I have used 2.5 inch Enterprize class SATA HDDs for years I still have a lot of those that I use for testing... My Dell PowerEdge T720 has 16 x 2.5" SAS/SATA drive bays.

In my new servers, they are all SSD and NVMe. For the SSD's, I use 1 slot 5.25" Drive Bay cages that hold 6 x 2.5" drives... They have 2 fans. Very compact. I am very happy with those.

Like TheFu mentioned... I prevent all my drives from spinning down at all. No power saving features left on. They never go to sleep or poweroff. <-- That is very important to me. Bad past experiences from drives going to sleep.

I used to do mdam/lvm >> Now solely ZFS RAIDZ2 and RAIDZ3 arrays. I like that I can afford to lose 2-3 drives and still go on with business. I like that I can make (most) changes with a live filesystem. I can mark drives as failed., clear, scrub, add, remove, etc, while the array is live and accessible. The filesystem within it is very robust.

If a drive powers down, it will be marked as failed in the array... Even though the drive is not really bad (just not accessible). When this happened to me, I could see each drive drop out of the array. Until the pool dropped out. Bad juju. PITA. Just caused more work and stress. Got it all back up... Changed the power-settings of the drives... No further problems.

---

### Post by sgt-mike on 2024-03-17
@TheFu  & MAFoElffen 

BEFORE I post my progress thus far let me ASSURE Both of you that your advice did not fall on deaf ears or I'm ignoring your mentorship and advice. As the systems are a homelab. 
That can be reconfigured with addition of a SAS controller and correct drives. And thank you for the advice, it will be used in my NFS (optiplex 3010) build is next so I can incorporate that into that system.  Then shift the media server over to SAS or pure SSD i'll review the power setting again but if I recall correctly I did not allow the drives to power down EXCEPT in a shutdown or reboot but Like I said I'll triple check.  


here is the progress thus far on what I have.
                        ```

mike@bastion:~$ sudo umount /dev/md0

 [sudo] password for mike:  
 mike@bastion:~$ sudo resize2fs -p /dev/md0 1800G
 resize2fs 1.46.5 (30-Dec-2021)
 Please run 'e2fsck -f /dev/md0' first.
 
 
 mike@bastion:~$ sudo e2fsck -f /dev/md0
 e2fsck 1.46.5 (30-Dec-2021)
 Pass 1: Checking inodes, blocks, and sizes
 Pass 2: Checking directory structure
 Pass 3: Checking directory connectivity
 Pass 4: Checking reference counts
 Pass 5: Checking group summary information
 /dev/md0: 976/213614592 files (1.0% non-contiguous), 254584432/854443520 blocks
 mike@bastion:~$ sudo resize2fs -p /dev/md0 1800G
 resize2fs 1.46.5 (30-Dec-2021)
 Resizing the filesystem on /dev/md0 to 471859200 (4k) blocks.
 Begin pass 3 (max = 26076)
 Scanning inode table          XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
 The filesystem on /dev/md0 is now 471859200 (4k) blocks long.
 
 
 mike@bastion:~$ sudo mdadm --grow /dev/md0 --raid-devices=6  
 mdadm: this change will reduce the size of the array.
        use --grow --array-size first to truncate array.
        e.g. mdadm --grow /dev/md0 --array-size 2441267200
 mike@bastion:~$ sudo mdadm --grow /dev/md0 --array-size 2441267200
 mike@bastion:~$ sudo mdadm --grow /dev/md0 --raid-devices=6  
 mdadm: Need to backup 17920K of critical section..
 mdadm: /dev/md0: Cannot grow - need backup-file   
 
```
 
 
 this last line caused a cockeyed look from me so I issued
 
 
 ```

 mike@bastion:~$ sudo mdadm --grow /dev/md0 --raid-devices=6 --backup=/home/mike/*.tmp
 mdadm: Need to backup 17920K of critical section..
 
```
 
 
 hmm did it finish resizing ???
 ```

 mike@bastion:~$ sudo mdadm -D /dev/md0 | grep -e "Array Size" -e "Device Size"
         Array Size : 2441267200 (2.27 TiB 2.50 TB)
 mike@bastion:~$ cat /proc/mdstat  
 Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
 md0 : active raid5 sdb1[8] sdh1[6] sdi1[7] sdg1[5] sdf1[4] sde1[3] sdc1[1] sdd1[2]
       2441267200 blocks super 1.2 level 5, 512k chunk, algorithm 2 [6/6] [UUUUUU]
       [>....................]  reshape =  0.6% (2956284/488253440) finish=649.7min speed=12448K/sec
 
```   
 
 
 Nope still working at resizing , ok just have to slow down quit rushing and wait 600 min until resized and complete until I can reissue the command sudo mdadm --grow /dev/md0 --raid-devices=6

and the post that TheFu made about the HDD Temps here is mine UNDER Load as a FYI and not bragging etc but to give a idea of what I have without taking a picture
**Drive temperatures** 
sda: 26°C sdb: 30°C sdc: 29°C sdd: 31°C sde: 32°C sdf: 31°C sdg: 32°C sdh: 30°C sdi: 30°C 
all have fans blowing over them 
sdc through sdi are setting in a 6 bay (2.5" 7-9.5mm height) 1 x 5.25 caged bay with cooling fans

---

### Post by darkod on 2024-03-17
Sorry, my bad that I didn't mention the backup file parameter in my grow command. I thought you had that clear from your tutorial link. The --grow reshape is basically asking you for path and filename where to keep some basic info about the reshape in case things go wrong.

So it would have been something like:
```
sudo mdadm --grow /dev/md0 --raid-devices=6 --backup-file=/home/mike/reshape.tmp
```

In any case, the --array-size command did complete correctly, you can see your new temporary Array Size is 2.27TiB (which is 5x 465GiB).

After you did the --grow --array-size, the next --grow --raid-devices=6 you issued actually started the reshape (shrink) to 6 members. That is the process you see in 'cat /proc/mdstat'. It is estimating 600mins to complete after which you should see two of the 8 disks marked as spare in the array. NO NEED to issue another grow after this, in my opinion. This is the actual main grow/shrink that is already in progress.

PS. If you can notice in the cat output, the array is already considered as having 6 members, but the two spares won't be assigned until this reshape process completes. The reshape is actually the shrink of the array.
```
2441267200 blocks super 1.2 level 5, 512k chunk, algorithm 2 [[COLOR=#ff0000]6/6[/COLOR]] [[COLOR=#ff0000]UUUUUU[/COLOR]]
```

---

### Post by sgt-mike on 2024-03-17
sidebar question as getting older in my 60's memory sometimes fails me.
the command to scrub the drives would be:
echo check > /sys/block/md0/md/sync_action 

correct?



on the 
sudo mdadm --grow /dev/md0 --raid-devices=6 --backup-file=/home/mike/reshape.tmp 

had I actually thought about it the reshape.tmp file should have come to mind I had seen that 
listed somewhere before I don't know why I used the wildcard in the command. Just was not thinking. Brain fart i guess.

---

### Post by darkod on 2024-03-17
I don't know that command, and not sure what exactly you mean by 'scrub'.

Basically after you remove a disk/member from the array (for example the mentioned sdb1), and zero its superblock, you are free to use it where and how you want. It will not be related to this array any more. You can use it in the same or another machine.

If you need to repartition it, or simply start fresh, you just create new blank partition table and off you go.

---

### Post by sgt-mike on 2024-03-17
found the link to scrubbing the raid array as a maintenance, which is what I was thinking of and why I said it was a sidebar and not on topic 
[https://raid.wiki.kernel.org/index.php/Scrubbing_the_drives](https://raid.wiki.kernel.org/index.php/Scrubbing_the_drives) 
this is what I was thinking of scrubbing has really nothing to do with this thread Other than maintaining the array's health

perusing the media server I do see that there is a cron job configured via webmin that appears to be a "scrub" operation noticed this after post my sidebar question. And looking to see if Webmin had parameter for disk spin down that TheFu mentions.

---

### Post by TheFu on 2024-03-17
> **sgt-mike said:**
> sidebar question as getting older in my 60's memory sometimes fails me.
the command to scrub the drives would be:
echo check > /sys/block/md0/md/sync_action 

correct? 

Let me check what I did, if I can find it in old backups from a year ago when I used mdadm.  Well, I don't have backups from that system anymore and I took the HDDs out of it, so booting it won't do any good either. Sorry.  Guess I deleeted the backups after the migration to a new system + 30 days when it was clear I wouldn't be  .... hummmm.  Let me check one more place.

Found an old backup HDD on a shelf.  The command I used:
```
# /usr/share/mdadm/checkarray --all --idle
checkarray: I: check queued for array md1.
checkarray: I: selecting idle I/O scheduling class and 15 niceness for resync of md1.
checkarray: I: check queued for array md2.
checkarray: I: selecting idle I/O scheduling class and 15 niceness for resync of md2.

```

Ran that monthly for each mdadm array device.  When it runs, it shows up in the /proc/mdstat file.
```
$ less /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdd2[3] sdc3[2]
      1943010816 blocks super 1.2 [2/2] [UU]
      [>....................]  check =  0.2% (5037440/1943010816) finish=218.1min speed=148065K/sec
      
md2 : active raid1 sde2[0] sdb2[1]
      1338985536 blocks [2/2] [UU]
      [>....................]  check =  0.3% (4799232/1338985536) finish=157.3min speed=141340K/sec
      
unused devices: <none>

```
I moved the array from the other system (core i5-750) to a new system (Ryzen 5600G), but also moved the data from the arrays onto a new WD-black 8TB HDD. I've been slowly checking the old data and migrating it to better places on the LAN - much has been moved to the NFS box.  Still need to deal with photo galleries and bring up old websites that need those photos and home movies. No hurry.

The backup HDD I found isn't connected and it was failing after 10+ yrs of service holding backups for 10-20 systems over all that time.
```
/mnt/1/Backups# df -hT .
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdf1      ext4  1.4T  1.3T   34G  98% /mnt/1
```

Hope all that isn't confusing.  Lots of things moved systems in 2023 here. I retired a bunch of power-wasting systems to get down to just 2 Ryzens handling almost everything, sized so that 1 can handle all RAM/CPU requirements, if not hold all the storage.

---

### Post by sgt-mike on 2024-03-17
Failed sdb1 , hot removed, then zeroed the super blocks
```

mike@bastion:~$ sudo mdadm /dev/md0 --fail /dev/sdb1
mdadm: set /dev/sdb1 faulty in /dev/md0
mike@bastion:~$ sudo mdadm /dev/md0 --remove /dev/sdb1
mdadm: hot removed /dev/sdb1 from /dev/md0
mike@bastion:~$ sudo mdadm --zero-superblock /dev/sdb1
mike@bastion:~$ watch cat /proc/mdstat 
mike@bastion:~$ watch cat /proc/mdstat 
mike@bastion:~$ sudo mdadm -D /dev/md0
/dev/md0:
           Version : 1.2
     Creation Time : Thu Mar  7 22:57:49 2024
        Raid Level : raid5
        Array Size : 2441267200 (2.27 TiB 2.50 TB)
     Used Dev Size : 488253440 (465.63 GiB 499.97 GB)
      Raid Devices : 6
     Total Devices : 7
       Persistence : Superblock is persistent

       Update Time : Sun Mar 17 15:31:36 2024
             State : clean, degraded, recovering 
    Active Devices : 5
   Working Devices : 7
    Failed Devices : 0
     Spare Devices : 2

            Layout : left-symmetric
        Chunk Size : 512K

Consistency Policy : resync

    Rebuild Status : 1% complete

              Name : bastion:0  (local to host bastion)
              UUID : 58952835:75d234f4:d4201fb9:d535d0c4
            Events : 8239

    Number   Major   Minor   RaidDevice State
       6       8      113        0      spare rebuilding   /dev/sdh1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1

       7       8      129        -      spare   /dev/sdi1
mike@bastion:~$ lsblk
NAME    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINTS
loop0     7:0    0   9.8M  1 loop  /snap/canonical-livepatch/264
loop1     7:1    0  63.9M  1 loop  /snap/core20/2182
loop2     7:2    0  63.9M  1 loop  /snap/core20/2105
loop3     7:3    0  74.2M  1 loop  /snap/core22/1122
loop4     7:4    0    87M  1 loop  /snap/lxd/27037
loop5     7:5    0    87M  1 loop  /snap/lxd/27428
loop6     7:6    0  40.4M  1 loop  /snap/snapd/20671
loop7     7:7    0  39.1M  1 loop  /snap/snapd/21184
sda       8:0    0 232.9G  0 disk  
&#9500;&#9472;sda1    8:1    0     1G  0 part  /boot/efi
&#9492;&#9472;sda2    8:2    0 231.8G  0 part  /
sdb       8:16   0 465.8G  0 disk  
&#9492;&#9472;sdb1    8:17   0 465.8G  0 part  
sdc       8:32   0 465.8G  0 disk  
&#9492;&#9472;sdc1    8:33   0 465.8G  0 part  
  &#9492;&#9472;md0   9:0    0   2.3T  0 raid5 
sdd       8:48   0 465.8G  0 disk  
&#9492;&#9472;sdd1    8:49   0 465.8G  0 part  
  &#9492;&#9472;md0   9:0    0   2.3T  0 raid5 
sde       8:64   0 465.8G  0 disk  
&#9492;&#9472;sde1    8:65   0 465.8G  0 part  
  &#9492;&#9472;md0   9:0    0   2.3T  0 raid5 
sdf       8:80   0 465.8G  0 disk  
&#9492;&#9472;sdf1    8:81   0 465.8G  0 part  
  &#9492;&#9472;md0   9:0    0   2.3T  0 raid5 
sdg       8:96   0 465.8G  0 disk  
&#9492;&#9472;sdg1    8:97   0 465.8G  0 part  
  &#9492;&#9472;md0   9:0    0   2.3T  0 raid5 
sdh       8:112  0 465.8G  0 disk  
&#9492;&#9472;sdh1    8:113  0 465.8G  0 part  
  &#9492;&#9472;md0   9:0    0   2.3T  0 raid5 
sdi       8:128  0 465.8G  0 disk  
&#9492;&#9472;sdi1    8:129  0 465.8G  0 part  
  &#9492;&#9472;md0   9:0    0   2.3T  0 raid5 
mike@bastion:~$ 

``` 
things are looking really good. At this moment the array is resyncing / rebuilding. once completed one last grow command (Only if needed for some strange reason)

I know I posted that I desired that I wanted /dev/sdd1 to be listed as spare, but I'm trying to decide if I really want to force that member into the spare slot. 
Which in my mind / thoughts would be to fail, remove then add back as a spare (sdd1).
OR if I want to just let it run as it is currently setup, which I am really leaning towards.

---

### Post by sgt-mike on 2024-03-17
OK everything seems to be finish 
```

mike@bastion:~$ sudo resize2fs -p /dev/md0
resize2fs 1.46.5 (30-Dec-2021)
Resizing the filesystem on /dev/md0 to 610316800 (4k) blocks.
The filesystem on /dev/md0 is now 610316800 (4k) blocks long.

mike@bastion:~$ sudo mdadm -D /dev/md0
/dev/md0:
           Version : 1.2
     Creation Time : Thu Mar  7 22:57:49 2024
        Raid Level : raid5
        Array Size : 2441267200 (2.27 TiB 2.50 TB)
     Used Dev Size : 488253440 (465.63 GiB 499.97 GB)
      Raid Devices : 6
     Total Devices : 7
       Persistence : Superblock is persistent

       Update Time : Sun Mar 17 20:14:02 2024
             State : clean 
    Active Devices : 6
   Working Devices : 7
    Failed Devices : 0
     Spare Devices : 1

            Layout : left-symmetric
        Chunk Size : 512K

Consistency Policy : resync

              Name : bastion:0  (local to host bastion)
              UUID : 58952835:75d234f4:d4201fb9:d535d0c4
            Events : 8283

    Number   Major   Minor   RaidDevice State
       6       8      113        0      active sync   /dev/sdh1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       5       8       97        5      active sync   /dev/sdg1

       7       8      129        -      spare   /dev/sdi1

```
Looks like I lost/ or bad data....size on disks seems to be smaller....  No Problem will copy from the external drive I have the files backed up on 
To ensure that the files are good.   I'll leave sdi1 as the spare

All in all I'm pleased with the results thus far   now to look at how to mark this solved

---

### Post by copz1998 on 2024-07-14
I am rejoining the Linux community after some time off, building a Plex NextCloud server on Ubuntu server. I am booting off my nvme 1TB drive. All is well, but I am having difficulty with my RAID 5 array regarding its size. I have 3 2TB SSDs which should be 6TB, but lsblk and alike only show 3.6TB. I am looking for any guidance on resolving the issue. 
I used the Digital Ocean tutorial, which seemed to work fine except for the array size??
[https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu](https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu)


**lsblk**[COLOR=#2FFF12][FONT=&amp]

[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]loop0         7:0    0  55.7M  1 loop  /snap/core18/2829[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]loop1         7:1    0  74.2M  1 loop  /snap/core22/1380[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]loop2         7:2    0 130.1M  1 loop  /snap/docker/2915[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]loop3         7:3    0   325M  1 loop  /snap/nextcloud/42890[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]loop4         7:4    0  38.8M  1 loop  /snap/snapd/21759[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]sda           8:0    0   1.8T  0 disk  [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]&#9492;&#9472;md0         9:0    0   3.6T  0 raid5 /mnt/md0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]sdb           8:16   0   1.8T  0 disk  [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]&#9492;&#9472;md0         9:0    0   3.6T  0 raid5 /mnt/md0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]sdc           8:32   0   1.9T  0 disk  [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]&#9492;&#9472;md0         9:0    0   3.6T  0 raid5 /mnt/md0[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]sdd           8:48   0   3.7T  0 disk  [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]&#9500;&#9472;sdd1        8:49   0   200M  0 part  [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]&#9492;&#9472;sdd2        8:50   0   3.7T  0 part  /media/plexmedia[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]sde           8:64   0   3.6T  0 disk  [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]&#9500;&#9472;sde1        8:65   0   200M  0 part  [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]&#9492;&#9472;sde2        8:66   0   3.6T  0 part  /mnt/4tbcrucial[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]nvme0n1     259:0    0 931.5G  0 disk  [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]&#9500;&#9472;nvme0n1p1 259:1    0     1G  0 part  /boot/efi[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]&#9492;&#9472;nvme0n1p2 259:2    0 930.5G  0 part  /[/FONT][/COLOR]


**frisk -l**
[COLOR=#000000][FONT=Menlo]**Disk /dev/loop0: 55.66 MiB, 58363904 bytes, 113992 sectors**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]**Disk /dev/loop1: 74.24 MiB, 77844480 bytes, 152040 sectors**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]**Disk /dev/loop2: 130.09 MiB, 136404992 bytes, 266416 sectors**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]**Disk /dev/loop3: 325 MiB, 340791296 bytes, 665608 sectors**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]**Disk /dev/loop4: 38.83 MiB, 40714240 bytes, 79520 sectors**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]**Disk /dev/nvme0n1: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Disk model: WD Blue SN570 1TB                       [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Disklabel type: gpt[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Disk identifier: 7F2ED68A-DF94-4517-9F5C-7C9AD1DC91B6[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]**Device        ** **  Start** **       End** **   Sectors** **  Size** **Type**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/nvme0n1p1    2048    2203647    2201600     1G EFI System[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/nvme0n1p2 2203648 1953521663 1951318016 930.5G Linux filesystem[/FONT][/COLOR]

[COLOR=#000000][FONT=Menlo]**Disk /dev/sda: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Disk model: CT2000MX500SSD1 [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Menlo]**Disk /dev/sdb: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Disk model: CT2000MX500SSD1 [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT][/COLOR]

[COLOR=#000000][FONT=Menlo]**Disk /dev/sdc: 1.86 TiB, 2048408248320 bytes, 4000797360 sectors**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Disk model: T-FORCE T253TY00[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#B42419][FONT=Menlo]GPT PMBR size mismatch (4294967294 != 8001573551) will be corrected by write.[/FONT][/COLOR]_[FONT=Menlo] [i am unsure if this is an issue??][/FONT]_[COLOR=#B42419][FONT=Menlo][/FONT][/COLOR]

[COLOR=#000000][FONT=Menlo]**Disk /dev/sdd: 3.73 TiB, 4096805658624 bytes, 8001573552 sectors**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Disk model: T-FORCE T253TY00[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Disklabel type: gpt[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Disk identifier: 335CC8AB-3BD8-4FE3-9721-F878F16836E9[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]**Device    ** ** Start** **       End** **   Sectors** ** Size** **Type**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sdd1      40     409639     409600  200M EFI System[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sdd2  411648 8001572863 8001161216  3.7T Microsoft basic data[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]**Disk /dev/md0: 3.64 TiB, 4000527155200 bytes, 7813529600 sectors**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]I/O size (minimum/optimal): 524288 bytes / 1048576 bytes[/FONT][/COLOR]
[COLOR=#B42419][FONT=Menlo]GPT PMBR size mismatch (4294967294 != 7814037167) will be corrected by write.[/FONT][/COLOR]

[COLOR=#000000][FONT=Menlo]**Disk /dev/sde: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Disk model: CT4000X9PROSSD9 [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Units: sectors of 1 * 512 = 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Disklabel type: gpt[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Disk identifier: 300BA892-F45B-41FF-AC5D-F85CFD0FADE4[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]**Device    ** ** Start** **       End** **   Sectors** ** Size** **Type**[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sde1      40     409639     409600  200M EFI System[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sde2  409640 7813774983 7813365344  3.6T Apple HFS/HFS+[/FONT][/COLOR]

**blkid**

[COLOR=#000000][FONT=Menlo] blkid[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/nvme0n1p1: UUID="2921-C7B0" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="e6cc44ea-c846-4eeb-9fea-066dec45d9a9"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/nvme0n1p2: UUID="27741d3d-ee50-4b89-ac69-9efc24630774" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="c4be6a03-56f2-46db-bbce-575c770edd79"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sdd2: UUID="35bfd2bc-603c-4b45-87de-2f2613bd6274" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="d2568c05-eb0c-47c4-8a21-b8bb3067d361"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sdd1: LABEL_FATBOOT="EFI" LABEL="EFI" UUID="67E3-17ED" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="550a17f8-96a2-497e-a489-17b225d8bf7a"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sdb: UUID="df71813f-8ee7-efd6-fbe8-3b21100f2497" UUID_SUB="e572584f-6046-1e73-5d03-7df2f7689f2b" LABEL="selbynas:0" TYPE="linux_raid_member"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/md0: UUID="76ae7744-4374-486f-b2c3-2417d1a5e577" BLOCK_SIZE="4096" TYPE="ext4"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sdc: UUID="df71813f-8ee7-efd6-fbe8-3b21100f2497" UUID_SUB="e4f2da1f-beb4-2cc2-d5c5-d52a1a6bb641" LABEL="selbynas:0" TYPE="linux_raid_member"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sda: UUID="df71813f-8ee7-efd6-fbe8-3b21100f2497" UUID_SUB="3c5e1f92-0e6f-9aac-d1c3-20742a6d5ae3" LABEL="selbynas:0" TYPE="linux_raid_member"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop1: BLOCK_SIZE="131072" TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop4: BLOCK_SIZE="131072" TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop2: BLOCK_SIZE="131072" TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop0: BLOCK_SIZE="131072" TYPE="squashfs"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sde2: UUID="592d1e8f-7374-32dd-aadc-1cd7cf393e65" BLOCK_SIZE="8192" LABEL="4TBCrucial" TYPE="hfsplus" PARTUUID="9f7ae9f6-3cc8-47e2-9121-b4e8d43a6b37"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/sde1: LABEL_FATBOOT="EFI" LABEL="EFI" UUID="67E3-17ED" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="8ccafe28-d82a-4936-a6a7-dc9f48254ce7"[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]/dev/loop3: BLOCK_SIZE="131072" TYPE="squashfs"[/FONT][/COLOR]


Thank you in advance for any suggestions!

---

### Post by sgt-mike on 2024-09-13
Yes for a Raid 5 the 3.6 TB will be correct, not 6 TB. 
I'm sure you are siting there wondering why?
Drive Manufacture use Decimal format (1kb= 1000 bytes) and operating systems - Linux/Windows/DOS use Binary format (1kb =1024 bytes), Mac's are the exception they use decimal format to address the capacity. 
This means that the manufacturers 2TB is actually 1.8TB to most of the operating system used,  so a 3 drive setup in RAID 5 is 5.4TB  because a Raid 5 uses 1 drive for parity one loses 1 drive to that parity. 
So while we start out with 5.4 TB (3 drives x1.8 capacity each) usable for all the drives. Parity means we must lose the capacity of one drive. So 5.4TB - 1.8 TB  this leaves 3.6 TB useable. 
Easiest way to calculate the RAID 5 capacity is to not count 1 drive in the calculation.  
Here is a article that explains better than I can on drive manufacturer's advertised capacity vs actual  ( [https://www.seagate.com/support/kb/why-does-my-hard-drive-report-less-capacity-than-indicated-on-the-drives-label-172191en/](https://www.seagate.com/support/kb/why-does-my-hard-drive-report-less-capacity-than-indicated-on-the-drives-label-172191en/)) 

Here is a link to raid capacity calculator ( [https://www.servethehome.com/raid-calculator/](https://www.servethehome.com/raid-calculator/) )  

The question I have for you to consider is for a plex server do you really need a RAID 5? would a RAID 0 work?

I understand the desire to have a drive to go down and still be functioning, which the RAID 5 [FONT=&amp]redundancy a[/FONT][FONT=Roboto][COLOR=#222222][FONT=Verdana]llows. 
But if your goal is pure capacity (which from your post I'm assuming is your goal) maybe a RAID 0 for the Plex server? 
 Which means for your setup you gain back that 1.8TB , leaving you at 5.4 TB available.
RAID is not a backup but a redundancy. Backups are stored on a different machine (i.e NAS) or a drive that is used only for backups

It is your goals as to which mandates RAID configuration to use for your purposes.
 
Personally I have my headless plex server backed up with a NAS which is where my RAID configuration are now. My Plex server just uses the drives for my media at mount points, although there is nothing wrong with combining drives to make a RAID. 

My original media server I was using Universal Media Server utilizing a RAID5 array. I have now taken that out of service as UMS didn't do a good job for 1 of my TV, thus I migrated to Plex, using a old HP compaq 8200 elite ultra small  with a second gen i7. [/FONT][/COLOR][/FONT]

---

