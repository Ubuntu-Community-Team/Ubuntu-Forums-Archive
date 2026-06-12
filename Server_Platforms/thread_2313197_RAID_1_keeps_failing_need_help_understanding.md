---
title: "RAID 1 keeps failing need help understanding"
date: 2016-02-10
forum: Server Platforms
---

### Post by Babaoupla on 2016-02-10
Hi so I'm having a weird problem with RAID 1 on my server if anyone could help me understand whats going out it would be awesome.

I have been running my Ubuntu system on 2 [Samsung 840 pro 128G SSD]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16820147192") mounted in RAID 1 and everything was fine for 2 years. One day Mdadm sent me an email to say that 1 of the 2 drives had failed.

Right away I purchased a replacement drive, the Samsung 840 pro was discontinued so I purchased the newer [Samsung 850 pro 128G SSD]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16820147359") instead. I Found the serial of the good drive (was not able to even pull the serial of the failed drive at that time, it seemed dead dead!), replaced the failed drive and rebuilt the RAID 1 array, everything seemed fine, a problem well taken care of?

Unfortunately about 2 days later Mdadm sent me another email, one of my RAID drive had failed again, this time only the main system partition (out of the 2 partition which are on this drive) had failed and I was still able to pull the serial number of the failed drive. It was the brand new drive that had failed. I figured maybe I got a bad drive no big deal.

I purchased another Samsung 850 pro and replaced the first Samsung 850 pro by the second. I had the original failed 840 pro at home and the first 850 which lasted 2 days, I ran an extended test on them, they were both fine, only a few bad sectors on the older one.

About 2 days later again Mdadm emails me again, the second 850 had failed in the RAID array again, I went and replaced the cable on the server rebuilt the RAID.

Another few days later it fails again!! confused I disconnect one of my other drives which was not needed, I add the first 850 pro instead of the removed drive (and leave the second 850 pro where it is) I grow my RAID to 3 drives and rebuild RAID, Im now running RAID 1 with 3 drives, the original 840 which never failed, and the 2 new 850.

A couple of days later Mdadm emails me again. The 2 850 drives have failed?!?! at the same time....

So I dont think its the new drives that are bad, what are the chances that I buy 2 drives and theyre both bad, + I ran all kinds of tests on them every test says they're 100% fine. I know its not the cables or the SATA ports on the motherboard because I've changed the cables, I've plugged in 2 different SATA ports (and the second 1 is hot swap so it does not use the same type of cables) and no matter what all the new drives just keep failing and I'm unable to have a RAID 1 security which holds more than 2 days.

What can cause that? Can there be something wrong with the Samsung 850 pro SSD drives that prevent them from working correctly in a RAID 1 array? Is there a log which I can consult to discover what the problem is?

All I could find in the logs so far is this:

/var/log$ cat syslog | grep /dev/sdf
Feb 10 08:05:10 intercode mdadm[3967]: Fail event detected on md device /dev/md/0, component device /dev/sdf1

That does not tell me anything I didn't already know, yes sdf1 has failed but why does it keep failing?

Any help would be appreciated!

My RAID array currently looks like that:

cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md2 : active raid1 sdc1[0] sdd1[1]
      3906885440 blocks super 1.2 [2/2] [UU]

md1 : active raid1 sda5[3] sdf5[2] sde5[0]
      16745344 blocks super 1.2 [3/3] [UUU]

md0 : active raid1 sda1[3](F) sdf1[2](F) sde1[0]
      108213120 blocks super 1.2 [3/1] [U__]

unused devices: <none>



Thanks!

---

### Post by mastablasta on 2016-02-11
having 3 disks in raid 1 array doesn't make sense.

what happens if you format the drive and add it back to array? you say they are good so they should be picked up by the array. 

you say you use it for the OS so what about this:
> Red Hat also warns that software RAID levels 1, 4, 5, and 6 are not recommended for use on SSDs. During the initialization stage of these RAID levels, some RAID management utilities (such as mdadm) write to all of the blocks on the storage device to ensure that checksums operate properly. This will cause the performance of the SSD to degrade quickly.

[http://serverfault.com/questions/612716/should-i-avoid-putting-two-ssds-in-a-raid1-configuration-due-to-performance-degr](http://serverfault.com/questions/612716/should-i-avoid-putting-two-ssds-in-a-raid1-configuration-due-to-performance-degr)

read through for other options. looks like proper setup is needed for SSD mdadm and also newer kernel (already provided by Ubuntu, unless you are on 14.04)

---

### Post by Babaoupla on 2016-02-11
Hi Mastablasta, thanks for your answer. Setting up 3 disks for raid 1 was more just an experiment but according to what I've read with RAID 1 the more drives you have setup on your RAID array the faster read speeds you'll be getting! however the write speed will be as slow as the slowest drive in the array*. So there could be advantages to have as many drives as possible in your RAID 1 array.

I did a lot of reading before decided to setup SSDs on RAID 1. Some people seem to say its no good because RAID 1 writes a lot and SSDs can only write limited amounts in its lifetime, however when I did my research I also found plenty of people saying that they are using SSDs in RAID 1 and its working good for them. In my case I can say it's been working totally fine for 2 years, great performance + the security of RAID 1. After one of my SSDs failed from the RAID array I checked how much data had been written in the drives lifetime (ext 4 partitions keep track of how much data was written in its lifetime) and found that slightly under 40 Terabytes of data had been written to the drivesin 2 years while the warranty was good for 73 Terabytes and 5 years. So for 2 years of operation its not so bad at all! (that's the Samsung 840 pro SSD which is discontinued now, for the new 850 pro the warranty allows for even more Terabytes to be written and 10 years). So I think using SSDs with RAID 1 is generally OK despite the different opinions. Lots of ppl do it, I did it for long time without issues. Of course I'm not excluding the possibility of just buying 2 SATA drives and reinstalling my system on that but this is a running server with active websites on it so reinstalling the system is not something I would want to do unless I don't have a choice.

You mentioned something about newer kernel to be required to use mdadm with SSD, unless youre on 14.04. Im actually on 14.04.3 LTS would that be a version which would have the necessary kernel to run mdadm with SSD (I first started out with 12.04 and things were functional for me, no issues to report).

Anyways at this point I'm thinking maybe RAID 1 with Samsung 840 pro and 850 pro SSDs mixed together could be the issue, I'm going to try removing the 840 pro from the RAID 1 array and keep only the 2 850 pro next. Maybe like this the array will hold. If not Ill have to assume that 850 pro are just no good for RAID 1 and purchase something different.

---

### Post by Babaoupla on 2016-02-11
So I did some changes in my RAID setup and I hope this will hold this time, we will see. My raid config currently looks like this:

cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md1 : active raid0 sdf5[1] sda5[0]
      33506304 blocks super 1.2 512k chunks

md2 : active raid1 sdc1[0] sdd1[1]
      3906885440 blocks super 1.2 [2/2] [UU]

md0 : active raid1 sde1[2](S) sda1[3] sdf1[4]
      108213120 blocks super 1.2 [2/2] [UU]



One thing I realized is that /dev/md1 was a small raid 1 partition used for swapping. I realized it didn't make much sense using raid 1 on a swap partition (why keep a copy of swap data since its volatile, pretty useless!) So I turned it into raid 0. since I didn't want to use sdf5 and sda5 for raid 1 anymore I had those 2 free with nothing to do with them so instead of making just 1 a swap and having no use for the other one (what else can I do with a partition of 16G??) I combined them in a raid 0 partition and made the partition my new swap. My server doesnt use swap very much but since it has only 16G RAM its a security... Plus raid 0 is supposed to be fast but not very safe.. perfect for swap I would think...

for md0, which is my main drive, I took out /dev/sde (which happens to be the old Samsung 840 pro SSD, the only one who never failed yet.. scary thing!), grew my RAID 1 back to 2 drives and re-added it (to make it a spare just in case!!). So now Im running my / on a RAID 1 of the 2 new Samsung 850 pro SSDs and have the old 840 pro as a spare...

Hope things hold this time!! the server ATM seems fine, websites are fast, cant tell if they're faster than before or not but everything seems pretty fast! I also setup a rsync command to copy all the contents of / (except a few folders) on my big RAID 1 drive for storage /dev/md2 for security in case all these 850 pro just fail simulateously again... In case anyone is interested my backup command looks like this 
```
rsync -aAXv --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found"} / */path/to/backup/folder*
```
*source: **[https://wiki.archlinux.org/index.php/full_system_backup_with_rsync](https://wiki.archlinux.org/index.php/full_system_backup_with_rsync)*
and its setup as a cronjob

---

### Post by Babaoupla on 2016-02-11
Just for the fun I ran some test speeds on the RAID personalities

```
$ sudo hdparm -Tt /dev/md0
```

/dev/md0:
 Timing cached reads:   23268 MB in  1.99 seconds = 11695.60 MB/sec
 Timing buffered disk reads: 776 MB in  3.00 seconds = 258.44 MB/sec

```
$ sudo hdparm -Tt /dev/md2
```

/dev/md2:
 Timing cached reads:   16338 MB in  1.99 seconds = 8199.00 MB/sec
 Timing buffered disk reads: 404 MB in  3.00 seconds = 134.62 MB/sec

```
$ sudo hdparm -Tt /dev/md1
```

/dev/md1:
 Timing cached reads:   23912 MB in  1.99 seconds = 12017.69 MB/sec
 Timing buffered disk reads: 1468 MB in  3.00 seconds = 489.08 MB/sec


mod0 is the 2 RAID 1 Samsung 850 pro SSD, md2 is my big SATA 4T storage RAID 1 as well and md1 is my new super RAID 0 swap.

---

### Post by mastablasta on 2016-02-12
RAID is redundant array of independent disks and is there mainly to provide disk redundancy in case of disk failure.

You can have FakeRAID, Hardware RAID or software RAID. in articles I linked and read it points out that software raid (specifically the mdadm) has (or rather had) issues with SSD, while the hardware RAID where controler is used worked just fine. If I read correct issue is prior to kernel 3.8. I thnk 14.04 is at 3.02 or I could be wrong. in any case check the kernel version.

---

### Post by Babaoupla on 2016-02-12
Thanks Mastablasta! I didnt know there were 3 kinds of raid I assumed software and fake raid were the same. Ill have to do some more reading on this.

By the way I checked my kernel:

uname -a
Linux *blahfuzz* 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

I guess my kernel would be 3.12 so that would be above 3.8 phew..!! :)

So far my latest test (RAID with just the 850s, keeping the 840 as a spare) has not yet failed but its been only 1 day. I keep my finger crossed and Ill consider this in my decision for my next test if it unfortunately fails again.

Thanks for all your advice!

---

### Post by MAFoElffen on 2016-02-13
I looked on my servers today (Ubuntu 14.04.03 LTS), and they are at 3.13.0-77.121... But those are Security/Updates. Base is still at 3.13.0-24.46. So 3.13.0.24 did have *some* upstream improvements for SSD's. I confirm that you are current for an LTS Desktop Edition.

I am following this out of curiosity and interest...

---

### Post by Babaoupla on 2016-02-18
So I toughed I was good with the 2 Samsung 850 pro in RAID 1 alone (without the 840 pro in the equation) but 1 week after it failed again...

```
cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md1 : active raid0 sdf5[1] sda5[0]
      33506304 blocks super 1.2 512k chunks

md2 : active raid1 sdc1[0] sdd1[1]
      3906885440 blocks super 1.2 [2/2] [UU]

md0 : active raid1 sde1[2](S)(R) sda1[3] sdf1[4](F)
      108213120 blocks super 1.2 [2/1] [_U]

unused devices: <none>


```

ran some tests on the drive that failed:

```
sudo smartctl --all /dev/sdf
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-24-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     Samsung SSD 850 PRO 128GB
Serial Number:    S1SMNSAG401066H
LU WWN Device Id: 5 002538 8a0a0c6d0
Firmware Version: EXM02B6Q
User Capacity:    128,035,676,160 bytes [128 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    Solid State Device
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2, ATA8-ACS T13/1699-D revision 4c
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Thu Feb 18 10:04:21 2016 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


```

```
 sudo badblocks -v /dev/sdf1
Checking blocks 0 to 108278783
Checking for bad blocks (read-only test):
done
Pass completed, 0 bad blocks found. (0/0/0 errors)


```

the drive seems fine.. right now running a write test with badblocks, still waiting for the results:

```
sudo badblocks -vw /dev/sdf1
```

so these new drives keep failing yet they dont seem to be bad. When I was running sda1(850 pro in hot swap nut not screwed in properly, too small) sde1(old 840 pro just sitting in bottom of case) and sdf1(850 pro sitting in bottom of case too) together, the 2 850 pro failed with about 1 minute interval of each other, leaving the old 840 pro alone... When running the 2 850 pro togheter on sda (hot swap but not screwed in) and sdf (bottom of case) the one at the bottom of the case, sdf, the one which failed the most regularly in this whole story failed alone but sda held! (lucky for me! so I wasnt down!) sde (the old 840 which was never moved) was a spare but it did not kick in... (a flag (R) appeared next to in in /proc/mdstat)

A this point Im thinking Im going to try removing the 840 on sde, move the newest new 850 from sdf to sde (maybe sdf SATA port on mobo is bad?) possibly plug the old 840 on sdf as a spare and change the SATA cables of the 2 drives sitting at the bottom of the case for cables with 90 degree connector (its a 1u case and those connectors are slightly squished by the case) I may also change the IDE to SATA power adapters (in case one of them is bad)

Im pretty much at a loss, maybe its a connection that is bad somewhere! Maybe some SATA ports on my motherboard are failing. Maybe my motherboard is failing altogheter, maybe the Samsung 850 pro SSD are not fit for RAID 1, maybe the 2 Samsung 850 pro SSDs that I bought both have an issue where there are good but occasionally stop working?? Back to the DC for my disk/cable swapping and will update you!

---

### Post by Babaoupla on 2016-02-18
badblocks write test seems to say the drive is good as well:

```
sudo badblocks -vw /dev/sdf1
Checking for bad blocks in read-write mode
From block 0 to 108278783
Testing with pattern 0xaa: done
Reading and comparing: done
Testing with pattern 0x55: done
Reading and comparing: done
Testing with pattern 0xff: done
Reading and comparing: done
Testing with pattern 0x00: done
Reading and comparing: done
Pass completed, 0 bad blocks found. (0/0/0 errors)

```

---

### Post by Babaoupla on 2016-04-20
So still today 2-3 months later I still have the problem with my RAID1 drives continuously failing however with time I noticed a weird thing. [SIZE=3]**My RAID always fails on Wednesday morning around 8h30 -9h00 AM!!!!**[/SIZE] It never fails at any other moment and always does at that time!! weird!! I'm trying to dig through all the system cronjobs to find which runs at that day/time (theres a LOT!)... At this point I'm wondering, did I install a new program when my old drives RAID failed the first time that caused the RAID to fail (and purchased 2 new drives for nothing!) or is it that first my drive failed for real reason (a drive going bad) and with 850 pro drives in the equation the RAID doesnt survive that task anymore (whatever task runs every Wednesday around 8h30 -9h00 which causes my RAID to fail.... The investigation continues!!! :confused:

---

### Post by SeijiSensei on 2016-04-20
You can see all the jobs run by cron with this:
```
grep -i cron /var/log/syslog | more
```

For ones that start between 8:00 and 8:59 am:
```
grep -i cron /var/log/syslog | grep ' 08:' 
```

---

### Post by Babaoupla on 2016-06-08
> **SeijiSensei said:**
> You can see all the jobs run by cron with this:
```
grep -i cron /var/log/syslog | more
```

For ones that start between 8:00 and 8:59 am:
```
grep -i cron /var/log/syslog | grep ' 08:' 
```

Thank you so much @SeijiSensei this command is really helpful in troubleshooting this however somehow even with the help of this I was still not yet able to find the reason and every Wednesday around 8 or 9 AM (while Im getting ready for work and dont usually have time to troubleshoot my own server....) my RAID 1 on my main system drive (/dev/md0) fails. I thought maybe it could be due to the Magento 2 cronjob since I installed it shortly before this started happening... But one Tuesday I disabled all my Magento 2 cronjobs on my server and on the following Wednesday it still happened... So I dont think its the Magento 2 cronjobs... However to install Magento 2 I had to update many things. Among other things I had to bring my MySQL up to 5.5 and when doing this I had the bad idea of calling a **sudo apt-get upgrade** #-o#-o#-o so it updated about a million random things on my server, most likely either the new MySQL version 5.5 or any of the other packages that got updated with apt-get upgrade is responsible for this new problem.

Here's what I'm at right now:

```
$ sudo cat /etc/*release*
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"
NAME="Ubuntu"
VERSION="14.04.3 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.3 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
```

Does anyone by any chance have any idea of what processes or program can cause my RAID 1 to fail every Wednesday morning? How to troubleshoot this? What in the first place can cause RAID 1 to fail on perfectly healthy drives like clockwork??? Reading/Writing too much data too fast??

Thanks!!

---

### Post by Babaoupla on 2017-05-31
Ultimately I was never able to find the solution, my main drive RAID keeps failing every Wednesday. I didnt find anything related in the cronjobs, anyways why would a cronjob make my RAID fail?? I feel this all started to happen when I needed to upgrade to a new version of MySQL and I did the mistake of calling a sudo apt-get upgrade and so many things changed on my system but in the end this upgrade was unecessary. Maybe another upgrade could fix it now (its already been over a year) but I'm little scared to do it as this is a server in production and in my experience with every upgrade server things break and then there is a headache to make everything work again... If anyone has any info on how to figure what causes my RAID to fail every Wednesday morning for over 1 year and never at any other moment, I'm still looking for a solution!

Thanks!

---

### Post by darkod on 2017-05-31
I can't say what causes it to fail if you can't find anything in the logs, but just to tell you that I regularly run sudo apt-get dist-upgrade on many production servers and it has never broken them.

If the server has issues, yes, maybe things can break when updating it, but not because of apt-get. Saying that updating breaks linux servers is simply not true... In fact by not updating the server you might be missing out on any possible bug fixes, etc... So leaving it as it is might be worse than updating it.

I also regularly update the latest LTS kernels, in other words 14.04 server to be running kernel 4.4/4.8 instead of 3.x.

---

