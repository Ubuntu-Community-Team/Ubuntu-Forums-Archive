---
title: "mdadm grow (user) error... now what ? help plz"
date: 2011-10-15
forum: Server Platforms
---

### Post by zosky on 2011-10-15
hi yall

we had a raid5 w/ 4x1TB, then we added 2 more & 2 more... until we reached 10. for the current upgrade, i added 4 more and switched it to raid6

each time, i've used [these steps]("http://www.jamierf.co.uk/2009/11/04/software-raid-5-using-mdadm-in-ubuntu-9-10/") to create 1 linux raid auto partition per drive. then i added them and grew the array.  

this time around i'm afraid i've hosed the array ??? ... i added the devices (/dev/sda) not the partitions (/dev/sda**1**)

cat /proc/mdstat shows it rebuilding, but i have no idea what to expect when it finishes ??? 

what should i do ? doing anything while its level-changing/reshape doesn't seem smart. 

i **think** once it is done, i need to fail 2 of the new drives, rePartition and reAdd them, reshape.. then repeat with the other 2 new drives (all before the next reboot) ???

help plz

---

### Post by stn21 on 2011-10-15
I don't think you have a problem.

I have build mdadm-raids with devices before. They work the same as with partitions.

Have you mounted your array? Can you read+write files? If you can then everything should be ok

---

### Post by zosky on 2011-10-15
the array is live and 97% full. (we should have added drives months ago). r+w is constant because it is my seed box and home media server. it is mounted w/NFS in 3 places & my bro has it mapped w/SAMBA. all systems seem normal captain 

it was reShaping at 1.5mb/s. i managed to double the speed (3mb/s) [with this]("http://www.cyberciti.biz/tips/linux-raid-increase-resync-rebuild-speed.html") ... this is realllly slow, right ? i think it is the best i'll get from my setup: 3(4sata-port)pci-cards & a mix of green/blue drives. can i add a bitmap (while it is reshping?) and are there other speed hacks ?

i have a line in crontab @hourly "cat /proc/mdstat | mail -s "mdSTAT" <myCell#>@<myCarrier>" ... just because incomming email/txts are free ;) ... 56% w/1d12h left ... yeeha

fyi:
```
zosky@homeNAS:~$ sudo mdadm --detail /dev/md0
[sudo] password for zosky: 
/dev/md0:
        Version : 0.91
  Creation Time : Mon Mar 15 23:51:02 2010
     Raid Level : raid6
     Array Size : 8790839424 (8383.60 GiB 9001.82 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 14
  Total Devices : 14
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Oct 15 02:46:09 2011
          State : clean, degraded, recovering
 Active Devices : 13
Working Devices : 14
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric-6
     Chunk Size : 64K

 Reshape Status : 57% complete
  Delta Devices : 3, (11->14)
     New Layout : left-symmetric

           UUID : e53abd15:b99fe199:ef1a8e61:6a3100d1
         Events : 0.5890322

    Number   Major   Minor   RaidDevice State
       0       8      113        0      active sync   /dev/sdh1
       1       8      129        1      active sync   /dev/sdi1
       2       8      161        2      active sync   /dev/sdk1
       3       8      145        3      active sync   /dev/sdj1
       4       8      177        4      active sync   /dev/sdl1
       5       8      193        5      active sync   /dev/sdm1
       6       8      209        6      active sync   /dev/sdn1
       7       8      225        7      active sync   /dev/sdo1
       8       8       17        8      active sync   /dev/sdb1
       9       8        1        9      active sync   /dev/sda1
      10       8       96       10      spare rebuilding   /dev/sdg
      11       8       80       11      active sync   /dev/sdf
      12       8       48       12      active sync   /dev/sdd
      13       8       32       13      active sync   /dev/sdc
zosky@homeNAS:~$ 

```

---

### Post by rubylaser on 2011-10-15
You cannot add a bitmap while it is reshaping.  You can try to run [this script]("http://ubuntuforums.org/showpost.php?p=9368732&postcount=1").  It should improve your speeds, but the main problem is your PCI SATA cards.  I'd pickup an IBM [m1015 card]("http://www.ebay.com/itm/IBM-ServeRAID-M1015-SAS-RAID-FRU-46M0861-w-Bracket-/160665622119?pt=COMP_EN_Networking_Components&hash=item25686ad667#ht_1441wt_1084") from ebay if you have an open PCI-Express slot or PCIe x8.  Then flash it with the [LSI IT firmware]("http://lime-technology.com/forum/index.php?topic=12767.msg124393#msg124393")  These work great and will allow your disks to work at maximum speed.

---

### Post by zosky on 2011-10-18
it is done reshaping (14x1TB/raid6). when i ssh & cp something, speedometer shows ~40mb/s ... is this an adquite test for max-speed of the array ? if so, this means the bottleneck is our mBit LAN. and, the bottleneck while reshaping was the software speed ? (athlon 3000)

i can see why something like the IBM card would be useful in the right situation, but it seems like overkill for our modest (home-fileServer) needs. at 50$/per the PCI SATA card let us start a NAS at a relativity low cost (with 90% of the $$ going to HDDs). we are using an 8yr old grey box (a friend was ready to toss). over time i added 3 more cards and there is still room for 2more. parts get cheaper as time marches. 

if we get to the point where we need 3+ simultaneous HD mkv streams in the house, i think the best upgrade will be gBit LAN... if we end up needing more then 8 then a (proper) pciE card would be the next step.

thanks for all the suggestions. 
and the support in my moment of need/doubt

UPDATE: i did some more reading and i understand (a little more) now ...each drive in my array is 1TB. if i add 1.5 TB drives, 1/2T would be wasted, unless partioned and used separately ?

along this same line, if i start adding 2TB drives (replacing the 1TBs) ... will it (eventually) realize the smallest disk is 2TB ? 

lastly, is it correct (on wikipedia) that ext4 w/ 4 KB blocks, can do 2 TB/file and 16TB/partition... if so 8K may need to be part of the next upgrade

---

### Post by rubylaser on 2011-10-18
I used an Athlon 3000+ for years in my 11 (1TB) disk RAID6 mdadm array and could easily saturate a gigabit connection (115+ MB/s).  So, I don't think your processor is the bottleneck.  If you don't tune the array at all, around 40-50 MB/s with your hardware sounds about right.

I bought my IBM cards for $55 and $60 respectively from ebay, so the price isn't really much different than what you paid.  But the PCI bus on your cards is really the limiting factor on your disk's throughput (this is where your bottleneck is).

mdadm like hardware RAID5 will base it's size off your smallest disk, so if you added a 1.5, 2, or 3TB drive, it would end up being used as 1TB unless you added multiple partitions. **DON'T** do this! If you add two partitions a 2TB disks or 3 to a 3TB disk and then add each of those partitions to the array, a hardware failure could at the minimum remove all parity and at worst could result in a complete failure in the case of a 3TB disk. Disks are cheap, just add another.

ext4 is limited to 16TB because of the lack of a stable e2fsprogs to support growing the filesystem, and fscking it.  If you need > 16TB, ext4 is currently not an option, unless you want to run a second filesystem and append them together with mhddfs or greyhole.

---

