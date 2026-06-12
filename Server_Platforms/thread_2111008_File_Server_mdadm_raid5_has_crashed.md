---
title: "File Server mdadm raid5 has crashed"
date: 2013-01-31
forum: Server Platforms
---

### Post by apokkalyps on 2013-01-31
6 months ago I built a file server with a RAID array and put all my files on it.  Today it stopped working.  I got home from work, set my HTPC (in one room) to start playing a media file, which it started streaming immediately.  Then I walked to the back room where the server is and could hear all kinds of beeping noises coming from the server tower.  I'm not sure if this beeping is truly a "beep" or just mechanical vibration of inner parts, but the tone of the beep is very clear almost like a synthesized beep with no overtones.  Also the start and end of the "beep" is very distinct like a 'short' beep of a mobo POST code.  I have heard this "beep" before when the drives are physically jarred.  All but one are Seagate Barracuda 2TB 7200RPM P/N ST2000DM001-9YN164

It sounded like several drives were all beeping simultaneously out of phase, and some of the "beeps" were higher and lower pitched.  Again I do not know if these are truly beeps, or mechanical noise, but it is FAR from ordinary operating noise of the drives and I knew it meant trouble.  The first thing I did was drop to a shell and reboot.  After rebooting, the "beeping" started again.  Typically on bootup, my BIOS detects all the drives and lists them before continuing, and this took MUCH longer than normal.  Then ubuntu started loading (OS is not on the array) and said "/media/vault is not available to be mounted.  press s to skip" So I skipped it.  I got into Ubuntu and the array is not active.  I opened disk utility, and one of the drives seems to be coming on and offline, not good.  But the other drives all have passed SMART diagnostics, although with some errors but still "Good" status.  

> Obligatory emotions:
I am such an idiot.  My hubris to think I could handle maintenance of this thing just from a few tutorials.  I will have lost all my photos for the last 15 years, all of my scanned artwork, all of my writings including 400 pages of notes toward a book, 30 hours of home video from my childhood, all of my programming projects, basically my entire life.  I know it's hard to have any sympathy for an idiot that put every meaningful artifact of his entire life on a raid array with no backup, but fwiw I was saving the money to do the backup.  But for many TB of data it's not cheap.  I'm feeling panic and suffocation just talking about this but trying to keep my emotions in check while I do what I can.  The fact that it was streaming media just fine prior to rebooting (weird sounds aside) gives me just the slightest bit of hope, before hitting the yellow pages looking for a grief counselor.

All parts are 6 months from the store, and the server is powered through a UPS.  I am running 12.04, the raid is on 5 or 6 2TB sata drives plugged into an ASRock Z77 motherboard, using RAID5 configured with mdadm. 

I am looking for guidance through the commands to check everything there is to check to understand the nature of the problem(s) and the probability of recovering any data.  If I have to I will look into professional data recovery.  But I don't know if I should do that now or try some things first.

---

### Post by darkod on 2013-01-31
The first thing to check would be the md device state. If you have it powered down, boot it again skipping the mounting of the array (since you have to do that to continue the boot), and post the output of:
cat /proc/mdstat

That should show all md devices, how many disks/partitions are members, and how many are active.

EDIT PS: On another note, for a storage of this importance, I would seriously consider FreeNAS with RAIDZ2, or at least change the array to raid6. You will have less usanle space, but it can handle two disk failures and still work. But we can discuss that later.

---

### Post by chrisguk on 2013-01-31
I hear your pain man.  I had a similar situation once upon a time and from that point I stayed away from software RAID.

You have a lot of storage space which is a dam shame really.  

First thing I would do is this.

Hit the mdadm –examine command to find which drives have failed.

I have found a few good articles on how to recover data:

[http://askubuntu.com/questions/64156/how-do-i-repair-my-software-raid5-disks]("http://askubuntu.com/questions/64156/how-do-i-repair-my-software-raid5-disks")

[http://ubuntuforums.org/showthread.php?t=958369]("http://ubuntuforums.org/showthread.php?t=958369")

In fact after a quick Google search there are tonnes of articles regarding your issue.  I am sure one of them will assist you with your situation.

---

### Post by darkod on 2013-02-01
I would wait before assigning blame to mdadm. As the Op stated, the beeps are not heard until you actually go into the cabinet of the server. In theory, one disk could have failed a while ago and raid5 array would keep on going. If you don't have any mechanism to do regular checks, you wouldn't even know about it.

You will only find out when a second disk fails.

It could be HW issue, or mdadm issue, too early to say.

If it's HW issue, what ever configuration you have (fakeraid, HW card, SW raid) a raid5 array will fail with two devices failed. Further more, fakeraid which is most commonly used at home, will probably be unrecoverable, while mdadm might still be recoverable. It's definitely more flexible and better to use compared to fakeraid.

If you invest in server grade HW cards at home, that's another story.

With all the urgency, the OP doesn't seem to be checking the thread too often. :)

---

### Post by apokkalyps on 2013-02-01
I took a day away from thinking about it to calm down and be rational.  The "beeping" somehow seems to have stopped.  Now when I boot the machine it comes up and drops me to an initramfs prompt to try to trouble shoot the array, which I exit out of. Then skip the lack of the array at ubuntu start up. 


```
barrett@mainframe:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sda[5](S) sdb[0](S) sdd[4](S) sdc[2](S)
      7813534048 blocks super 1.2
       
unused devices: <none>
barrett@mainframe:~$ sudo mdadm --examine
mdadm: No devices to examine
barrett@mainframe:~$ sudo mdadm --examine /dev/md0
[sudo] password for barrett: 
barrett@mainframe:~$ 

```

As you can see 4 drives are up for the array.  My end goal was to grow this to 8 drives RAID6 where one was a hotspare.  I am embarrassed to say I cannot remember exactly where I was in that process, if I had a 5 or 6 drives on it.  I **think** it was 4 + raid5 parity + hotspare.  Is there any way to even verify this?

mdadm --examine didn't seem to turn much up (maybe because the array is inactive?)

also if this is helpful
```
barrett@mainframe:~$ blkid
/dev/sda: UUID="8bc78af0-d9a9-81e3-7354-9f212f76cd24" UUID_SUB="f18da9cc-27f5-eee4-61ba-900edd6ca8b9" LABEL="mainframe:vault" TYPE="linux_raid_member" 
/dev/sdb: UUID="8bc78af0-d9a9-81e3-7354-9f212f76cd24" UUID_SUB="004a89c7-bd03-e0fe-b6ea-3ab976e5e5e0" LABEL="mainframe:vault" TYPE="linux_raid_member" 
/dev/sdc: UUID="8bc78af0-d9a9-81e3-7354-9f212f76cd24" UUID_SUB="a6ad29b7-35b5-46ae-4bc2-a5afe6bc8252" LABEL="mainframe:vault" TYPE="linux_raid_member" 
/dev/sdd: UUID="8bc78af0-d9a9-81e3-7354-9f212f76cd24" UUID_SUB="1df1fd17-592f-431a-f3f0-5592fbfccdcd" LABEL="mainframe:vault" TYPE="linux_raid_member" 
/dev/sde1: UUID="0acc3250-919f-44c1-a076-ed66ff5d9684" TYPE="ext4" 
/dev/sdf1: LABEL="Library2" UUID="72fd10b8-8a5b-4f11-be62-da7f397f44b7" TYPE="ext4" 
/dev/sdg1: LABEL="Library1" UUID="17b74dce-e201-480e-9ad0-761123175c41" TYPE="ext4" 
/dev/sdh1: UUID="d56d31ff-3c42-4b8e-a8c1-bd1cea757963" TYPE="ext4" 
/dev/sdh2: UUID="d56d31ff-3c42-4b8e-a8c1-bd1cea757963" TYPE="ext4" 
/dev/sdh3: UUID="e80ece6a-6703-4d2c-82a3-706797264f49" TYPE="swap" 
```


> 
cat /etc/mdadm/mdadm.conf
...
ARRAY /dev/md0 metadata=1.2 name=mainframe:vault UUID=8bc78af0:d9a981e3:73549f21:2f76cd24
...


---

### Post by steeldriver on 2013-02-01
> **apokkalyps said:**
> 
```
barrett@mainframe:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sda[5](S) sdb[0](S) sdd[4](S) sdc[2](S)
      7813534048 blocks super 1.2
       
unused devices: <none>
barrett@mainframe:~$ sudo mdadm --examine
mdadm: No devices to examine
barrett@mainframe:~$ sudo mdadm --examine /dev/md0
[sudo] password for barrett: 
barrett@mainframe:~$ 

```.
.
.
mdadm --examine didn't seem to turn much up (maybe because the array is inactive?)


You need to run it on the array members not the assembled /dev/mdX array,  I think, e.g.

```
sudo mdadm --examine /dev/sd[a-d]
```

---

### Post by apokkalyps on 2013-02-01
```
barrett@mainframe:~$ sudo mdadm --examine /dev/sd[a-e]
/dev/sda:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 8bc78af0:d9a981e3:73549f21:2f76cd24
           Name : mainframe:vault  (local to host mainframe)
  Creation Time : Wed Aug 15 21:57:14 2012
     Raid Level : raid5
   Raid Devices : 5

 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 7813531648 (7451.56 GiB 8001.06 GB)
  Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f18da9cc:27f5eee4:61ba900e:dd6ca8b9

    Update Time : Tue Jan 29 04:34:28 2013
       Checksum : 9139486d - correct
         Events : 7170

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 4
   Array State : A.AAA ('A' == active, '.' == missing)
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 8bc78af0:d9a981e3:73549f21:2f76cd24
           Name : mainframe:vault  (local to host mainframe)
  Creation Time : Wed Aug 15 21:57:14 2012
     Raid Level : raid5
   Raid Devices : 5

 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 7813531648 (7451.56 GiB 8001.06 GB)
  Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 004a89c7:bd03e0fe:b6ea3ab9:76e5e5e0

    Update Time : Tue Jan 29 04:34:57 2013
       Checksum : 77edbc17 - correct
         Events : 7176

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : A.... ('A' == active, '.' == missing)
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 8bc78af0:d9a981e3:73549f21:2f76cd24
           Name : mainframe:vault  (local to host mainframe)
  Creation Time : Wed Aug 15 21:57:14 2012
     Raid Level : raid5
   Raid Devices : 5

 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 7813531648 (7451.56 GiB 8001.06 GB)
  Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : a6ad29b7:35b546ae:4bc2a5af:e6bc8252

    Update Time : Mon Jan 28 20:04:27 2013
       Checksum : 7f030895 - correct
         Events : 7169

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAAA ('A' == active, '.' == missing)
/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 8bc78af0:d9a981e3:73549f21:2f76cd24
           Name : mainframe:vault  (local to host mainframe)
  Creation Time : Wed Aug 15 21:57:14 2012
     Raid Level : raid5
   Raid Devices : 5

 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 7813531648 (7451.56 GiB 8001.06 GB)
  Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 1df1fd17:592f431a:f3f05592:fbfccdcd

    Update Time : Tue Jan 29 04:34:42 2013
       Checksum : a9ccac88 - correct
         Events : 7171

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : A.AAA ('A' == active, '.' == missing)
/dev/sde:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)

```



Also, I know that there is a command that would enumerate these but I can't seem to google it up so I took some screenshots of disk utility
[http://pastehtml.com/view/cr3p7ugrg.html to view them]("http://pastehtml.com/view/cr3p7ugrg.html") or the individual images:
/dev/sda : [http://i.snag.gy/tXkj2.jpg](http://i.snag.gy/tXkj2.jpg)
/dev/sdb : [http://i.snag.gy/ZluyV.jpg](http://i.snag.gy/ZluyV.jpg)
/dev/sdc : [http://i.snag.gy/nFFh6.jpg](http://i.snag.gy/nFFh6.jpg)
/dev/sdd : [http://i.snag.gy/8qRms.jpg](http://i.snag.gy/8qRms.jpg)
/dev/sde : [http://i.snag.gy/MdvXc.jpg](http://i.snag.gy/MdvXc.jpg)
Array    : [http://i.snag.gy/pUG3w.jpg](http://i.snag.gy/pUG3w.jpg)

(if you would rather me return the output of a command ill do that)

Notice that the array says it has 5 components.  There are actually 6 drives plugged SATA into my motherboard (not counting the SSD).  One drive is not showing up at all, you can see that between sdb and sdc it goes from port 2 to port 4 on the sata controller.  The drive that's on port 3 is not registering apparently.  So **if** that drive is dead, I still have 6 of the original 5 drives showing green smart statuses.  Except /dev/sde is wierd. As you can see in the screenshot, disk utility says that unlike all the other ones sde has an ext4 partition on it, LABLED "Linux RAID".  I don't know how it got like that but it doesn't seem to be part of the array. (does it?)  So I have 4 out of 5 of the components running, should it not be assembling?

Also, my /proc/mdstat shows all the drives in the array with **(S)** next to them.  Doesn't that mean it's a hot spare?  Does it think all the drives are spares?

---

### Post by darkod on 2013-02-02
Yeah, somehow it has marked all as spares. A raid5 array should still assemble with 4 disks out of 5.

As for the partitons sde1, I guess you used the whole disks as devices when you first created the array sda-sdd, but when adding sde you actually created a partition on it. mdadm can work either way, but I have read it's better to be consistent and not mix them up. You either work with whole disks, or partitions on them.
I prefer creating partitions even if you use the whole disk as a single partition, but it's not necessary.

The event counters are different on all 4 disks shown by examine. And sde doesn't show at all. Since it has a partition, what if you try like:
sudo mdadm --examine /dev/sde1

You can start by trying to auto assemble it, but I doubt it will work:
sudo mdadm --assemble --scan

I think the different counters will not allow it. The good news is that the counter values are very close, there is a way to force it to assemble in cases like that while not damaging the data. I just have to find the correct syntax.

I will also PM someone who is a much better expert in mdadm, lets see if he can join in.

---

### Post by darkod on 2013-02-02
I found a similar case where all disks were marked as Spare. Look here in the first post in the first code section:
[http://ubuntuforums.org/showthread.php?t=1838932](http://ubuntuforums.org/showthread.php?t=1838932)

Later in the post you can see he did manage to assmeble it by using the --force option and the --scan option letting it find its own disk members.

So, in your case it would also be something like:
sudo mdadm --assemble --scan --force /dev/md0

I think that will assemble it only with sda-sdd which are currently shown as members by /proc/mdstat.

With 4 disks it should still become active. If it does, you can consider whether you want to add to the array sde1 as partition, or delete the partition first and add it as a disk sde like the others are.

You can wait with the above procedure if you want, for someone else to give their opinion. In the thread linked above, and another thread I found, it seems to have worked with --force. As I already said, your counters are very close to each other which is always good.

---

### Post by rubylaser on 2013-02-02
The first thing I'd do is stop any running arrays.
```
sudo -i
mdadm --stop /dev/md0
```

The next step is to force assemble the array. If that doesn't work, we can re-create the array's metadata, but I like to leave that step for last.  Here's your next step.

```
mdadm --assemble --force /dev/md0 /dev/sd[abcd]
```

---

### Post by prodigy_ on 2013-02-02
Well, if more than one drive physically fails in a RAID5 the array can be beyond saving no matter if it's software or hardware. Long story short, you ALWAYS want to have a fresh enough backup of any valuable data.

People often misunderstand the purpose of RAID5. Even though it has redundancy, it doesn't magically protect your data from any possible accident. The main benefit of having a RAID5 is that when you run it in corporate environment and have spare drives at hand in most cases it lets you get back on track really fast. It can help minimize the downtime but you want to make backups anyway.

At home RAID5 is usually somewhere between useless and harmful unless you really have a reason to invest in reliable hardware. And Seagate drives coming with 2 years (or is it 1 year these days?) warranty just scream unreliable.

---

### Post by rubylaser on 2013-02-02
4 of the 5 drives are still working, so this should be salvageable.  I would guess that smartmontools + email alerting wasn't setup, so the OP never knew the first disk failed.  I love mdadm, but for most home media servers, I become more convinced that SnapRAID is a better solution (pictures, home movies, music, videos, etc.).  All that being said, rubbing salt in someone's wounds about backup when they risk losing all of their family pictures is hardly productive.  Let's get this array working again, and then talk about proper backup :)

---

### Post by apokkalyps on 2013-02-02
No luck, interestingly, it says 4 drives is not enough to start the array.

```
barrett@mainframe:~$ sudo mdadm --examine /dev/sde1
[sudo] password for barrett: 
mdadm: No md superblock detected on /dev/sde1.
barrett@mainframe:~$ sudo -i
root@mainframe:~# mdadm --stop /dev/md0
mdadm: stopped /dev/md0
root@mainframe:~# mdadm --assemble --force /dev/md0 /dev/sd[abcd]
mdadm: forcing event count in /dev/sdd(3) from 7171 upto 7176
mdadm: forcing event count in /dev/sda(4) from 7170 upto 7176
mdadm: forcing event count in /dev/sdc(2) from 7169 upto 7176
mdadm: clearing FAULTY flag for device 2 in /dev/md0 for /dev/sdc
mdadm: clearing FAULTY flag for device 3 in /dev/md0 for /dev/sdd
mdadm: clearing FAULTY flag for device 0 in /dev/md0 for /dev/sda
mdadm: Marking array /dev/md0 as 'clean'
mdadm: /dev/md0 assembled from 4 drives - not enough to start the array.
root@mainframe:~# mdadm --assemble --force /dev/md0 /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde1
mdadm: /dev/sda is busy - skipping
mdadm: /dev/sdb is busy - skipping
mdadm: /dev/sdc is busy - skipping
mdadm: /dev/sdd is busy - skipping
mdadm: no recogniseable superblock on /dev/sde1
mdadm: /dev/sde1 has no superblock - assembly aborted
root@mainframe:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdb[0](S) sda[5](S) sdd[4](S) sdc[2](S)
      7813534048 blocks super 1.2
       
unused devices: <none>
root@mainframe:~# 
```

Not sure what to make of this.  If four isn't enough, then it must have had 6 drives, but sde or sde1 doesn't appear to be a raid member at all.

---

### Post by apokkalyps on 2013-02-02
I went down to the "dead" drive on sata port 3 and noticed physical damage on the molex connection where the data cable plugs in.  I forgot to mention in the OP that when I brought up disk utility the first time I rebooted it (during all that beeping), one drive was appearing and disappearing out of the list.  The plastic peice that braces the metal contacts on the SATA jack has come off and all the metal peices are just kindof hanging there bent.  I'm not sure if there is further damage besides this (maybe the innards were already damaged from the original problem and then I broke the connector troubleshooting), or maybe it was this loose connection that originated the problem.  But I work at an engineering/prototyping firm and I will take it in monday to have one of the pros solder a sata cable directly to those pins.

Whether that works or not, I still don't get how 4 drives isn't enough, if sde isn't a raid member.


I do want to say thanks everyone for your thoughts and help!

---

### Post by darkod on 2013-02-02
You said earlier you don't precisely remember how far you got with your plans and the array changes.

Are you sure it was a 5 disk raid5 array + spare or 6 disk raid5 array?

A 6 disk array wouldn't start with only 4 disks.

---

### Post by rubylaser on 2013-02-02
All of the disks metadata were showing a 5 disk RAID5.  It also pulled the event counters up to match on each drive so this should be able to start.  As a side note, why don't you replace the damaged molex plug with a functional molex cable?  How about passing the run flag with your start command?

```
sudo -i
mdadm --stop /dev/md0
mdadm --assemble --force --run --verbose /dev/md0 /dev/sd[abcd]
```

---

### Post by apokkalyps on 2013-02-02
That did it!  Adding the --run parameter seems to have made the difference.  

```
root@mainframe:~# mdadm --stop /dev/md0
mdadm: stopped /dev/md0
root@mainframe:~# mdadm --assemble --force --run --verbose /dev/md0 /dev/sd[abcd]
mdadm: looking for devices for /dev/md0
mdadm: /dev/sda is identified as a member of /dev/md0, slot 4.
mdadm: /dev/sdb is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 3.
mdadm: no uptodate device for slot 1 of /dev/md0
mdadm: added /dev/sdc to /dev/md0 as 2
mdadm: added /dev/sdd to /dev/md0 as 3
mdadm: added /dev/sda to /dev/md0 as 4
mdadm: added /dev/sdb to /dev/md0 as 0
mdadm: /dev/md0 has been started with 4 drives (out of 5).
root@mainframe:~# mount /dev/md0
root@mainframe:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb[0] sda[5] sdd[4] sdc[2]
      7813531648 blocks super 1.2 level 5, 512k chunk, algorithm 2 [5/4] [U_UUU]
      
unused devices: <none>
root@mainframe:~# 

```

I am ecstatic beyond words, thank you guys SO much!

I'm going to microcenter here soon to buy some more storage to back it all up.  From now on I will keep my replacable HTPC media seperate from all my other valuables and at minimum backup all the stuff that's irreplacable.

---

### Post by rubylaser on 2013-02-02
Great! I'm glad you got it working again :)

---

### Post by darkod on 2013-02-03
Don't forget, you still need to add a fifth disk as soon as possible because this is only a degraded array. rubylaser can correct me, but I believe the correct command would be:
```
sudo mdadm --manage /dev/md0 --add /dev/sde
```

If you want to add a spare too, I'm not sure if the command is the same and it becomes a spare automatically, or you need to tell it that it's spare by using some additional options when doing the --add.

---

### Post by rubylaser on 2013-02-03
> **darkod said:**
> Don't forget, you still need to add a fifth disk as soon as possible because this is only a degraded array. rubylaser can correct me, but I believe the correct command would be:
```
sudo mdadm --manage /dev/md0 --add /dev/sde
```

If you want to add a spare too, I'm not sure if the command is the same and it becomes a spare automatically, or you need to tell it that it's spare by using some additional options when doing the --add.

That's the correct command.  Personally, I wouldn't add a spare, I'd just [convert this to a RAID6]("http://zackreed.me/articles/56-mdadm-raid5-to-raid6-migration") if you have an extra disk.  That will allow you to survive 2 disk failures.

---

### Post by apokkalyps on 2013-02-03
Hmmm, I did this already last night, but skipped the --manage parameter
```
root@mainframe:~# mdadm --add /dev/md0 /dev/sde
mdadm: added /dev/sde
root@mainframe:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde[6] sdb[0] sda[5] sdd[4] sdc[2]
      7813531648 blocks super 1.2 level 5, 512k chunk, algorithm 2 [5/4] [U_UUU]
      [>....................]  recovery =  0.0% (445588/1953382912) finish=584.3min speed=55698K/sec
      
unused devices: <none>

```

and then ~6 hours later
```
root@mainframe:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde[6] sdb[0] sda[5] sdd[4] sdc[2]
      7813531648 blocks super 1.2 level 5, 512k chunk, algorithm 2 [5/5] [UUUUU]
      
unused devices: <none>

```

So I notice the indicies of the array still skip slot 1.  Is that normal?  When a component fails, its number is retired like a sports jersey?:P

What was the deal with those counters being off?  If that one drive had a weak electrical connection going on and off (multiple times per second), does that explain how the other got out of sync?  I guess I'm wondering if I should expect the other drives to fail soon?

My plan is to buy enough drives to bring this up to raid6, do a full backup, and then a second backup for the 20% that is most important.  It won't be cheap but it's money I should have spent already anyway.

---

### Post by darkod on 2013-02-03
I'm not sure how the slots go because it's not that only slot 1 was skipped, slot 3 is also skipped.

---

### Post by apokkalyps on 2013-02-05
So after all that, I think I've managed to lose my files anyway.  As soon as I had it back up to RAID5 I went and spent 800 bucks on 12TB of backup plus another 2TB to replace the physically damaged drive.  Then, before doing the backup, I tried growing it to a RAID6.  I didn't know this would take ~100 hours, but I let it run until my server hung at 15% completion.  Seriously hung, like no REISUB, and the reset button didn't work.  I rebooted, of course the array won't come up.  I tried to do a mdadm --assemble --scan, and it says something about "unable to reshape, maybe you forgot to specify the backup file".  I think, oh thank god it forced me to make a backup file, and I go looking for it and it's gone.  How did I not know that ubuntu clears the /tmp/ folder at reboot??  I use c:\temp in windows a lot...  What a perfect storm of bad decisions, fate cutting me some slack, and then more bad decisions to seal the deal...

I shut the machine off.  Unless anyone knows a magic way to recover the array without the backup file, it seems like my only slim chance is to take the SSD with the os on it to data recovery people.  If they can maybe (maybe?) find the backup file on the file system (marked for deletion and not yet overwritten), then I could maybe, maybe recover the array.

Even if I had the backup file, what are the chances that my array would be recoverable?

---

### Post by darkod on 2013-02-05
Wait for rubylaser if he has some ideas.

Just for info, did you try reshaping the degraded array before having a "full" raid5 with 5 disks and synced?

Or first you added a new disk to make it a 5 disk raid5 array again, and only then tried the reshape?

---

### Post by darkod on 2013-02-05
Sorry, I just noticed above you did have the array full with all 5 members.

Did you try checking the current mdadm status with something like:
sudo mdadm --examine /dev/sd[abcde]

---

### Post by darkod on 2013-02-05
This guy had a similar problem trying to grow 4 disk raid5 to 5 disk raid6. At the end it seems --assemble --force worked.

But lets see what the examine command above shows first in your case, and wait until rubylaser confirms with his opinion.

In theory, the reshape should continue after you rebooted, if I got it right you say that it didn't.

Also, in the thread I linked now ignore most of the situation, I think the guy made en error joining a disk as spare first. You followed rubylaser tutorial for reshaping to raid6, stick to it. I think a forced assmeble might help you but lets wait for another opinion.

---

### Post by apokkalyps on 2013-02-05
I wonder if it puts the path of the backup file in metadata and then uses that to continue the reshape, but ubuntu cleared the tmp folder on reboot so it couldn't continue.  I'm only speculating.

I did not try a force assemble, I could still try that, it's what fixed me last time.  But I was betting that since it FORCED me to make the backup file, that it would be needed.  I could try it, but right now I'm keeping the machine off so that there is less chance of the lost backup file getting over written on the file system.

Maybe if I try to do a force assemble i should do it off a live ISO, if that's possible, rather than my standard OS drive (unless it HAS to be from the same OS drive that started the reshape).

---

### Post by darkod on 2013-02-05
Yeah, that was my idea with the --examine command. Boot into live mode, add the mdadm package (because it's not included), and without trying to assemble md0 or nothing, simply try reading what the superblock says on the first five disks with:
sudo mdadm --examine /dev/sd[abcde]

You might have superblock on more disks since you tried growing, but lets see the original first 5 first.

In my opinion, this should be safe because you are not mounting md0, you are not even trying to assemble it.

I don't know where the backup file is kept but the the --grow command examples I have seen, you put your own path. And I have never seen it as tmp in any example. Just put it directly in / for example.

---

### Post by apokkalyps on 2013-02-05
I stupidly, manually specified /tmp/raid-backup.bak as the path for the backup file.  Shooting myself in the foot.  I did not realize that in ubuntu, that location is actually cleared on reboot.  School of hard knocks.

I'll do the examine when I get home from work.

---

### Post by apokkalyps on 2013-02-05
/dev/sdc is the new drive I bought to replace the drive with the molex damage, and was being --grow'n onto for the raid6 reshape.

```
    sudo mdadm --examine /dev/sd[abcdef]
    /dev/sda:
              Magic : a92b4efc
            Version : 1.2
        Feature Map : 0x4
         Array UUID : 8bc78af0:d9a981e3:73549f21:2f76cd24
               Name : mainframe:vault
      Creation Time : Thu Aug 16 02:57:14 2012
         Raid Level : raid6
       Raid Devices : 6
     
     Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
         Array Size : 7813531648 (7451.56 GiB 8001.06 GB)
      Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
        Data Offset : 262144 sectors
       Super Offset : 8 sectors
              State : clean
        Device UUID : f18da9cc:27f5eee4:61ba900e:dd6ca8b9
     
      Reshape pos'n : 1181333504 (1126.61 GiB 1209.69 GB)
         New Layout : left-symmetric
     
        Update Time : Tue Feb  5 03:05:43 2013
           Checksum : 7ac690a9 - correct
             Events : 295638
     
             Layout : left-symmetric-6
         Chunk Size : 512K
     
       Device Role : Active device 4
       Array State : AAAAAA ('A' == active, '.' == missing)
     
     
    /dev/sdb:
              Magic : a92b4efc
            Version : 1.2
        Feature Map : 0x4
         Array UUID : 8bc78af0:d9a981e3:73549f21:2f76cd24
               Name : mainframe:vault
      Creation Time : Thu Aug 16 02:57:14 2012
         Raid Level : raid6
       Raid Devices : 6
     
     Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
         Array Size : 7813531648 (7451.56 GiB 8001.06 GB)
      Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
        Data Offset : 262144 sectors
       Super Offset : 8 sectors
              State : clean
        Device UUID : 004a89c7:bd03e0fe:b6ea3ab9:76e5e5e0
     
      Reshape pos'n : 1181333504 (1126.61 GiB 1209.69 GB)
         New Layout : left-symmetric
     
        Update Time : Tue Feb  5 03:05:43 2013
           Checksum : 617f0438 - correct
             Events : 295638
     
             Layout : left-symmetric-6
         Chunk Size : 512K
     
       Device Role : Active device 0
       Array State : AAAAAA ('A' == active, '.' == missing)
     
     
    /dev/sdc:
              Magic : a92b4efc
            Version : 1.2
        Feature Map : 0x6
         Array UUID : 8bc78af0:d9a981e3:73549f21:2f76cd24
               Name : mainframe:vault
      Creation Time : Thu Aug 16 02:57:14 2012
         Raid Level : raid6
       Raid Devices : 6
     
     Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
         Array Size : 7813531648 (7451.56 GiB 8001.06 GB)
      Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
        Data Offset : 262144 sectors
       Super Offset : 8 sectors
    Recovery Offset : 590666752 sectors
              State : clean
        Device UUID : 0d8ddf14:2601f343:0b7e182f:cc8358e9
     
      Reshape pos'n : 1181333504 (1126.61 GiB 1209.69 GB)
         New Layout : left-symmetric
     
        Update Time : Tue Feb  5 03:05:43 2013
           Checksum : 956d5260 - correct
             Events : 295638
     
             Layout : left-symmetric-6
         Chunk Size : 512K
     
       Device Role : Active device 5
       Array State : AAAAAA ('A' == active, '.' == missing)
     
     
    /dev/sdd:
              Magic : a92b4efc
            Version : 1.2
        Feature Map : 0x4
         Array UUID : 8bc78af0:d9a981e3:73549f21:2f76cd24
               Name : mainframe:vault
      Creation Time : Thu Aug 16 02:57:14 2012
         Raid Level : raid6
       Raid Devices : 6
     
     Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
         Array Size : 7813531648 (7451.56 GiB 8001.06 GB)
      Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
        Data Offset : 262144 sectors
       Super Offset : 8 sectors
              State : clean
        Device UUID : a6ad29b7:35b546ae:4bc2a5af:e6bc8252
     
      Reshape pos'n : 1181333504 (1126.61 GiB 1209.69 GB)
         New Layout : left-symmetric
     
        Update Time : Tue Feb  5 03:05:43 2013
           Checksum : 688dc85c - correct
             Events : 295638
     
             Layout : left-symmetric-6
         Chunk Size : 512K
     
       Device Role : Active device 2
       Array State : AAAAAA ('A' == active, '.' == missing)
     
     
    /dev/sde:
              Magic : a92b4efc
            Version : 1.2
        Feature Map : 0x4
         Array UUID : 8bc78af0:d9a981e3:73549f21:2f76cd24
               Name : mainframe:vault
      Creation Time : Thu Aug 16 02:57:14 2012
         Raid Level : raid6
       Raid Devices : 6
     
     Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
         Array Size : 7813531648 (7451.56 GiB 8001.06 GB)
      Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
        Data Offset : 262144 sectors
       Super Offset : 8 sectors
              State : clean
        Device UUID : 1df1fd17:592f431a:f3f05592:fbfccdcd
     
      Reshape pos'n : 1181333504 (1126.61 GiB 1209.69 GB)
         New Layout : left-symmetric
     
        Update Time : Tue Feb  5 03:05:43 2013
           Checksum : 9359f4b5 - correct
             Events : 295638
     
             Layout : left-symmetric-6
         Chunk Size : 512K
     
       Device Role : Active device 3
       Array State : AAAAAA ('A' == active, '.' == missing)
     
     
    /dev/sdf:
              Magic : a92b4efc
            Version : 1.2
        Feature Map : 0x4
         Array UUID : 8bc78af0:d9a981e3:73549f21:2f76cd24
               Name : mainframe:vault
      Creation Time : Thu Aug 16 02:57:14 2012
         Raid Level : raid6
       Raid Devices : 6
     
     Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
         Array Size : 7813531648 (7451.56 GiB 8001.06 GB)
      Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
        Data Offset : 262144 sectors
       Super Offset : 8 sectors
              State : clean
        Device UUID : 15dcad1e:3808a229:7409b3aa:4e03ae1b
     
      Reshape pos'n : 1181333504 (1126.61 GiB 1209.69 GB)
         New Layout : left-symmetric
     
        Update Time : Tue Feb  5 03:05:43 2013
           Checksum : fa5d762 - correct
             Events : 295638
     
             Layout : left-symmetric-6
         Chunk Size : 512K
     
       Device Role : Active device 1
       Array State : AAAAAA ('A' == active, '.' == missing)

```

Is it safe to try a mdadm --assemble --force?

---

### Post by darkod on 2013-02-06
I would say yes. The superblock already says it's raid6, all members are present and the event counters are the same on all disks.

If you want, wait for confirmation from rubylaser, I'll PM him now and depending on time zone and free time, he might pop in.

---

### Post by rubylaser on 2013-02-06
I would do a force assemble at this point.  It appears that the metadata has been updated, so this should work.

---

### Post by apokkalyps on 2013-02-06
Can I do the force assemble on a live ISO?

---

### Post by SaturnusDJ on 2013-02-06
Yes.

---

### Post by apokkalyps on 2013-02-06
No dice.

```
ubuntu@ubuntu:~$ sudo mdadm --assemble --force --run --verbose /dev/md0 /dev/sd[abcdef]
mdadm: looking for devices for /dev/md0
mdadm: /dev/sda is identified as a member of /dev/md0, slot 4.
mdadm: /dev/sdb is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdc is identified as a member of /dev/md0, slot 5.
mdadm: /dev/sdd is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sde is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdf is identified as a member of /dev/md0, slot 1.
mdadm:/dev/md0 has an active reshape - checking if critical section needs to be restored
mdadm: Failed to find backup of critical section
mdadm: Failed to restore critical section for reshape, sorry.
      Possibly you needed to specify the --backup-file
```

So I talked to a data recovery company.  To retrieve the backup file from my SSD, they charge $100 to even look at the drive and then $500-$700 if they can restore the file.  
Hypothetically, if the file is restored perfectly, what are the chances of the assemble succeeding with it?  90%?  50?  30?

---

### Post by SaturnusDJ on 2013-02-07
Personally I don't believe in recovery, at least after my experiences.

But of course you want to do all you can to get the backup-file back. Note that the more you use the drive the /tmp is at, the more chance the file will be overwritten by something else.

[http://askubuntu.com/questions/217606/undelete-files-on-ext4](http://askubuntu.com/questions/217606/undelete-files-on-ext4)

---

### Post by darkod on 2013-02-07
Are you sure the /tmp is overwritten? Is it on the same array? If you have / on the same array, then /tmp is not accessible until the array is assembled, which is a catch 22.

It seems it's best to have the backup file on another disk, but only if you have one.

I'm not sure what's best to do right now. If they can get the backup file back, the reshape might be able to continue. But on the other hand, it depends whether they will get the file 100% back and whether they will destroy any other data/settings on the disk while doing it.

Having the backup file back helps nothing if they mess up the stopped reshape. You want the backup file for reshape continuation.

---

### Post by apokkalyps on 2013-02-07
I keep my OS and / mounted on a separate drive besides the array.  So the filesystem /tmp was on, does not need to be assembled, just scoured for deleted data.  After the initial crash/reboot I tried a few mdadm commands, attempted an assemble, ls'ed the /tmp folder, and then shut the machine down immediately and unplugged the OS drive.  So I've done my best to increase the chances of recovery from the instant I knew the file was missing.

Yeah, apparently ubuntu clears the /tmp folder each time you reboot by default.  This was news to me.  Bad bad news.

[http://ubuntu-tutorials.com/2008/01/19/changing-the-tmp-cleanup-frequency/](http://ubuntu-tutorials.com/2008/01/19/changing-the-tmp-cleanup-frequency/)

---

### Post by SaturnusDJ on 2013-02-07
I would try the ext4 undelete from the link I gave you, read into it yourself some more. If you fail I think the recovery company will fail also.

---

### Post by apokkalyps on 2013-04-21
This epic saga continues.  First, thanks everyone that helped me in this thread, I would have been useless without all these hints.  Now I have recovered most of the more important part of my data, but would like some advice on if I can recover any more.

I was able to get the backup file recovered and re-assembled the array with the --invalid-backup param in case parts of it had been corrupted.  I was able to get my array back up and running for a while.  First I took one external drive and copied of the smallest and most immediatly important stuff.  At this point I had what was originally a synced raid5, which was growing/reshaping to a raid6 onto a new drive.  As it was happeneing atleast one of the drives was still making the beeping noises periodically and I knew it was a matter of time before it went out.  Eventually /dev/sdd totally failed and got marked F on /proc/mdstat.  The array was still operational, still showed 4 of 6 components active, where the fifth still being resynced.  After getting the most important smallest stuff copied to one location, I started doing an rsync -avH of the entire array contents to another array.  This was going while it was reshaping, since I didn't have faith the array would live long enough for the 5 day reshape to complete, which would have gotten me up to 5/6 components of the raid 6, at which point I would have added another drive for 6/6.  The reason I didn't immediatly add the extra drive is because I really felt this array and its drives were a timebomb and I was more immediatly interested in copying the data off than trying to get the full raid 6 running (again if it was going to take 10 days and I expected another drive to fail within a few).  

Anyway, quite a bit of my data got rsynced off, this morning I woke up to find out another drive (/dev/sda) in the array had failed as I expected.  I am really confused about what kind of state it is in, and I am hoping for some advice about what is going on and if it's finally time to give up and take my baby off lifesupport.

First:
```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid6 sdb[0] sdc[7] sda[5](F) sde[4] sdd[2](F) sdf[6]
      7813531648 blocks super 1.2 level 6, 512k chunk, algorithm 18 [6/3] [UU_U__]
      
unused devices: <none>

```

So judging from the above, I would expect the array to be totally offline/broken.  3 out of 6 drives in a raid6?  But my array is still "active" and I still have it mounted, can still see the folder structure and many files, just the certain folders give I/O errors when you try to ls them.  How is this possible?  Why do I have some files but not the others?  Is it wrong to expect all or nothing of a filesystem on md0 (ext4)?  

My theory: The array had been 40% through the reshape onto the new drive (even with 4/5 of the 'old' components), then 1 more of the old components died, so I am at 3/5 of the old components PLUS a new drive with 40% of the stripes, so right now in essence I have 40% of the 4th drive needed for minimum raid6 operation, and thus can see 40% of the files.  I don't know if mdadm is capable of that kind of magic, but I can't otherwise explain how my array is even assembled right now.  Can anyone tell me if this is indeed possible/accurate?  If it is something like this, why doen't mdstat atleast say something other than "active" like "degraded" etc?

The real question.  Right now Disk Utility says /dev/sda is "green" but with 1 bad sector (I don't really know what this means except it's bad).  What I'm asking is what everyone is always asking in these threads, is there any way I can bring my array back to full functionality?

```
sudo mdadm --examine /dev/sd[a-f]
/dev/sda:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4
     Array UUID : 8bc78af0:d9a981e3:73549f21:2f76cd24
           Name : mainframe:vault  (local to host mainframe)
  Creation Time : Wed Aug 15 21:57:14 2012
     Raid Level : raid6
   Raid Devices : 6

 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 7813531648 (7451.56 GiB 8001.06 GB)
  Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : f18da9cc:27f5eee4:61ba900e:dd6ca8b9

  Reshape pos'n : 3277520896 (3125.69 GiB 3356.18 GB)
     New Layout : left-symmetric

    Update Time : Sun Apr 21 06:27:31 2013
       Checksum : 75147b14 - correct
         Events : 755496

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 4
   Array State : AA.AAA ('A' == active, '.' == missing)
/dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4
     Array UUID : 8bc78af0:d9a981e3:73549f21:2f76cd24
           Name : mainframe:vault  (local to host mainframe)
  Creation Time : Wed Aug 15 21:57:14 2012
     Raid Level : raid6
   Raid Devices : 6

 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 7813531648 (7451.56 GiB 8001.06 GB)
  Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 004a89c7:bd03e0fe:b6ea3ab9:76e5e5e0

  Reshape pos'n : 3277520896 (3125.69 GiB 3356.18 GB)
     New Layout : left-symmetric

    Update Time : Sun Apr 21 13:41:12 2013
       Checksum : 5bc7638b - correct
         Events : 759402

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AA.A.A ('A' == active, '.' == missing)
/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x6
     Array UUID : 8bc78af0:d9a981e3:73549f21:2f76cd24
           Name : mainframe:vault  (local to host mainframe)
  Creation Time : Wed Aug 15 21:57:14 2012
     Raid Level : raid6
   Raid Devices : 6

 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 7813531648 (7451.56 GiB 8001.06 GB)
  Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
Recovery Offset : 1638760448 sectors
          State : clean
    Device UUID : 0d8ddf14:2601f343:0b7e182f:cc8358e9

  Reshape pos'n : 3277520896 (3125.69 GiB 3356.18 GB)
     New Layout : left-symmetric

    Update Time : Sun Apr 21 13:41:12 2013
       Checksum : ce2e55b3 - correct
         Events : 759402

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 5
   Array State : AA.A.A ('A' == active, '.' == missing)
/dev/sde:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4
     Array UUID : 8bc78af0:d9a981e3:73549f21:2f76cd24
           Name : mainframe:vault  (local to host mainframe)
  Creation Time : Wed Aug 15 21:57:14 2012
     Raid Level : raid6
   Raid Devices : 6

 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 7813531648 (7451.56 GiB 8001.06 GB)
  Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 1df1fd17:592f431a:f3f05592:fbfccdcd

  Reshape pos'n : 3277520896 (3125.69 GiB 3356.18 GB)
     New Layout : left-symmetric

    Update Time : Sun Apr 21 13:41:12 2013
       Checksum : 8da25408 - correct
         Events : 759402

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AA.A.A ('A' == active, '.' == missing)
/dev/sdf:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x4
     Array UUID : 8bc78af0:d9a981e3:73549f21:2f76cd24
           Name : mainframe:vault  (local to host mainframe)
  Creation Time : Wed Aug 15 21:57:14 2012
     Raid Level : raid6
   Raid Devices : 6

 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 7813531648 (7451.56 GiB 8001.06 GB)
  Used Dev Size : 3906765824 (1862.89 GiB 2000.26 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 15dcad1e:3808a229:7409b3aa:4e03ae1b

  Reshape pos'n : 3277520896 (3125.69 GiB 3356.18 GB)
     New Layout : left-symmetric

    Update Time : Sun Apr 21 13:41:12 2013
       Checksum : 9ee36b5 - correct
         Events : 759402

         Layout : left-symmetric-6
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AA.A.A ('A' == active, '.' == missing)

```

---

