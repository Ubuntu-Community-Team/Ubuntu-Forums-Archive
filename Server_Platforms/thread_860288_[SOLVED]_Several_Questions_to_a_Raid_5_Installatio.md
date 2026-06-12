---
title: "[SOLVED] Several Questions to a Raid 5 Installation"
date: 2008-07-15
forum: Server Platforms
---

### Post by gaspedalo on 2008-07-15
Hi,

I've got a File-Server with Ubuntu Desktop 6.10 running for the last 2 1/2 years now and because of some IT changes we decided to renew that guy and pass him the 8.04.1 Server edition. 
We had a sata software raid 10 running and the os booted from an ide harddrive. This time i'd like to make this more economical and use just 3 of them discs. 3 discs for a raid5 array that holds data AND os.
Unfortunately the server documentation lacks the whole raid thing. I know that building a raid with mdadm is a piece of cake but building a raid that holds the os might be ?possible/impossible?

- This guy is doing it right in installing ubuntu on raid 1 and it doesn't seem to be a big deal
[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)
It looks like that he could have chosen raid5 (picture 7) and everything else would have worked out the same way. What do you think? (another howto for raid1 at hardy installation: [http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1))

- Do I have to use the alternate version, to get the raid option at the installation point (server version might have the same options, but it's no where mentioned).

- Do you think it's reasonable to have all on one raid or would you prefer to seperate mass-data from the system (like one os-drive and three raid-data-drives)?
We have a beautiful nas in here (synology) that has impressive performance and that puts everything on one big raid5 (at least that#s what it looks like)

- Is there an easy way to expand from a raid1 to a raid5, or even from noraid to raid5. That would be an option, but I fear that it's even more complicated.

looking forward to your insight,
daniel

---

### Post by robgolding63 on 2008-07-15
If I were you I would definitely keep the O/S on one single drive, and RAID the others for data. Keep as little on the O/S as you can - so reinstallation is quick and easy if the O/S drive goes south.

There is a bug in Ubuntu whereby it will not boot from a RAID1 array if a drive has died, and installation on a RAID array just adds another layer of complication (in my opinion anyway).

If you have 4 other disks (you have RAID10 atm), then maybe RAID5 them - to get a bit more space, but dont include the IDE drive in that, save it for the O/S itself.

Hope this helps :)

Rob

---

### Post by windependence on 2008-07-16
IMHO, skip this all together, buy a hardware controller and a spare (you can get them for under $100) and use REAL RAID. In that case you <could> put all your stuff on one array but I still like a small drive for the OS, RAID 5 for the data and apps, and another drive for backups if you can do it.

-Tim

---

### Post by isrich on 2008-07-18
> - Do I have to use the alternate version, to get the raid option at the installation point (server version might have the same options, but it's no where mentioned).

As I know the answer is Yes you've to use alternate version.

> - Do you think it's reasonable to have all on one raid or would you prefer to seperate mass-data from the system (like one os-drive and three raid-data-drives)?

I preferred to have my OSes on mirror raid and all my data in raid5 or 6. :)
I'd hear someone around linux communities said "OS come and go but data forever".

> - Is there an easy way to expand from a raid1 to a raid5, or even from noraid to raid5. That would be an option, but I fear that it's even more complicated.


There is no easy way man. :cry:

I use 3 80GB disks for my 8.04 workstation.
all of it was set to active and partition into 2 part, one small part for /boot set to mirror and other one set to raid 5 for / and /home which lvm sit on top of raid.

---

### Post by gaspedalo on 2008-07-21
Clearification:

- With manual partition setup it's simply to have ubuntu-server edition installed to software-raids. No Alternate Version is needed.

- Ubuntu is not able to boot on a raid5 partition

-Ubuntu will boot on raid1 (mirrored) partition right after installation.

So here is what I did. I have 3 drives (300gb sata). I chose manual configuration a t setup and had all three drives partitioned the same way (1GB primary, prepared for raid, bootable; 290 GB primary, prepared for raid; 8GB primary, prepared for raid). Then I chose to make MDs and I had 
1. md0 as raid1 with the three bootable partitions, ext3, mountable at /boot; 
2. md1 as raid5 for the data, ext3, mountable at /
3. md2 as raid5 for swapspace

Then installation continued, reboot, automatically resyncing, done!
104mb/sec. read performance

Just one thing to be sure: alway check that md0 is mounted when you are doing kernel update or if your are updating grub. 

I've not been testing the exchanging of discs yet. But it should work easily with a system disc like this guy mentions here: [http://ubuntuforums.org/showthread.php?t=852650]("http://ubuntuforums.org/showthread.php?t=852650")

---

### Post by windependence on 2008-07-21
You either made a typo or you didn't configure this way because you need at least three drives for RAID 5 and you only have 2 RAID 5 drives listed.

Also, for RAID 1 you would need at least another drive since this is mirrored. Your setup doesn't make sense. RAID should not be used unless you need it and never in place of good backups. Sometimes I think people do this because it's "cool". Modern drives are very fast (SATAII 300mb/s). If you want balls to the wall speed, use RAID 0 and back your stuff up.

-Tim

---

### Post by gaspedalo on 2008-07-25
again, simple form:
3 drives
each with 3 equal partitions
three first partitions connected to raid1 mounted at /boot
three second partitions connected to raid5 mounted at /
three third partitions connected to raid five mounted as swap

read performance 104 MB/sec (equals more or less 800 Mb/sec)

In the case you need data performance it's not just plane fun to do raid. And if one disc crashes and the spare disc comes in, it's good NOT to have to rely only on your backups.

---

### Post by fjgaude on 2008-07-26
> **gaspedalo said:**
> again, simple form:
3 drives
each with 3 equal partitions
three first partitions connected to raid1 mounted at /boot
three second partitions connected to raid5 mounted at /
three third partitions connected to raid five mounted as swap

read performance 104 MB/sec (equals more or less 800 Mb/sec)

In the case you need data performance it's not just plane fun to do raid. And if one disc crashes and the spare disc comes in, it's good NOT to have to rely only on your backups.

Sounds good... that thru-put reads like you are running disk controllers off a PCI bus, not PCI-E or -X... with the right, modern drives you can go to 200MB/sec and all the way up to over 400. <smile>

---

### Post by djamu on 2008-07-27
If I may add.

I usually configure similar setups. but with the small difference that I partition my array instead creating arrays on partitioned disks !. This has several advantages ( read on ). I also keep my system partition seperate from my data.



[B]Redundancy Case description:
setup described in previous post ( arrays on partitions ) :
[/B]
1 drive of your array fails, person who installed it is on vacation... > problem > new drive needs to be partitioned EXACTLY the same as current drives.......


So there goes part of your redundancy, as not all data is redundant > the partitiontable is not...


Partitioning arrays itself will solve that, as the partition table will become part of the array. ( not a minor difference I'd say, seems all those tutorials fail to mention this )


So how to do this.
The main problem here is then that a system cannot boot from anything else then a normal partition and a raid1 ( in case of the raid1 the system doesn't initially know it's a raid because all data on the mirrors is equal )

Either you sacrifice a bit on boot redundancy and use a small 150MB partition on each disk as raid1 mounted /boot that just holds your grub & initramfs. or you just use a ( 2 mirrored :)  ) cheap 128/256MB USB sticks to bootstrap your system directly into a single partitioned array. ( just don't run your system from USB sticks as they cannot handle that many rewrites ).


So your disk layout would then be.

2x 256MB USB disks as raid1 mounted as /boot

3x unpartitioned disks raid5 assembled as  /dev/md0

>>  3 partitions on /dev/md0 

/dev/md0p1 as /
/dev/md0p2 as /data
/dev/md0p3 as swap

**use CFDISK on an empty array ! as partitioning the array will destroy your data**> ```
sudo cfdisk /dev/md0
``` 


Most people don't realize that an MD device is unpartitioned ( **/dev/md0 is not the 1st partition of /dev/md** ), but is treated by the system as a large superfloppy / USB disk, both usually also unpartitioned.


By doing it like this you don't have to worry about disk layout in case of disk failure... enjoying full complete redundancy, with minimal fuzz on failure....


A note on formatting USB disks. These come usually preformatted as either FAT / FAT32, a normal grub install won't work on them, use GRUB4DOS > 
[[COLOR="Navy"]Wiki & download[/COLOR]]("https://gna.org/projects/grub4dos/")
[[COLOR="Navy"]Project page[/COLOR]]("https://sourceforge.net/projects/grub4dos")

or easier just reformat them to ext3 & you'll be set...

**Don't forget to set the bootflag on the USB devices** > also use CFDISK for that, ( changing bootflag doesn't harm any data on the device )




cheers

:lolflag:

---

### Post by Ceephis on 2008-08-15
wanted to share that your partition idea using USB drives and a raid 5 is pure genius I love it.

Here is what I set up 

2 128 meg usb (raid 1) set as /boot
3 40 gig hard drives
5 meg swap
15 meg /root
25 meg /home
After the raid these numbers are double 
I set up the raid using the text driven installer of ubuntu.

I created 4 separate raid disks

1 Usb 
2 hard drive /swap
3 hard drive /home
4 hard drive /root

After setting this up it did not boot it was giving an error in grub. (12 I believe)

Any idea on how to fix this?

By the way how do you rebuild a disk when one goes bad?

Thanks for your time

Peter

p.s. 

What is CFDISK used for? Maby that is why I cant boot? I did not do this step yet.

use CFDISK on an empty array !>

---

### Post by windependence on 2008-08-15
Great post djamu! I forgot all about the problem with partitions on the RAID device as most of the time I use hardware RAID5 on all my stuff and create one logical volume. Then I use LVM on top of that for flexiblilty. I am really gald you brought this out because it would be a real PITHA to recover from.

-Tim

---

### Post by djamu on 2008-08-15
> **Ceephis said:**
> wanted to share that your partition idea using USB drives and a raid 5 is pure genius I love it.


lolz

> 
.......snipsnip....

After setting this up it did not boot it was giving an error in grub. (12 I believe)

Any idea on how to fix this?

By the way how do you rebuild a disk when one goes bad?

Thanks for your time

Peter

p.s. 

use CFDISK on an empty array !>

K Peter I edited my previous post a little, seems it was not specific enough.

> What is CFDISK used for? Maby that is why I cant boot? I did not do this step yet.

CFDISK is a partitioning tool like fdisk ( but easier to work with, it's standard available ), you can use it to partition and make bootable devices ( which you probably forgot, I edited this in my post )..

Partitioning devices usually kills the FS -file system- on there ( if any formatted ) .. that's why I stated it ...

Mind that I don't partition the disks prior to creating the array but the way around>
**NOT** partitioning disks and then creating arrays 
**But** create 1 large array that you partition afterward... (using CFDISK)

Here's another thread from me on preparing bootable USB devices [http://ubuntuforums.org/showthread.php?p=5496792#post5496792](http://ubuntuforums.org/showthread.php?p=5496792#post5496792)

**rebuilding / repairing RAID's**
If you're new to Raid be sure to check out some other threads from me ... BEFORE you begin, just to make sure NEVER EVER to do an erase superblocks + rebuild with all disks > use the missing statement in the mdadm command, then mount the array to check if it got assembled correctly if it does add the missing disk.. this way your data will allways be intact ( for RAID6 use 2 missing disks )..

anything else ? 

:popcorn:

---

### Post by djamu on 2008-08-15
> **windependence said:**
> Great post djamu! I forgot all about the problem with partitions on the RAID device as most of the time I use hardware RAID5 on all my stuff and create one logical volume. Then I use LVM on top of that for flexiblilty. I am really gald you brought this out because it would be a real PITHA to recover from.

-Tim

Thanks...
Yeah I know, even when I write it here, the ( not so minor difference ) is easily overlooked, not a single howto on the internet mentions this. For most users LVM or EVMS ( I prefer the latter ) is overkill, so just partitioning the array will suffice...

Guess you're on of those guys who really understand what I'm talking about.. be sure to check out my other threads in regard to RAID..

cool profile picture you have there :)

cheers.

---

### Post by windependence on 2008-08-15
Can you tell me abit about EVMS? Why you like it over LVM? I never heard of it I am embarrassed to say.

-Tim

---

### Post by djamu on 2008-08-15
> **windependence said:**
> Can you tell me abit about EVMS? Why you like it over LVM? I never heard of it I am embarrassed to say.

-Tim

K,
Well EVMS is actually a more advanced version of LVM. 
( sorry folks, this is going to be abracadabra )
I'm quite sure you're aware of the limitations in regard to RAID (0/1/5/6), I'm not talking about the supposedly slow performance that some claim, and is ( on linux ) complete nonsense. 
A 5 disk RAID5 almost performs equally to a 4 disk RAID0, as both are striped ( raid 5 just adds redundancy and uses a simple XOR operation ).

So performance on **single file I/O**will go up with every disk added to the array ( limited by your onboard I/O capabilities ).

And here comes the much overlooked bottleneck. While peak throughput goes up with any added disk to a striped array **Head seek doesn't** because all heads on the disk need to work synchronously.
So while linear writing across adjacent sectors expresses itself in nanosec , disk head seeking is in msec. ( quite slow ).

Especially on busy mailservers ( any server that handles lots of small files ), this will become a bottleneck.
This problem doesn't exist on spanned arrays because each disk can work independent, so while absolute throughput doesn't go up with each disk added, concurrent I/O will go up when different files are written on different devices belonging to the same volume. ( remember disks don't work synchronously anymore ).

Unfortunately this kind of setup doesn't have redundancy, and is mostly solved by mirroring spanned arrays.
**sidenote:** an LVM created with physical devices creates a spanned array for those who like to know, but an LVM created on a RAID(0/5/6) is still a striped array.

So the limitation of an LVM is that it can only divide RAID horizontally.
And here comes the main advantage of EVMS, because it can both do horizontal and vertical array separation.

So with EVMS you can effectively let your RAID5/6 volume behave as either spanned / striped / both , by letting your physical disks work independently -vertical separation- ... ( both meaning > 5 disk raid5 > performing as raid10 )


Tried to be as briefly as possible ... hope it helps someone.
Ooh and correct me if I'm wrong, but one cannot boot from an EVMS volume ( standard ubuntu kernel has no build-in support, only modules > just roll your own kernel if needed )

( there's a little GUI in gnome for EVMS, forgot the name because I'm a CLI freak )


:lolflag:

---

### Post by windependence on 2008-08-15
Well I don't do GUI either, I'm a *BSD freak.

Thanks for the insight AND the confirmation. I get beat up here all the time for my views on RAID. I was always sure RAID 5 performed much better than single disks and almost as good as RAID 0.

I'm not a big fan of software RAID though. I prefer a good hardware (not emulated) controller. What are your thoughts on that?

-Tim

---

### Post by djamu on 2008-08-15
> **windependence said:**
> Well I don't do GUI either, I'm a *BSD freak.

Thanks for the insight AND the confirmation. I get beat up here all the time for my views on RAID. I was always sure RAID 5 performed much better than single disks and almost as good as RAID 0.

I'm not a big fan of software RAID though. I prefer a good hardware (not emulated) controller. What are your thoughts on that?

-Tim

Well since RAID(0/5/6) are all stripe flavors, throughput will go up in ALL cases, exception anything lower then Pentium 2 or when using Mickeysoft -ever tried raid5 on windoz ? it's a joke, first time I tried was the last time > AMD-XP 2Ghz > 800kBs 4disk raid5 :guitar: -

But seriously, anybody who claims that RAID is slower or equally fast then single disk on nix / bsd doesn't know sh*t ... plain & simple.

> I'm not a big fan of software RAID though. I prefer a good hardware (not emulated) controller. What are your thoughts on that?

Well that's an easy answer, you're wrong .... let me elaborate...



**case > RAID hardware controller:**

Your precious ( expensive > with heavily underutilized offload engine, just doing simple xor operations, but shhh don't tell anyone ) dies... 

1. run to shop, mmm bummer don't have it in stock, mmm buy other brand > bummer raid engine uses some custom partitioning > order exact same type wait couple of days ...
2. run to shop > not in stock > deprecated controller ( did good service for a couple of years ) is not available anymore & used some obscure formatting type > bye bye PITHA array....



**case > RAID onboard hardware controller:**

you have an onboard ( MOBO ) pretending to be hardware controller, which is obviously not a hardware controller but actually is BIOS software & run by the CPU :) ( no kidding > there's NO hardware controller on COTS MOBO's ( COTS > Commodity Of The Shelf > ordinary mobo's )

1. same as previous
2. same as previous



**case > RAID software nix/bsd**

your mobo dies.
take other computer > cram your disks in there > within 15min. you're back online...
( nix/bsd OS's are portable, even if you have to install file server from scratch ... I did it once in 12min. )
(Doesn't apply to Windoz, because it's not portable > tied to hardware, this alone is reason enough for not using mickeysoft as server)



Easy no ?

If you happen to be near a nix box using mdadm soft raid when someone spawns some gibberish about soft raid, just run top & show em just how much time the mdadm process used since boot.. it's negligible compared to other processes. In other words hardware controllers ( the combo  types > offload engine + connectors ) are IMHO a waste of money, and add more latency. -sidenote: latency is the very reason why they usually use AMD Opterons over Intel in supercomputers despite AMD's having less performance, AMD's have the memory controller onboard at full speed, and don't need something like FSB or large caches ( anyone comparing Intel with AMD by it's FSB is an I***t)- 

Zero RAID controllers on the other hand are a complete other breed ( it's just the controller without connectors ) and are very usefull in squeezing the last bit out of your server... As they don't replace any drive attached controller ( software ) but support existing controllers with hardware offloading.. 



:KS

---

### Post by windependence on 2008-08-15
OK you're edging me over just a bit, EXCEPT, I always keep a spare controller and I don't use junk. I have been doing large data centers for years, so I use Tyan, SuperMicro, etc. and rack mount hardware. So if you have the time (I don't want to waste yours) sell me on software RAID.

Also, I didn't quite get whether you are pro AMD or not. I am an AMD partner and I rather like them with the cores connected ON the chip and not talking to each other thru the bus.

At any rate, this has been a great conversation. I really enjoyed it an learned some things. Other folks have been rather confrontational when trying to change my mind about software RAID. I am almost convinced to put it in my dual quad-core Opteron build in the rack right now and try it. This is going to be a VMware box running 5 or 6 VMs. Any tips for disk I/O performance there? :) 

Sorry for all the questions.

-Tim

---

### Post by Ceephis on 2008-08-15
First off DJMU

Are you for real?  I have been scouring these forums for about 3 months now for someone who knows 1/3 as much as you do and can explain 1/2 of it.  Your past 4 posts have taught me more than the 50 or so pages I have printed out and have mused over for a while.

Would you be willing to put EVMS and raid 5 head to head for system down time and rebuilding a dead drive.

Do you need to boot EVMS from thumb drives to avoid the whole boot sector problem?


Thanks again for your time

Peter

---

### Post by Ceephis on 2008-08-15
BTW the error code I got from the USB drives was '21'

---

### Post by djamu on 2008-08-15
> **windependence said:**
> 
...
 so I use Tyan, SuperMicro,
...

hehehe the good stuff, 
> Also, I didn't quite get whether you are pro AMD or not. I am an AMD partner and I rather like them with the cores connected ON the chip and not talking to each other thru the bus.
Pro AMD, depends on the situation. If it's about raw computing. Lets say HPC infiniband low latency clustering up a couple of lovely 8 way quad cores on Tyanboards ( as a matter of fact the dual cores boards without level3 cache have lower latency )  ... nothing beats AMD, this kind of things can't even be done with normal available hardware from Intel so ...
Unfortunately these are expensive toys...
So if it's just about max bandwidth or processes that run according to the [[COLOR="Navy"]Embarrassingly parallel[/COLOR]]("http://en.wikipedia.org/wiki/Embarrassingly_parallel") principle I'll go for a bunch of cheapo Intel Q6600's ( Embarrassingly parallel is a type of HPC process )
My line of work is not web related but high-end 3D. which is quite a different kind of IT, OpenGL clusters the likes :) Yes you read that right, you can pile up a couple of PC's & let those work as a grahical card...

> At any rate, this has been a great conversation. I really enjoyed it an learned some things. Other folks have been rather confrontational when trying to change my mind about software RAID. I am almost convinced to put it in my dual quad-core Opteron build in the rack right now and try it. This is going to be a VMware box running 5 or 6 VMs. Any tips for disk I/O performance there? :) 

Same here, real pro's are rare around this forum.. you recognize them by having no problem to admit not to know all, but at the same time being knowledgeable... I don't know lots of things either ( don't start of on DB's, HA, or loadbalancers lol ).

Regarding Vmware > there's a couple of pittfals you should be aware of. While the host has no problem whatsoever running soft-raid ( where talking mdadm ? ), running a raid on a client can be tricky > Meaning when the host OS has no knowledge of a RAID & the RAID is entirely managed by the Vmware client.
I used to do this for a long time on my windoz workstations -yeah I sometimes still need that stuff-. Sounds weird ? Well I essentially used the client (debian) OS as firmware for a RAID, and the host could either acces It via iSCSI / NFS / SMB ( in my case I mostly used an iSCSI partition as scratch + SMB as common share, works great BTW. and still faster as real local disks -go figure-) 
Just make sure that in this case( case > raid managed by client ) write caching is disabled on the host.
> 
Sorry for all the questions.
-Tim

np nice talking to you too, regarding you being AMD partner.. Is there any chance you'll let me ( remotely ) do some performance tests on the latest CPU's ? I'm currently developing a cluster package and in need of access to the latest HW, ( I don't need submitted samples, just access as my budget doesn't allow me to buy bleeding edge HW. We'll continue this conversation then thru PM, On my website ( still building it ) there's more info. 
:)

---

### Post by djamu on 2008-08-15
> **Ceephis said:**
> First off DJMU

Are you for real?

No :)
> Would you be willing to put EVMS and raid 5 head to head for system down time and rebuilding a dead drive.
Do you need to boot EVMS from thumb drives to avoid the whole boot sector problem

Peter, if it's just for your home server, just forget about EVMS & LVM, you don't need it. 
I'll PM you my messenger account so go thru this by chat ( works quicker )

---

