---
title: "Hardware questions - new here"
date: 2011-02-08
forum: Server Platforms
---

### Post by geddy2112 on 2011-02-08
[COLOR=black][FONT=Verdana]Hello,[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I have been following the Ubuntu forums for a while and as always, been procrastinating on building a home media server for months. Being completely new to Ubuntu, I had a few general questions. The primary function of this server is for tons of storage for ISO format movies and music to be distributed to other devices on my network. I just ordered a SuperMicro MBD-X7SPA-HF-O motherboard (along with memory, a case, power supply, etc...). I had originally been looking at the ASUS p5bv-c/4l, but ultimately decided on the SuperMicro. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]First question; I will be using a Crucial SSD for the OS to live on, but I did not want to use the 6 onboard SATA ports for anything other than my storage drives (more on that later). I plan on using a Vantec PCI-E UGT-IS100R internal SATA card to control this as the primary drive. Does anyone see that as being an issue or presenting any unique challenges?[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Next, I have not ordered the actual storage drives yet, but I was looking at using the new Hitachi Deskstar 3TB drives. Ultimately, I was planning on having 6 of them using a RAID1 configuration to mirror our files for redundancy giving me about 9TB of storage (full rip ISOs get big, and we have a lot of them already). Does Ubuntu have any issues seeing drives of that size or using them in a RAID configuration?[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]That's all for now... I appreciate any insight or recommendations you could give me and I apologize if any of these are 'stupid newbie' questions ;)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Thank you,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Geddy[/FONT][/COLOR]

---

### Post by rubylaser on 2011-02-08
I don't have any experience with that Vantec card to tell you if it works in Linux or not (I would bet that it would), but Newegg doesn't show any Linux Distros in it's supported platforms list.

Ubuntu will work just fine with the new 3TB Hitachi drives, so you won't have to worry about that (although, I believe these are advanced format drives, so you'll want to align the partition to 4K sectors with parted).

I'm sure you have a reason for RAID1, but I personally would use RAID6 is ideal for this situation, or you could do RAID10 if you'd like to potentially have 1 more parity drive (allow losing both disks from a mirror would still kill your array), and be much faster to rebuild.

I use RAID6 with mdadm for my media server at home, and it works brilliantly.  That's my 2 cents.

---

### Post by geddy2112 on 2011-02-08
Initially I plan to start with a total of 4 drives, so I believe RAID10 might be my best option... If I want to add 2 more drives in the future, is that a potential issue, or a pretty simple addition?
 
Thank you, I appreciate the suggestions.

---

### Post by rubylaser on 2011-02-08
Well, I don't run any mdadm arrays in RAID10, but setting an array up in RAID10 isn't any trickier than any other RAID level.  But, I just checked the man page for mdadm, and even though I'm running a much newer version of mdadm than is in Ubuntu 10.10, the --grow option is not showing RAID10 as a level that it can reshape.
> Grow (or shrink) an array, or otherwise reshape it in some  way.
              Currently supported growth options including changing the active
              size of component devices and  changing  the  number  of  active
              devices  in RAID levels 1/4/5/6, changing the RAID level between
              1, 5, and 6, changing the chunk size and layout  for  RAID5  and
              RAID5, as well as adding or removing a write-intent bitmap.

I'll setup a virtual machine and try it tonight to see if it works or not.  Personally, I'd still go with RAID6 instead of 10.  For media, you're going to waste a ton of space for RAID10 without any extra parity protection.

---

### Post by rubylaser on 2011-02-08
Well, here's my test.  This is with the latest stable version of mdadm (much newer than the version that ships with Ubuntu 10.10, version 2.6.7.1 - 15th October 2008 ).

Here's the newest version
```
root@mdadm-test:~# mdadm -V
mdadm - v3.1.4 - 31st August 2010
```

Creating the array.
```
root@mdadm-test:~# mdadm --create --verbose /dev/md0 --metadata 1.2 --level=10 --raid-devices=4 /dev/sd[bcde]1 
mdadm: layout defaults to n2
mdadm: chunk size defaults to 512K
mdadm: layout defaults to n2
mdadm: layout defaults to n2
mdadm: layout defaults to n2
mdadm: layout defaults to n2
mdadm: size set to 1043968K
mdadm: array /dev/md0 started.
```

Watching it sync...
```
root@mdadm-test:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid10 sde1[3] sdd1[2] sdc1[1] sdb1[0]
      2087936 blocks super 1.2 512K chunks 2 near-copies [4/4] [UUUU]
      [=====>...............]  resync = 27.8% (582912/2087936) finish=0.1min speed=194304K/sec
      
unused devices: <none>
```

Sync Complete...
```
root@mdadm-test:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid10 sde1[3] sdd1[2] sdc1[1] sdb1[0]
      2087936 blocks super 1.2 512K chunks 2 near-copies [4/4] [UUUU]
      
unused devices: <none>
```

Here's the Array structure...
```
root@mdadm-test:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Tue Feb  8 19:09:35 2011
     Raid Level : raid10
     Array Size : 2087936 (2039.34 MiB 2138.05 MB)
  Used Dev Size : 1043968 (1019.67 MiB 1069.02 MB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent

    Update Time : Tue Feb  8 19:11:03 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : near=2
     Chunk Size : 512K

           Name : mdadm-test:0  (local to host mdadm-test)
           UUID : 3b5636d7:ba53bd11:9d6dbfd7:9b8a351f
         Events : 17

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
```

Adding 2 new disks, like you're thinking of doing...
```
root@mdadm-test:~# mdadm --add /dev/md0 /dev/sd[fg]1
mdadm: added /dev/sdf1
mdadm: added /dev/sdg1
```

Now try to grow the array to add the new disks.
```
root@mdadm-test:~# mdadm --grow /dev/md0 --raid-devices=6
[COLOR="Red"]**mdadm: raid10 array /dev/md0 cannot be reshaped.**[/COLOR]
```

So, you're not going to want to go with RAID10 if you plan on adding new disks to the array because it does not support reshaping RAID10.  This will work fine with RAID5/6 though.  So, again, I'm back to suggesting RAID6 (with a spare if you're really want to be conscientious with your data).

Hope that helps.

---

### Post by rubylaser on 2011-02-08
The only other way I can think of doing this is creating the array with the 2 disk shown as missing, but you'll have to run that test on your own if you want...
```
root@mdadm-test:~# mdadm --create --verbose /dev/md0 --metadata 1.2 --level=10 --raid-devices=6 /dev/sd[bcde]1 missing missing
```
****The Above is Untested****

This would make your array run in degraded mode, but again, I REALLY wouldn't do this :)  Just go with RAID6.

---

### Post by geddy2112 on 2011-02-08
Good to know ruby... thank you for the info.
 
Should be putting this sucker together over the weekend.  I will be checking in here for sure!

---

### Post by cascade9 on 2011-02-09
> **rubylaser said:**
> Ubuntu will work just fine with the new 3TB Hitachi drives, so you won't have to worry about that (although, I believe these are advanced format drives, so you'll want to align the partition to 4K sectors with parted).

If your BIOS doesnt support the drives, then you wont be able to use them at all, unless you get some form of HBA (host bus adapter). 

+1 on RAID 5/6. If you can run 3TB drives with that motherboard then 5 3TB drives would give you 12TB (RAID 5) or 9TB (RAID 6). If it was me, I'd probably hold off until I could get 5 x 3TB drives. Or possibly get 4 x 3TB drives with RAID5, then add a drive later and move to RAID6. 

With a 5 drives RAID array, you can then use the SSD on the ICH9R controller. So you dont have to worry about PCIe SATA cards causing extra annoyance, and have to check for linux support etc..

---

### Post by geddy2112 on 2011-02-09
> **cascade9 said:**
> +1 on RAID 5/6. If you can run 3TB drives with that motherboard then 5 3TB drives would give you 12TB (RAID 5) or 9TB (RAID 6). If it was me, I'd probably hold off until I could get 5 x 3TB drives. Or possibly get 4 x 3TB drives with RAID5, then add a drive later and move to RAID6. 
 
With a 5 drives RAID array, you can then use the SSD on the ICH9R controller. So you dont have to worry about PCIe SATA cards causing extra annoyance, and have to check for linux support etc..
 
Thanks guys. After reading your posts and doing a little more research, I think I will go with RAID6. I really appreciate the insight... this is all new to me.
 
I have no problem committing to 5 drives if that is going to be my best option. I just want to be set up and have everything backed up once in place (ripping 2.5 TB worth of movies took a long time). So on a RAID6 with 5 drives I would show 9TB of storage with full redundancy, correct?
 
Thanks again.

---

### Post by rubylaser on 2011-02-09
You wouldn't have 9TB usable, you'd have about 8.38TB available.  Click here to understand why there's less than you'd think... [http://kb.epowermac.com.au/questions/27/Understanding+Advertised+vs+Actual+Drive+Storage+Capacities]("http://kb.epowermac.com.au/questions/27/Understanding+Advertised+vs+Actual+Drive+Storage+Capacities")

And, you'd have enough redundancy to survive 2 hard drive failures before losing the array.  Just make sure to setup smartmontools to monitor your drive health, and mdadm to email you if a disk falls out of the array.

Also, if you only have 2.5TB of movies, you could buy 4 disks right now and run them in RAID6. Then, laster you could expand the array for more space when you needed it if you'd like to keep the costs lower right now.

Hope that helps.

---

### Post by rubylaser on 2011-02-09
You wouldn't have 9TB usable, you'd have about 8.38TB available.  Click here to understand why there's less than you'd think... [http://kb.epowermac.com.au/questions/27/Understanding+Advertised+vs+Actual+Drive+Storage+Capacities]("http://kb.epowermac.com.au/questions/27/Understanding+Advertised+vs+Actual+Drive+Storage+Capacities")

And, you'd have enough redundancy to survive 2 hard drive failures before losing the array.  Just make sure to setup smartmontools to monitor your drive health, and mdadm to email you if a disk falls out of the array.

Also, if you only have 2.5TB of movies, you could buy 4 disks right now and run them in RAID6, then expand the array later for more space if you'd like to keep the costs lower. (That'd be about 5.58TB available, so more than double your current collection).

Hope that helps.

---

### Post by geddy2112 on 2011-02-09
> **rubylaser said:**
> You wouldn't have 9TB usable, you'd have about 8.38TB available. Click here to understand why there's less than you'd think... [http://kb.epowermac.com.au/questions/27/Understanding+Advertised+vs+Actual+Drive+Storage+Capacities](http://kb.epowermac.com.au/questions/27/Understanding+Advertised+vs+Actual+Drive+Storage+Capacities)
 
And, you'd have enough redundancy to survive 2 hard drive failures before losing the array. Just make sure to setup smartmontools to monitor your drive health, and mdadm to email you if a disk falls out of the array.
 
Also, if you only have 2.5TB of movies, you could buy 4 disks right now and run them in RAID6, then expand the array later for more space if you'd like to keep the costs lower. (That'd be about 5.58TB available, so more than double your current collection).
 
Hope that helps.
 
Yep, makes sense. I was commenting on Cascade's post about having 12TB in RAID5 and 9TB in RAID6 with 5 3TB drives. I understand those are rounded.
 
And you have already shown me that it is possible to add on drives as I go... So I take it that running RAID6 does not matter if there is 4, 5, 6, or 7 drives? 
 
Thanks again guys :)

---

### Post by rubylaser on 2011-02-10
With RAID6 you can add drives to the array, and it doesn't matter if you have 4,5,6,7+ drives, other than long resyncing times if you try to extend the array.  If you can afford it now, I'd buy as many disks as you plan to have at the end.  5 disks was a good recommendation, and will give you LOTS of room to grow.

---

