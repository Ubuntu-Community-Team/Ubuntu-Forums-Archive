---
title: "mdadm recovery for RAID 10"
date: 2015-02-21
forum: Server Platforms
---

### Post by rtotten on 2015-02-21
I've had a RAID 10 array running for long enough to recover from a few hard drive failures. My latest is especially nasty and I'm having trouble on re-assembly. I had everything on track for a simple recovery, but during the rebuild phase another drive's cable came loose. Now the simple fixes aren't working and I'm apprehensive of recreating the array without a second opinion.

When I attempt an --assemble --scan, I get the following response (adding a '--force' doesn't change anything):
 ```
mdadm: /dev/md127 assembled from 2 drives - not enough to start the array.
```

I've attached the results of mdadm --examine for each of my 'raided' drives and mdadm -D for each array. I've also attached my /proc/mdstat and /etc/mdadm/mdadm.conf files.
If any of you mdadm experts have a few minutes to take a look, I would be hugely grateful for your advice.

Thank you

---

### Post by darkod on 2015-02-22
Which array is sdi1 part of? md1?

Because in the mdadm -D output it shows as part of md1, which is shown as clean and running, but in the mdadm --examine results of sdb1, sdd1 and sde1 it shows sdi1 as part of md127. And it does NOT show sde1 as part of md127 which it should be, as it seems...

---

### Post by darkod on 2015-02-22
So, md1 looks good and running right? We should focus only on the other array?

First of all, I would start using md2 instead of md127. Very often mdadm can "rename" an array to md127, sometimes when it has an issue, sometimes without any existing issue... To be sure your array is really how you set it up, I would avoid running it as md127.

Then... looking at the examine results of sdb1, sdd1 and sde1, there seems to be quite inconsistency. Are all these outputs taken at the same time, of you were doing some actions in between? Look at the sdd1 results for example:
> /dev/sdd1:          Magic : a92b4efc
        Version : 0.90.00
           UUID : 857e2b85:e71c0abd:a60d56c2:4a9042a3
  Creation Time : Mon Mar 28 22:57:37 2011
     Raid Level : raid10
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 3907023872 (3726.03 GiB 4000.79 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 127


    Update Time : Wed Feb 18 18:52:43 2015
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 1d4ccb15 - correct
         Events : 54387


         Layout : far=2
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
[COLOR=#ff0000]this     2       8      129        2      active sync   /dev/sdi1[/COLOR]


   0     0       8       17        0      active sync   /dev/sdb1
   1     1       0        0        1      faulty removed
   2     2       8      129        2      active sync   /dev/sdi1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       33        4      spare   /dev/sdc1

It seems to "think" it's sdi1, not sdd1. Is the output pasted correctly?

What you could try is manually assembling the array but you need to know the order of the members. The above confusion makes me doubt I can get the order right. So it needs to be cleared first...

---

### Post by rtotten on 2015-02-22
Darko,


    Thank you for your time.


    Sorry about the misleading/unexplained attachments. /dev/md1 is alright, /dev/md127 is the one I'm attempting to reassemble. Furthermore, the mdadm -D output for /dev/md127 was before getting my original rebuild started. Since I knocked one of the cables loose during /dev/md127's rebuild, I haven't been able to reassemble. The auto-renaming to /dev/md127 was always weird to me, but occurred during a previous issue. Since the array was previously running with /dev/md127, should I rename or try to reassemble first? All the --examine outputs were taken at the same time with the following command:


```
mdadm --examine /dev/sd[bcdefghij]1 > mdadm-examine-disks.txt

```

Below is another capture of mdadm --examine for /dev/sd[di]1


```
ubu% sudo mdadm --examine /dev/sd[di]1
/dev/sdd1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 857e2b85:e71c0abd:a60d56c2:4a9042a3
  Creation Time : Mon Mar 28 22:57:37 2011
     Raid Level : raid10
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 3907023872 (3726.03 GiB 4000.79 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 127


    Update Time : Wed Feb 18 18:52:43 2015
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 1
  Spare Devices : 1
       Checksum : 1d4ccb15 - correct
         Events : 54387


         Layout : far=2
     Chunk Size : 64K


      Number   Major   Minor   RaidDevice State
this     2       8      129        2      active sync   /dev/sdi1


   0     0       8       17        0      active sync   /dev/sdb1
   1     1       0        0        1      faulty removed
   2     2       8      129        2      active sync   /dev/sdi1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       33        4      spare   /dev/sdc1
/dev/sdi1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : f25a7caf:b39ae013:bd1ed6e0:d6629b8a
           Name : ubu:1  (local to host ubu)
  Creation Time : Sat Jul 23 11:35:26 2011
     Raid Level : raid10
   Raid Devices : 4


 Avail Dev Size : 3907021954 (1863.01 GiB 2000.40 GB)
     Array Size : 3907020800 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907020800 (1863.01 GiB 2000.39 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=1154 sectors
          State : clean
    Device UUID : 8f394c37:92c824ea:e48e1b54:1dabb535


    Update Time : Thu Feb 19 03:15:55 2015
       Checksum : 31d33e8c - correct
         Events : 465874


         Layout : far=2
     Chunk Size : 512K


   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)

```



/dev/sdi1 is part of /dev/md1, but is showing up under /dev/md127 while examining /dev/sdd1. Could this be causing mdadm's confusion? Would it be safe to tell /dev/md127 to fail /dev/sdi1 to remove it from the array? If failing /dev/sdi1 out of /dev/md127 drops it from /dev/md1 as well, I can always manually add it back to /dev/md1 and rebuild.


Thanks again for your help.

rtotten

---

### Post by darkod on 2015-02-23
What is sdc1? A new member that is acting as spare right now because md127 is not running to start rebuilding?

From sdb1, sdd1 and sde1 do you know their order in md127 so we can try manual assemble? I can't look at you attachments right now to refresh my memory. If you know the order of members we could give it a shot.

---

### Post by darkod on 2015-02-23
OK, I just checked and according to mdadm -D /dev/md127 it says the order of members is:
0 sdb1
1 missing
2 sdd1
3 sde1

So, you can try assembling it by something like:
```
mdadm --assemble -v /dev/md127   (probably will fail)
mdadm --assemble /dev/md127 /dev/sdb1 missing /dev/sdd1 /dev/sde1
```

That might still fail because the sdd1 event counter is slightly different from sdb1 and sde1. If it fails in the above format, next option is probably to force it by adding --force. I think that should not hurt data, especially since sdd1 counter is very similar to sdb1 and sde1.

In case you can manage to start the array with the missing member, it's easy later to add a new disk and let it resync.

Also, speaking in general, is there a specific reason you selected raid10? Did you have raid1 first and then added more disk and made it raid10? Is it for performance? I am asking because compared to raid6 I do not see many advantages for raid10. Maybe performance speed, but on the other hand with a raid6 array of four disks you would still have a working array if two disks fail. While with raid10 it depends which two disks fail, if it will keep running or not...

---

### Post by rtotten on 2015-02-23
Darko,

    Sorry for my delayed response.
    Output from the suggested commands is below:

```
ubu% sudo mdadm --assemble -v /dev/md127
mdadm: looking for devices for /dev/md127
mdadm: /dev/sdi1 has wrong uuid.
mdadm: /dev/sdh1 has wrong uuid.
mdadm: /dev/sdg1 has wrong uuid.
mdadm: /dev/sdf1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdc1
mdadm: /dev/sde1 is identified as a member of /dev/md127, slot 3.
mdadm: /dev/sdd1 is identified as a member of /dev/md127, slot 2.
mdadm: /dev/sdb1 is identified as a member of /dev/md127, slot 0.
mdadm: no uptodate device for slot 2 of /dev/md127
mdadm: added /dev/sdd1 to /dev/md127 as 2 (possibly out of date)
mdadm: added /dev/sde1 to /dev/md127 as 3
mdadm: added /dev/sdb1 to /dev/md127 as 0
mdadm: /dev/md127 assembled from 2 drives - not enough to start the array.
ubu% sudo mdadm --assemble /dev/md127 /dev/sdb1 missing /dev/sdd1 /dev/sde1
mdadm: cannot open device missing: No such file or directory
mdadm: missing has no superblock - assembly aborted
ubu% sudo mdadm --assemble --force /dev/md127 /dev/sdb1 missing /dev/sdd1 /dev/sde1
mdadm: cannot open device missing: No such file or directory
mdadm: missing has no superblock - assembly aborted
ubu%

```    

Do I need to be creating to use 'missing?' Do I have any other options before attempting to recreate?

I chose RAID 10 out of the box, because I liked how it provided the redundancy of RAID 1 with the performance of RAID 0. It also seems to be a simpler layout. A simpler layout would seem to provide simpler management, while requiring fewer resources, but these are only hunches and I'm the one looking for help! How does RAID 6 stack up? Performance really doesn't need to be a driver here.

Thanks,

rtotten

---

### Post by darkod on 2015-02-24
Actually I wasn't sure if you can use missing with assemble or only with create. At least we are getting closer, sdb1, sdd1 and sde1 were detected as members of md127, with sdd1 slightly out of date (we knew that from the event counter).

It looks like the options are:
Try assemble with force
Try create with assume-clean (to avoid resync and destruction of current data)

The man page that some corruption is possibly if using force to assemble but in your case the sdd1 counter is so close to the other two that I don't think you are risking much corruption of data. Here is the extract:
> -f, --force
Assemble the array even if the metadata on some devices appears to be out-of-date. If mdadm cannot find enough working devices to start the array, but can find some devices that are recorded as having failed, then it will mark those devices as working so that the array can be started. An array which requires --force to be started may contain data corruption. Use it carefully.

The decision is yours. To me it looks like the best option right now is:
```
mdadm --assemble -v --force /dev/md127
```

There should not be much data corrupted, if any... That should start the array in my opinion. After that if you add sdc1 it will start rebuilding right away.

PS. I don't think --force needs you to specify the devices, especially since it detects them as part of md127. But in case the above doesn't work, try with:
```
mdadm --assemble -v --force /dev/md0 /dev/sd[bde]1
```

---

### Post by rtotten on 2015-02-24
Darko,

    I beat the --assemble approach like a dead horse, but it looks like it's time to recreate. How does the following look?

```
sudo mdadm --create --assume-clean --level 10 --num-devices 4 --chunk 64 --parity f2 /dev/md0 /dev/sdb1 missing /dev/sdd1 /dev/sde1
```

Thanks,

Robbie

---

### Post by rtotten on 2015-02-24
Another idea: would it work to clone /dev/sdd1 to /dev/sdc1 and attempt creating a RAID 10 array with /dev/sdb1 and /dev/sdd1 and two missing drives? If things work out, I can add /dev/sdc1 and /dev/sde1; if not, I haven't lost everything.

---

### Post by darkod on 2015-02-25
To create raid10 with two missing members, it depends which two members. That's the limitation of raid10. It can work with two members failed but only if those members do not form a mirror. In your case it seems the two failed members are actually forming a mirror and that's why it doesn't want to start with only sdb1 and sde1.

If you tried the assemble without success, yes, the only thing left is create with --assume-clean. The command you posted looks right, if those are the option you used to create the array in the first place. You can give it a shot.

---

### Post by rtotten on 2015-03-03
Darko,

    I regularly refreshed this thread's page, thinking you had abandoned me... then I realized there was a second page (ha!)
    Issuing the create worked, but I didn't specify the metadata version. Since mdadm defaults to 1.2 and my array was using 0.90, I believe some metadata was overwritten. On to my next disaster!

    Thank you very much for your help with everything. I sincerely appreciate you taking the time to help me out.

rtotten

---

### Post by darkod on 2015-03-04
Strange. I was also under the impression that mdadm can recognize the metadata version and use the correct one. I hope you didn't lose any data and the array is still operational.

---

