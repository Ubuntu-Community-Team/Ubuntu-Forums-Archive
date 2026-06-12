---
title: "Lost data and raid 5 does not mount"
date: 2017-12-10
forum: Server Platforms
---

### Post by daniele29 on 2017-12-10
Hello everyone.
Recently, as I was moving data, the machine stopped seeing the mouse.
I  waited for the end of the transfer and I made the mistake of resetting  the machine instead of giving the shutdown command (damn Windows  background).
Result?
All data of the last transfer lost ...
I have to say  that due to the frequency ram I could no longer set up correctly, I had  DMA, HMS and PIO violations at boot or reboot, now solved.
Furthermore, the RAID has disappeared again.
As in the "RAID 5 missing" thread I gave the command
sudo mdadm --verbose --assemble --scan
The output is
```
mdadm: Unknown keyword sudo
mdadm: looking for devices for /dev/md/1
mdadm: no RAID superblock on /dev/sdr1
mdadm: no RAID superblock on /dev/sdr
mdadm: no RAID superblock on /dev/sr0
mdadm: no RAID superblock on /dev/sdq1
mdadm: no RAID superblock on /dev/sdq
mdadm: /dev/sdp1 is busy - skipping
mdadm: no RAID superblock on /dev/sdp
mdadm: /dev/sdo1 is busy - skipping
mdadm: no RAID superblock on /dev/sdo
mdadm: no RAID superblock on /dev/sdn1
mdadm: no RAID superblock on /dev/sdn
mdadm: no RAID superblock on /dev/sdm2
mdadm: no RAID superblock on /dev/sdm1
mdadm: no RAID superblock on /dev/sdm
mdadm: no RAID superblock on /dev/sdl2
mdadm: no RAID superblock on /dev/sdl1
mdadm: no RAID superblock on /dev/sdl
mdadm: no RAID superblock on /dev/sdk3
mdadm: no RAID superblock on /dev/sdk2
mdadm: no RAID superblock on /dev/sdk1
mdadm: no RAID superblock on /dev/sdk
mdadm: /dev/sdj1 is busy - skipping
mdadm: no RAID superblock on /dev/sdj
mdadm: /dev/sdi1 is busy - skipping
mdadm: no RAID superblock on /dev/sdi
mdadm: no RAID superblock on /dev/sdh2
mdadm: no RAID superblock on /dev/sdh1
mdadm: no RAID superblock on /dev/sdh
mdadm: no RAID superblock on /dev/sdg2
mdadm: no RAID superblock on /dev/sdg1
mdadm: no RAID superblock on /dev/sdg
mdadm: no RAID superblock on /dev/sdf2
mdadm: no RAID superblock on /dev/sdf1
mdadm: no RAID superblock on /dev/sdf
mdadm: no RAID superblock on /dev/sde2
mdadm: no RAID superblock on /dev/sde1
mdadm: no RAID superblock on /dev/sde
mdadm: no RAID superblock on /dev/sdd2
mdadm: no RAID superblock on /dev/sdd1
mdadm: no RAID superblock on /dev/sdd
mdadm: no RAID superblock on /dev/sdc2
mdadm: no RAID superblock on /dev/sdc1
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdb1 is busy - skipping
mdadm: no RAID superblock on /dev/sdb
mdadm: /dev/sda1 is busy - skipping
mdadm: no RAID superblock on /dev/sda
mdadm: no RAID superblock on /dev/ram15
mdadm: no RAID superblock on /dev/ram14
mdadm: no RAID superblock on /dev/ram13
mdadm: no RAID superblock on /dev/ram12
mdadm: no RAID superblock on /dev/ram11
mdadm: no RAID superblock on /dev/ram10
mdadm: no RAID superblock on /dev/ram9
mdadm: no RAID superblock on /dev/ram8
mdadm: no RAID superblock on /dev/ram7
mdadm: no RAID superblock on /dev/ram6
mdadm: no RAID superblock on /dev/ram5
mdadm: no RAID superblock on /dev/ram4
mdadm: no RAID superblock on /dev/ram3
mdadm: no RAID superblock on /dev/ram2
mdadm: no RAID superblock on /dev/ram1
mdadm: no RAID superblock on /dev/ram0

```
I then also gave the command
sudo mdadm --examine /dev/sd[abcdfg]1
The output is
```
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 04bfdfa2:36fd9f17:2095a874:8fd6bde6
           Name : NAS3200:1
  Creation Time : Sun Jul  3 21:59:13 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860265887 (2794.39 GiB 3000.46 GB)
     Array Size : 14650662400 (13971.96 GiB 15002.28 GB)
  Used Dev Size : 5860264960 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : e875c057:078c39eb:145da265:f5b6f49e

    Update Time : Fri Nov 17 01:03:41 2017
       Checksum : b27cd3b7 - correct
         Events : 17182

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAAAAA ('A' == active, '.' == missing)
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 04bfdfa2:36fd9f17:2095a874:8fd6bde6
           Name : NAS3200:1
  Creation Time : Sun Jul  3 21:59:13 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860265887 (2794.39 GiB 3000.46 GB)
     Array Size : 14650662400 (13971.96 GiB 15002.28 GB)
  Used Dev Size : 5860264960 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : bd0327c4:84d752c3:c01f1f22:801f0b58

    Update Time : Sun Nov 19 21:11:35 2017
       Checksum : 6c910978 - correct
         Events : 46652

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : A.AAAA ('A' == active, '.' == missing)
mdadm: No md superblock detected on /dev/sdc1.
mdadm: No md superblock detected on /dev/sdd1.
mdadm: No md superblock detected on /dev/sdf1.
mdadm: No md superblock detected on /dev/sdg1.

```
After that I gave the command
cat /proc/mdstat
The ouput is 
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : inactive sdj1[5](S) sdi1[6](S) sdo1[4](S) sdp1[2](S) sda1[1](S) sdb1[0](S)
      17580797661 blocks super 1.2

```
I tried to give the command
sudo mdadm --stop /dev/mdX
and the output is
```
mdadm: Unknown keyword sudo
mdadm: error opening /dev/mdX: No such file or directory
mdadm: error opening output: No such file or directory

```
At this point I do not know what to do, could you kindly give me a hand?
Thank you.
Greetings.
Daniele

---

### Post by darkod on 2017-12-11
First, about that "Unknown keyword sudo" message. You only use sudo in front if you are running system commands with your standard user. If you are running them as root do NOT put sudo in front.

Second, from your output it seems the disks have changed letters after the reset. Try to check the mdadm superblocks with:
```
sudo mdadm --examine /dev/sd[abijop]1
```

Run only that and post the output, do not run anything else because if you run wrong commands you might lose data in case it can still be saved.

---

### Post by daniele29 on 2017-12-17
Hello darkod
I'm sorry, I did not notice the change ...
New reset (I do not understand why the system is unstable), new drive letters.
Now 
```
 Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : inactive sdi1[6](S) sdo1[2](S) sdj1[5](S) sdn1[4](S) sda1[1](S) sdb1[0](S)
      17580797661 blocks super 1.2

```

One question: since the  sequence of drive letters to the command ```
cat / proc / mdstat
``` was ```
sd[jiopab]1
``` of the previous message, why did you ask me to ceck 
```
sudo  mdadm --examine / dev / sd[abijop]1 
``` ?
Thanks again.
Daniele

P.S. But why do the drive letters change after a reset, since the connection remains the same?

---

### Post by darkod on 2017-12-17
The order of letters in --examine does not matter, the only important thing is to have the correct letters in the command so that it shows the info of mdadm superblocks for all related partitions.

Why do you keep resetting the computer?

We are still waiting the --examine output. And make sure you have all 6 partitions from the raid included in the output.

---

### Post by daniele29 on 2017-12-17
Hi
Ok for the sequence of drive letters of the examine command.
The reset is due to the fact that the machine performs fake booting due to the ram voltage out of place.
Also, in the ram frequencies menu, the correct one disappears (1,600Mhz).
Ok, now I'll give you the ouput of the --examine command.

Ouput
```
/dev/sdi1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 04bfdfa2:36fd9f17:2095a874:8fd6bde6
           Name : NAS3200:1
  Creation Time : Sun Jul  3 21:59:13 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860265887 (2794.39 GiB 3000.46 GB)
     Array Size : 14650662400 (13971.96 GiB 15002.28 GB)
  Used Dev Size : 5860264960 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 61db0909:21b7dd78:38f54e2a:4a41dd73

    Update Time : Sun Nov 19 22:26:37 2017
       Checksum : 8b01c999 - correct
         Events : 46657

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 5
   Array State : ..AAAA ('A' == active, '.' == missing)
/dev/sdo1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 04bfdfa2:36fd9f17:2095a874:8fd6bde6
           Name : NAS3200:1
  Creation Time : Sun Jul  3 21:59:13 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860265887 (2794.39 GiB 3000.46 GB)
     Array Size : 14650662400 (13971.96 GiB 15002.28 GB)
  Used Dev Size : 5860264960 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 306b21c7:c074eb9f:b3b43e2d:ae17c68e

    Update Time : Sun Nov 19 22:26:37 2017
       Checksum : 8dfface3 - correct
         Events : 46657

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : ..AAAA ('A' == active, '.' == missing)
/dev/sdj1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 04bfdfa2:36fd9f17:2095a874:8fd6bde6
           Name : NAS3200:1
  Creation Time : Sun Jul  3 21:59:13 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860265887 (2794.39 GiB 3000.46 GB)
     Array Size : 14650662400 (13971.96 GiB 15002.28 GB)
  Used Dev Size : 5860264960 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 609b425c:8b4cfa37:76a2f7db:b54e7c6d

    Update Time : Sun Nov 19 22:26:37 2017
       Checksum : 489ed9ab - correct
         Events : 46657

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 4
   Array State : ..AAAA ('A' == active, '.' == missing)
/dev/sdn1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 04bfdfa2:36fd9f17:2095a874:8fd6bde6
           Name : NAS3200:1
  Creation Time : Sun Jul  3 21:59:13 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860265887 (2794.39 GiB 3000.46 GB)
     Array Size : 14650662400 (13971.96 GiB 15002.28 GB)
  Used Dev Size : 5860264960 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ee63ac40:5f643a7b:545b2360:f7b9584d

    Update Time : Sun Nov 19 22:26:37 2017
       Checksum : d450de2b - correct
         Events : 46657

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : ..AAAA ('A' == active, '.' == missing)
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 04bfdfa2:36fd9f17:2095a874:8fd6bde6
           Name : NAS3200:1
  Creation Time : Sun Jul  3 21:59:13 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860265887 (2794.39 GiB 3000.46 GB)
     Array Size : 14650662400 (13971.96 GiB 15002.28 GB)
  Used Dev Size : 5860264960 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : e875c057:078c39eb:145da265:f5b6f49e

    Update Time : Fri Nov 17 01:03:41 2017
       Checksum : b27cd3b7 - correct
         Events : 17182

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAAAAA ('A' == active, '.' == missing)
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 04bfdfa2:36fd9f17:2095a874:8fd6bde6
           Name : NAS3200:1
  Creation Time : Sun Jul  3 21:59:13 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860265887 (2794.39 GiB 3000.46 GB)
     Array Size : 14650662400 (13971.96 GiB 15002.28 GB)
  Used Dev Size : 5860264960 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : bd0327c4:84d752c3:c01f1f22:801f0b58

    Update Time : Sun Nov 19 21:11:35 2017
       Checksum : 6c910978 - correct
         Events : 46652

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : A.AAAA ('A' == active, '.' == missing)


```

---

### Post by darkod on 2017-12-17
I will take a look at the superblock data in a short while. But if you have a HW issue you HAVE to sort that out first. It's pointless repairing the array if the machine keep unstable and rebooting itself when it feels like it. The resets are not so good for the HDDs either... So get that sorted out first...

You shouldn't have even installed an OS and put it in production if you didn't have the HW sorted out first.

---

### Post by daniele29 on 2017-12-17
Ok.
Right now the HW problem is solved.
I do not understand where the problem is, the psu tensions are ok, the memtest led is ok, the battery system voltage is ok ....
You're  right, I should not have installed the OS if the machine isn't good, but I  did not immediately understand that the problem is her and not the pen /  ssd drive where I installed the OS ...

---

### Post by darkod on 2017-12-17
Like I said in my previous post, I would first fix any HW issues before continuing to fix the array. When you get to the part of fixing the array, the --examine shows that sda1 is very outdated, so I would leave it out of the assemble at the first moment. You will delete its superblock and add it again to the array later. No point trying to add a member that is so outdated right now.

The other members have identical Events Counter (46657) and only sdb1 has 46652. That is close enough to assemble correctly.

So this is what you need to try (stop the current md1 first and ignore sda1 like it doesn't exist):
```
sudo mdadm --stop /dev/md1
sudo mdadm --verbose --assemble --force /dev/md1 /dev/sd[bonji]1
```

That should assemble the array with 5 members and start it. If that works out good, you can remove sda1 superblock and add it to the array (be sure you are working with the correct device if your letters are moving around!):
```
sudo mdadm --zero-superblock /dev/sda1
sudo mdadm /dev/md1 --add /dev/sda1
```

That should do it...

---

### Post by daniele29 on 2017-12-17
Output
```
sudo mdadm --verbose --assemble --force /dev/md1 /dev/sd[bonji]1
```
```
mdadm: Unknown keyword sudo
mdadm: looking for devices for /dev/md1
mdadm: /dev/sdb1 is identified as a member of /dev/md1, slot 0.
mdadm: /dev/sdo1 is identified as a member of /dev/md1, slot 2.
mdadm: /dev/sdn1 is identified as a member of /dev/md1, slot 3.
mdadm: /dev/sdj1 is identified as a member of /dev/md1, slot 4.
mdadm: /dev/sdi1 is identified as a member of /dev/md1, slot 5.
mdadm: forcing event count in /dev/sdb1(0) from 46652 upto 46657
mdadm: Marking array /dev/md1 as 'clean'
mdadm: no uptodate device for slot 1 of /dev/md1
mdadm: added /dev/sdo1 to /dev/md1 as 2
mdadm: added /dev/sdn1 to /dev/md1 as 3
mdadm: added /dev/sdj1 to /dev/md1 as 4
mdadm: added /dev/sdi1 to /dev/md1 as 5
mdadm: added /dev/sdb1 to /dev/md1 as 0
mdadm: /dev/md1 has been started with 5 drives (out of 6).

```

I am continuing to use sudo despite "Unknown keyword sudo"
Otherwise the system says that I have to be a super user

The raid is restarted, now I try to add sda1

sda1 added.
I have to restart the car now or not?

The machine...
sorry...

---

### Post by darkod on 2017-12-17
No, no need for any restart. Check with 'cat /proc/mdstat' the status of the array. And you can try mounting it now, even before the sda1 sync is finished. I would leave it to finish the sync before trying to use it though...

---

### Post by daniele29 on 2017-12-17
cat /proc/mdstat output
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sda1[7] sdb1[0] sdi1[6] sdj1[5] sdn1[4] sdo1[2]
      14650662400 blocks super 1.2 level 5, 512k chunk, algorithm 2 [6/5] [U_UUUU]
      [>....................]  recovery =  4.6% (137227996/2930132480) finish=319.1min speed=145841K/sec

```

"And you can try mounting it now, even before the sda1 sync is finished."
I do not understand what you mean ...
I now see the raid and I have already mounted it with the 5 discs ...
Do I have to disassemble and reassemble?
I'm sorry, but I do not understand a lot of things about this OS ...
About  the reset: the reset named in the first message was referred to the  button, the second was a "clear cmos", done by removing the system  battery.
I use the google translator, and sometimes I do not realize that he translates badly ...

---

### Post by darkod on 2017-12-17
This is assembling the array, not mounting it. Assembling /dev/md1 is one thing, mounting it to a mount point so you can use it is another thing.

Like for example (if it's not already mounted):
```
sudo mount /dev/md1 /mnt
```

Then you can list the contents of /mnt to check if your data is there. You probably already have a mount point assigned to this array in /etc/fstab, so you can also mount it there...

This is good so far, the array is assembled and sda1 is getting synced. It will take a while, it says maybe 319 minutes (over 5hrs).

---

### Post by daniele29 on 2017-12-17
I'm already copying files ...
is it better that I cancel the operation and wait for tomorrow?

---

### Post by darkod on 2017-12-17
Your choice... I would have waited for sda1 sync to complete first. It is already under load during the sync and you are adding more load by copying files. It is only raid5 so it can't handle multiple member failures. In reality you should not use raid5 for 6 disks, it's too many disks...

---

### Post by daniele29 on 2017-12-17
So I cancel ...
What raid would you recommend me? 6?
What command should I use to check the progress of the synchronization?

---

### Post by darkod on 2017-12-17
The 'cat /proc/mdstat' shows you the progress. You already posted output again, take a better look.

For raid with 6 members it is good practice to have raid6 that can continue working when 2 members are failed.

---

### Post by daniele29 on 2017-12-18
Ah ok...
I have only copied the output for you, I have not looked at him ...
Tomorrow I try to change the system battery.
it is possible that she gives correct voltage to empty, but maybe under load the voltage drops, the mobo is not so young.
About raid 6: can I now perform a raid 6 or do I lose data?
What can you tell me about lost data?
Is there a command or program under Ubuntu that allows me to understand if the files are in the disk or not?
A small OT: I have some problems with Windows raid 5 capacity, can you tell me where in which section to write the post?
I tried to write it in the Windows section, but no one answered me ... :-(
Thanks again Darkod, your help was once again precious.
Greetings.
Daniele
P.S. What  about the change of unit letter (not correct term, but I do not know  how to call sda, sdb etc.) in the moment who I make the clear cmos of the machine?

---

### Post by darkod on 2017-12-18
You could convert the raid5 mdadm array into raid6 but only if it is not full with data. You have 6 disks of 3TB making raid5 array with usable space of 15TB (5x 3TB usable space plus 1x 3TB for parity). A raid6 array has two members for parity, so with your 6 disks you would get only 12TB usable space. If that is enough to fit your data, you can try and plan converting the array into raid6.

Otherwise you would need to buy one more 3TB disk so that you can have 2x 3TB for parity and 5x 3TB = 15TB usable space in raid6 array.

I am not sure what lost data you are talking about. After you mount the array you can check the data on it. When you have much data it is sometimes difficult to know if any is lost until you need to use some files... According to your event counters it doesn't look like any data was lost, only that the array stopped to assemble because one member was very outdated and another one was only little outdated. And raid5 can't assemble with 2 members failed. But that doesn't actually mean data was lost, the array simply stopped to assemble. Now you have that fixed and it should continue working correctly.

The change of disk letter is not very important for mdadm, it can detect which disks are part of the array and assemble it correctly even if letters change. Usually the mobo is reading the disks in certain order and that is how it gives them the letters. And on next restart it should read them again in same order... But anyway the letters are not important for mdadm.

---

### Post by daniele29 on 2017-12-19
Hi
Please, regarding the lost data, read the first post.
In fact, I do not see the files moved before the machine reset trought reset button.

---

### Post by darkod on 2017-12-19
Did you confirm the data was really copied to the array before you reset the machine?

---

