---
title: "Ask HELP for RAID failure"
date: 2015-05-04
forum: Server Platforms
---

### Post by Yingwei_HU on 2015-05-04
I had a server installed Ubuntu 13.04 server version. It was running without any problem for a year until last week.
After once reboot, it failed to access the Ubuntu after showing the grub menu of "Ubuntu/Advanced Option/Memory Test...". The screen kept being ''purple".
We thought it is caused by the failure of building soft RAID of disks.
In our server, there are 2 SSD and 8 HDD. All of them can still be seen in BIOS.
The soft RAID created by Ubuntu installation was configured as:
RAID 1 (mirror): 2 SSD (ext4)
RAID 5: 8 HDD (ext4 and swap)
The Ubuntu OS was set up on the RAID 1 of the 2 SSD. If we unplugged all the 8 HDD, we can still access the Ubuntu and see the RAID of the two SSD.
However, if we plugged 8 HDD, the system stopped in the ''purple" screen after the grub menu.
Does anyone met this kind of problem previously?
Is there any possible to recover the RAID ?
Thank you very much.

---

### Post by darkod on 2015-05-04
When you were installing and when asked if you want the machine to boot in degraded mode, do you remember if you said yes or no?
If you said no, then it might be following those instructions and the raid5 is degraded. That would explain why it can boot without the raid5 disks and not with them
To see what is going on boot the machine with the desktop cd in live mode, and check the arrays. In live mode you will need to add the mdadm package and try to assemble the arrays it can. Something like:
```
sudo apt-get mdadm
sudo mdadm --assemble --scan
```

Then you can check arrays with:
```
cat /proc/mdstat
sudo mdadm -D /dev/mdX
```

Use the -D to get details of all your arrays that get assembled. Post the results here if you have questions.

On a side note, most production servers would use a Long Term Support version (LTS) and 13.04 is not a LTS. Also, building a raid5 from 8 disks is rarely recommended because that's too many disks. But you can think about that after you manage to start the array.

---

### Post by Yingwei_HU on 2015-05-05
Thank you very much for your help.
I have successfully seen the broken RAID in the OS booted from Ubuntu Live CD. 
It seems that one of my hard drives is broken. However, I accidently removed another one of the good drives from the RAID.
Now there are two drives removed. I also find that I can't add the hard drive back to the RAID as the "active sync" type.
The good one now is treated as a spare drive. Is it possible to put it back as "active sync"?
If  2 out of 8 devices are broken in the RAID 5, is it still possible to recover all the information?
I have tried to use "--re-add" but it failed and said "--re-add for /dev/sdk to /dev/md2 is not possible".
The following information is listed by using "sudo mdadm -D /dev/md2"
/dev/md2:
        Version : 1.2
  Creation Time : Mon Aug 12 07:49:28 2013
     Raid Level : raid5
     Array Size : 27348210176 (26081.29 GiB 28004.57 GB)
  Used Dev Size : 3906887168 (3725.90 GiB 4000.65 GB)
   Raid Devices : 8
  Total Devices : 8
    Persistence : Superblock is persistent

    Update Time : Tue May  5 09:32:52 2015
          State : clean, FAILED 
 Active Devices : 6
Working Devices : 7
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : KEZ323:2
           UUID : 333225cd:1e0c0757:cf95f5df:b503e5ec
         Events : 215298

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       0        0        2      removed
       3       8       48        3      active sync   /dev/sdd
       4       8      112        4      active sync   /dev/sdh
       5       8      128        5      active sync   /dev/sdi
       6       8      144        6      active sync   /dev/sdj
       7       0        0        7      removed

       2       8       32        -      faulty spare   /dev/sdc
       8       8      160        -      spare   /dev/sdk

---

### Post by darkod on 2015-05-05
You really got yourself into a mess there. When an array is already degraded you have to be very careful which disk you remove.

Can you post the result of:
```
sudo mdadm --examine /dev/sdk
```

That is assuming that sdk is still the disk reported as spare.

---

### Post by Yingwei_HU on 2015-05-05
ubuntu@ubuntu:~$ sudo mdadm --examine /dev/sdk
/dev/sdk:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 333225cd:1e0c0757:cf95f5df:b503e5ec
           Name : KEZ323:2
  Creation Time : Mon Aug 12 07:49:28 2013
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
     Array Size : 27348210176 (26081.29 GiB 28004.57 GB)
  Used Dev Size : 7813774336 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 5265e3e0:7d9f4810:5ab4bb91:afad0e12

    Update Time : Tue May  5 10:17:10 2015
       Checksum : df5afa87 - correct
         Events : 215308

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : spare
   Array State : AA.AAAA. ('A' == active, '.' == missing)


This is my /dev/sdk. Thank you very much.

---

### Post by darkod on 2015-05-05
Hmm, I wanted to compare the events counters on sdk and md2. To see if they are maybe equal which would help adding the disk back. The events are not equal but md2 has less events than sdk (215298 vs 215308) which I guess is a good thing.
Try simply readding it with:
```
sudo mdadm /dev/md2 --re-add /dev/sdk
```

See how that goes and post any errors it gives you.

---

### Post by Yingwei_HU on 2015-05-05
The error is :
mdadm: --re-add for /dev/sdk to /dev/md2 is not possible

---

### Post by darkod on 2015-05-05
After you removed the disk by mistake, how exactly did you add it back to md2? Because if you used --add it would detect it was part of md2 and mdadm would try --re-add anyway. Did you maybe zero the superblock? But in that case the events counter wouldn't be at 215308.

---

### Post by darkod on 2015-05-05
Since the --re-add doesn't work, the next step would be to force the array to assemble... The command to force md2 to assemble would be like:
```
sudo mdadm --assemble --force /dev/md2 /dev/sd[abdhijk]
```

That will try to force it to assemble with the order of disks as reported by -D. Only sdc is left out since it's failed. You can try that and let us know.

---

### Post by Yingwei_HU on 2015-05-05
Thank you very much.
I did the exact command you suggested.
The error is:
mdadm: clearing FAULTY  flag for device 6  in /dev/md2 for /dev/sdk
mdadm: Marking array /dev/md2 as 'clean'
mdadm: /dev/md2 assembled from 6 drives and 1 spare - not enough to start the array.

The sdk is still spare.

---

### Post by Yingwei_HU on 2015-05-05
More details of assemble and run md2:

ubuntu@ubuntu:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : inactive sdc[2](S) sdb[1](S) sdj[6](S) sdh[4](S) sdi[5](S) sdk[8](S) sda[0](S) sdd[3](S)
      31255100096 blocks super 1.2
       
md1 : active raid1 sdf2[0] sdg2[1]
      453094208 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sdg1[1] sdf1[0]
      15615872 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>
ubuntu@ubuntu:~$ sudo mdadm --assemble --force /dev/md2 /dev/sd[abdhijk]
mdadm: /dev/sda is busy - skipping
mdadm: /dev/sdb is busy - skipping
mdadm: /dev/sdd is busy - skipping
mdadm: /dev/sdh is busy - skipping
mdadm: /dev/sdi is busy - skipping
mdadm: /dev/sdj is busy - skipping
mdadm: /dev/sdk is busy - skipping
ubuntu@ubuntu:~$ sudo mdadm --stop /dev/md2
mdadm: stopped /dev/md2
ubuntu@ubuntu:~$ sudo mdadm --assemble --force /dev/md2 /dev/sd[abdhijk]
mdadm: clearing FAULTY flag for device 6 in /dev/md2 for /dev/sdk
mdadm: Marking array /dev/md2 as 'clean'
mdadm: /dev/md2 assembled from 6 drives and 1 spare - not enough to start the array.
ubuntu@ubuntu:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : inactive sda[0](S) sdk[8](S) sdj[6](S) sdi[5](S) sdh[4](S) sdd[3](S) sdb[1](S)
      27348212584 blocks super 1.2
       
md1 : active raid1 sdf2[0] sdg2[1]
      453094208 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sdg1[1] sdf1[0]
      15615872 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>
ubuntu@ubuntu:~$ sudo mdadm --detail /dev/md2
mdadm: md device /dev/md2 does not appear to be active.
ubuntu@ubuntu:~$ sudo mdadm --run /dev/md2
mdadm: failed to run array /dev/md2: Input/output error
ubuntu@ubuntu:~$ sudo mdadm --detail /dev/md2
/dev/md2:
        Version : 1.2
  Creation Time : Mon Aug 12 07:49:28 2013
     Raid Level : raid5
  Used Dev Size : -1
   Raid Devices : 8
  Total Devices : 7
    Persistence : Superblock is persistent

    Update Time : Tue May  5 10:35:41 2015
          State : active, FAILED, Not Started 
 Active Devices : 6
Working Devices : 7
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : KEZ323:2
           UUID : 333225cd:1e0c0757:cf95f5df:b503e5ec
         Events : 215309

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       0        0        2      removed
       3       8       48        3      active sync   /dev/sdd
       4       8      112        4      active sync   /dev/sdh
       5       8      128        5      active sync   /dev/sdi
       6       8      144        6      active sync   /dev/sdj
       7       0        0        7      removed

       8       8      160        -      spare   /dev/sdk
ubuntu@ubuntu:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : inactive sda[0] sdk[8](S) sdj[6] sdi[5] sdh[4] sdd[3] sdb[1]
      27348212584 blocks super 1.2
       
md1 : active raid1 sdf2[0] sdg2[1]
      453094208 blocks super 1.2 [2/2] [UU]
      
md0 : active raid1 sdg1[1] sdf1[0]
      15615872 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

---

### Post by darkod on 2015-05-06
Strange. Why did it say it cleared a faulty flag from sdk.
And how about trying to force assemble but adding sdc to the list of disks too:
```
sudo mdadm --stop /dev/md2
sudo mdadm --assemble --force /dev/md2 /dev/sd[abcdhijk]
```

Lets see if that helps.

---

### Post by Yingwei_HU on 2015-05-06
I think the FAULTY flag of sdk was added due to the command "mdadm /dev/md2 --fail /dev/sdX --remove /dev/sdX".
In fact, the stragest thing is that we actually did run "mdadm /dev/md2 --fail /dev/sdc --remove /dev/sdc" but somehow sdk was removed from /dev/md2.
We doubly checked the history and found we never tried to remove sdk. SO SAD...
I posted the output of your suggested commands in the next post. Thank you very much for your help.

---

### Post by Yingwei_HU on 2015-05-06
ubuntu@ubuntu:~$ sudo mdadm --stop /dev/md2
mdadm: stopped /dev/md2
ubuntu@ubuntu:~$ sudo mdadm --assemble --force /dev/md2 /dev/sd[abcdhijk]
mdadm: forcing event count in /dev/sdc(2) from 215301 upto 215309
mdadm: clearing FAULTY flag for device 2 in /dev/md2 for /dev/sdc
mdadm: Marking array /dev/md2 as 'clean'
mdadm: /dev/md2 has been started with 7 drives (out of 8) and 1 spare.
ubuntu@ubuntu:~$

---

### Post by Yingwei_HU on 2015-05-06
ubuntu@ubuntu:~$ sudo mdadm -D /dev/md2
/dev/md2:
        Version : 1.2
  Creation Time : Mon Aug 12 15:49:28 2013
     Raid Level : raid5
     Array Size : 27348210176 (26081.29 GiB 28004.57 GB)
  Used Dev Size : 3906887168 (3725.90 GiB 4000.65 GB)
   Raid Devices : 8
  Total Devices : 8
    Persistence : Superblock is persistent

    Update Time : Thu May  7 00:03:10 2015
          State : clean, FAILED 
 Active Devices : 6
Working Devices : 7
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 512K

           Name : KEZ323:2
           UUID : 333225cd:1e0c0757:cf95f5df:b503e5ec
         Events : 215314

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       0        0        2      removed
       3       8       48        3      active sync   /dev/sdd
       4       8      112        4      active sync   /dev/sdh
       5       8      128        5      active sync   /dev/sdi
       6       8      144        6      active sync   /dev/sdj
       7       0        0        7      removed

       2       8       32        -      faulty spare   /dev/sdc
       8       8      160        -      spare   /dev/sdk
ubuntu@ubuntu:~$

---

### Post by darkod on 2015-05-06
This is definitely very weird. Especially the fact that it didn't want to add back a drive recently removed from the array. I asked that in one of the previous posts but you never explained how did you add it back? You did not zero its superblock, right? I am still very confused why it shows up only as spare. If the superblock was zeroed, the disk would not "know" it was part of that array and would be added as spare.

There are few more options to try, but those are the most "dangerous" ones. You always start with the simplest and safest options for re-assemble, but since none of that worked you can decide if you want to try something else.

One thing to try would be --assemble --force again but this time adding --run. This is little bit more dangerous than without --run because it can start the array even if something is wrong, which means part of the data might be lost. In your case it might help that according to you sdk never failed, it was removed by accident. So the data on it should be good, and you should have in fact 7 disks with good data from 8 which should be enough for the array to work. The danger of using that command should be minimal.

Next, is the more dangerous one. You can zero the superblocks on all devices, but that doesn't delete the data on them. Only the mdadm superblock info. Then you create new array with --assume-clean which tells mdadm not to do initial sync. mdadm is smart enough to detect the data and could be possible to create the "new" array by keeping the "old" data. However this is really the last resort... if you wanna give it a try, those separate two procedures would be like:
```
sudo mdadm --stop /dev/md2
sudo mdadm --assemble --force --run /dev/md2 /dev/sd[abcdhijk]
```

Or:
```
sudo mdadm --stop /dev/md2
sudo mdadm --zero-superblock /dev/sd[abcdhijk]
sudo mdadm --create --assume-clean /dev/md2 /dev/sd[abcdhijk]
```

---

### Post by Yingwei_HU on 2015-05-07
Our RAID configuration:
2 SSD, RAID1, Ubuntu 13.04 server (previously boot from this one)
8 HDD, RAID 5, /data

1. One thing I may forget to tell is that we now are using a live USB to boot the Ubuntu 14.04 Desktop in order to see all the HDDs of the broken RAID. This Ubuntu is independent to the original Ubuntu 13.04 server edition. 
We can't boot from the original Ubuntu 13.04 server on the RAID of SSD as long as the HDDs are plugged in the motherboard. The reason may be that we choose not to use degraded RAID in our installation one year ago.
In the new Ubuntu 14.04 Desktop, it can find all the RAIDs and the associated HDDs kind of "correctly". I can still access the RAID of SSD and read/write data on it in the new Ubuntu 14.04 Desktop.
But is it possible to be the reason that it wrongly dropped the sdk even if we specified sdc in the "--remove" command of mdadm ? Maybe it actually uses a different order of devices comparing to the original Ubuntu 13.04 server? 
Is it possible to boot from the original RAID of SSD ( it is still alive) with all the HDDs? chroot? How to change the option to allow boot with a degraded or even broken RAID?

2. --zero --superblock
Yes. I didn't clear the zero superblock of any drive.

3. for the "mdadm --add"
In the first try of adding sdk back to the array, we used "mdadm /dev/md2 --add /dev/sdk" or maybe "mdadm --manage /dev/md2 --add /dev/sdk"

4. --assemble --run --force 
We tried it previously with "[abcdhijk]". In that time , only the sdk was regarded as spare.The RAID array had not known that sdc was broken. After that "force running", the RAID started syncing and failed due to 2 missing disks soon. It then marked the sdc as a "faulty spare". We also found that there are some bad sectors in sdc.
If we want to do this "--assemble --force --run" again, should we replace sdc with a new blank disk?

5. --create --assume-clean
Do we must clear the zero superblock before "create"? Will it cause any problem if we don't clear the super block?
Should we try the create command by using
sudo mdadm --create /dev/md2 /dev/sda /dev/sdb missing /dev/sdd /dev/sdh /dev/sdi /dev/sdj /dev/sdk --assume-clean
Because the sdc must be bad. 
Thank you very much.

---

### Post by darkod on 2015-05-07
I would not try --force --run with a new disk instead of sdc. Even if you are sure it's failed. The new disk would not have a superblock and I don't know what would happen in that case. The idea is to make it run with the existing disks including failed ones. After you have it running you replace the failed disks. But you say you already tried this command so I doubt it will help.

The idea to use --create and missing is good. It might help. But --assume-clean can't be at the back. The --create should have the list of devices at the end. I don't know what would happen if the superblocks are not zeroed. In my logic zeroing the superblocks is to delete any leftover config of the broken array. For example in your case the info in the existing superblocks add sdk only as spare. You want it to stop doing it and zeroing might help you achieve it. The instructions I have for --create --assume-clean say zero the superblocks first.
Also, not sure if you need the --level and --raid-devices but it doesnt hurt using them. So the command would be like:
```
sudo mdadm --create /dev/md2 --level=5 --raid-devices=8 --assume-clean /dev/sda......
```

This assumes you zeroed the superblocks so I only included the create command. The device list is how you posted it in that order. I didn't retype it all.

---

### Post by Yingwei_HU on 2015-05-13
sudo mdadm --stop /dev/md2
sudo mdadm --zero-superblock /dev/sd[abcdhijk]
sudo mdadm --create /dev/md2 --level=5 --raid-devices=8 --assume-clean /dev/sda /dev/sdb missing /dev/sdd /dev/sdh /dev/sdj /dev/sdj /dev/sdk

We finally tried the --create command and successfully loaded the degraded RAID. Although some data is still lost, we rescued most of them. Thank you very much for your help!

---

