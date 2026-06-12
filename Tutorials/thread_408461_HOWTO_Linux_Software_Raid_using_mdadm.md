---
title: "HOWTO: Linux Software Raid using mdadm"
date: 2007-04-13
forum: Tutorials
---

### Post by kragen on 2007-04-13
[SIZE="5"]**1) Introduction:**[/SIZE]

Recently I went out and bought myself a second hard drive with the purpose of setting myself up a performance raid (raid0). It took me days and a lot of messing about to get sorted, but once I figured out what I was doing I realised that it's actually relatively simple, so I've written this guide to share my experiences :) I went for raid0, because I'm not too worried about loosing data, but if you wanted to set up a raid 1, raid 5 or any other raid type then a lot of the information here would still apply.

[SIZE="5"]**2) 'Fake' raid vs Software raid:**[/SIZE]

When I bought my motherboard, (The ASRock ConRoeXFire-eSATA2), one of the big selling points was an on board raid, however some research revealed that rather than being a true hardware raid controller, this was in fact more than likely what is know as 'fake' raid. I think wikipedia explains it quite well: [http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)

> Hybrid RAID implementations have become very popular with the introduction of inexpensive RAID controllers, implemented using a standard disk controller and BIOS (software) extensions to provide the RAID functionality. The operating system requires specialized RAID device drivers that present the array as a single block based logical disk. Since these controllers actually do all calculations in software, not hardware, they are often called "fakeraids", and have almost all the disadvantages of both hardware and software RAID.

After realising this, I spent some time trying to get this fake raid to work - the problem is that although the motherboard came with drivers that let windows see my two 250 GB drives as one large 500 GB raid array, Ubuntu just saw the two separate drives and ignored the 'fake' raid completely. There are ways to get this fake raid working under linux, however if you are presented with this situation then my advice to you is to abandon the onboard raid controller and go for software raid instead. I've seen arguments as to why software raid is faster and more flexible, but I think the best reason is that software raid is far easier to set up! :)

[SIZE="5"]**3) The Basics of Linux Software Raid:**[/SIZE]

For the basics of raids try looking on Wikipedia again: [http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks). I don't want to discuss it myself because its been explained many times before by people who are far more qualified to explain it than I am. I will however go over a few things about software raids:

Linux software raid is more flexible than hardware raid or true raid because rather than forming a raid arrays between identical disks, the raid arrays are created between identical partitions. As far as I understand, if you are using hardware raid between (for example) two disks, then you can either create a raid 1 array between those disks, or a raid 0 array. Using software raid however, you could create two sets of identical partitions on the disks, and for a raid 0 array between two of those partitions, and a raid 1 array between the other two. If you wanted to you could probably even create a raid array between two partitions on the same disk! (not that you would want to!)

The process of setting up the a raid array is simple:

[LIST=1]
[*]Create two identical partitions
[*]Tell the software what the name of the new raid array is going to be, what partitions we are going to use, and what type of array we are creating (raid 0, raid 1 etc...)
[/LIST]

Once we have created this array, we then format and mount it in a similar way to the way we would format a partition on a physical disk.

[SIZE="5"]**4) Which Live CD to use:**[/SIZE]

You want to download and burn the alternate install Ubuntu cd of your choosing, for example, I used:

```
ubuntu-6.10-alternate-amd64.iso
```

If you boot up the ubuntu desktop live CD and need to access your raid, then you will need to install mdadm if you want to access any software raid arrays:

```
sudo apt-get update
sudo apt-get install mdadm
```

Don't worry too much about this for now - you will only need this if you ever use the Ubuntu desktop cd to fix your installation, the alternate install cd has the mdadm tools installed already.

[SIZE="5"]**5) Finally, lets get on with it!**[/SIZE]

**[SIZE="3"]Boot up the installer[/SIZE]**
Boot up the alternate install CD and run through the text based installation until you reach the partitioner, and select "Partition Manually".

**[SIZE="3"]Create the partitions you need for each raid array[/SIZE]**
You now need to create the partitions which you will (in the next step) turn into software raid arrays. I recommend using the space at the start, or if your disks are identical, the end of your disks. That way once you've set one disk up, you can just enter exactly the same details for the second disk. The partitioner should be straightforward enough to use - when you create a partition which you intend to use in a raid, you need to change the type to "Linux RAID Autodetect".

How you partition your installation is upto you, however there are a few things to bear in mind:

[LIST=1]
[*]If (like me) you are going for a performance raid, then you will need to create a separate /boot partition, otherwise grub wont be able to boot - it doesn't have the drivers needed to access raid 0 arrays. It sounds simple, but it took me so long to figure out.
[*]If, on the other hand, you are doing a server installation (for example) using raid 1 / 5 and the goal is reliability, then you probably want the computer to be able to boot up even if one of the disks is down. In this situation you need to do something different with the /boot partition again. I'm not sure how it works myself, as I've never used raid 1, but you can find some more information in the links at the end of this guide. Perhaps I'll have a play around and add this to the guide later on, for completeness sake.
[*]If you are looking for performance, then there isn't a whole load of point creating a raid array for swap space. The kernel can manage multiple swap spaces by itself (we will come onto that later).
[*]Again, if you are looking for reliability however, then you may want to build a raid partition for your swap space, to prevent crashes should one of your drives fail. Again, look for more information in the links at the end.
[/LIST]

On my two identical 250 GB drives, I created two 1 GB swap partitions, two +150 GB partitions (to become a raid0 array fro my /home space), and two +40 GB partitions (to become a raid 0 array for my root space), all inside an extended partition at the end of my drives. I then also created a small 500 MB partition on the first drive, which would become my /boot space. I left the rest of the space on my drives for ntfs partitions.

**[SIZE="3"]Assemble the partitions as raid devices[/SIZE]**
Once you've created your partitions, select the "Configure software raid" option. The changes to the partition table will be written to the disk, and you will be allowed to create and delete raid devices - to create a raid device, simply select "create", select the type of raid array you want to create, and select the partitions you want to use. Remember to check which partition numbers you are going to use in which raid arrays - if you forget, hit <Esc> a few times to bring you back to the partition editor screen where you can see whats going on.

**[SIZE="3"]Tell the installer how to use the raid devices[/SIZE]**
Once you are done, hit finish - you will be taken back to the partitioner where you should see some new raid devices listed. Configure these in the same way you would other partitions - set them mounts points, and decide on their filesystem type.

**[SIZE="3"]Finish the instalation[/SIZE]**
Once you are done setting up these raid devices (and swap / boot partitions you decide to keep as non-raid), the installation should run smootly.

[SIZE="5"]**6) Configuring Swap Space**[/SIZE]

I mentioned before that the linux kernel automatically manages multiple swap partitions, meaning you can spread swap partitions across multiple drives for a performance boost without needing to create a raid array. A slight tweak may be needed however; each swap partition has a priority, and if you want the kernel to use both at the same time, you need to set the priority of each swap partition to be the same. First, type

```
swapon -s
```

to see your current swap usage. Mine outputs the following:

```
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       979956  39080   -1
/dev/sdb5                               partition       979956  0       -2
```

As you can see, the second swap partition isn't being used at the moment, and won't be until the first one is full. I want a performance gain, so I need to fix this by setting the priority of each partition to be the same. Do this in /etc/fstab, by adding pri=1 as an option to each of your swap partitions. My /etc/fstab file now looks like this:

```
# /dev/sda5
UUID=551aaf44-5a69-496c-8d1b-28a228489404 pri=1            swap    sw              0       0
# /dev/sdb5
UUID=807ff017-a9e7-4d25-9ad7-41fdba374820 pri=1            swap    sw              0       0
```

[SIZE="5"]**7) How to do things manually**[/SIZE]

As I mentioned earlier, if you ever boot into your instalation with a live cd, you will need to install mdadm to be able to access your raid devices, so its a good idea to at least roughly know how mdadm works. [http://man-wiki.net/index.php/8:mdadm](http://man-wiki.net/index.php/8:mdadm) has some detailed information, but the important options are simply:

```
[LIST]
[*]-A, --assemble
    Assemble a pre-existing array that was previously created with --create.
[*]-C, --create
    Create a new array. You only ever need to do this once, if you try to create arrays with partitions that are part of other arrays, mdadm will warn you.
[*]--stop
    Stop an assembled array. The array must be unmounted before this will work.
[/LIST]
```

When using --create, the options are:

```
mdadm --create *md-device* --chunk=*X* --level=*Y* --raid-devices=*Z* *devices*
[LIST]
[*]-c, --chunk=
    Specify chunk size of kibibytes.  The default is 64.
[*]-l, --level=
    Set  raid  level, options are: linear, raid0, 0, stripe, raid1, 1, mirror, raid4, 4, raid5,  5,  raid6, 6,  multipath,  mp, fautly.
[*]-n, --raid-devices=
    Specify the number of active devices in the array.
[/LIST]
```

for example:

```
mdadm --create /dev/md0 --chunk=4 --level=0 --raid-devices=2 /dev/sda1 /dev/sdb1
```

will create a raid0 array /dev/md0 formed from /dev/sda1 and /dev/sdb1, with chunk size 4.

When using --assemble, the usage is simply:

```
mdadm --assemble *md-device* *component-devices*
```

for example

```
mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1
```

Which will assemble the raid array /dev/md0 from the partitions /dev/sda1 and /dev/sdb1

Alternatively you can use:

```
mdadm --assemble --scan
```

and it will assemble any raid arrays it can detect automatically.

Lastly,

```
mdadm --stop /dev/md0
```

will stop the assembled array md0, so long as its not mounted.

If you wish you can set the partitions up yourself manually using fdisk and mdadm from the command line. Either boot up a desktop live cd and apt-get mdadm as described before, or boot up the alternate installer and hit escape until you see a list of the different stages of instalation - the bottom one should read execute shell - which will drop you at a shell with fdisk, mdadm and mkfs etc... available.

Note that if you ever need to create another raid partition, you create filesystems on them in exactly the same way you would a normal physical partition. For example, to create an ext3 filesystem on /dev/md0 I would use:

```
mkfs.ext3 /dev/md0
```

And to create a swapspace on /dev/sda7 I woud use:

```
mkswap /dev/sda7
```

Lastly, mdadm has a configuration file located at ```
/etc/mdadm/mdadm.conf
``` this file is usually automatically generated, and mdadm will probably work fine without it anyway. If you're interested then [http://man-wiki.net/index.php/5:mdadm.conf](http://man-wiki.net/index.php/5:mdadm.conf) has some more information.

And that's pretty much it. As long as you have mdadm available, you can create / assemble raid arrays out of identical partitions. Once you've assembled the array, treat it the same way you would a partition on a physical disk, and you can't really go wrong! :)

I hope this has helped someone! At the moment I've omitted certain aspects of dealing with raids with redundancy (like raid 1 and raid 5), such a rebuilding failed arrays, simply because I've never done it before. Again, I may have a play around and add some more information later (for completeness), or if anyone else running a raid 1 wants to contribute, it would be most welcome.

[SIZE="5"]**Other links**[/SIZE]

**The Linux Software Raid Howto: **
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)
This guide refers to a package "raidtools2" which I couldn't find in the Ubuntu repositories - use mdadm instead, it does the same thing.

**Quick HOWTO: Linux Software Raid**
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)

**Using mdadm to manage Linux Software Raid arrays**
[http://www.linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html](http://www.linuxdevcenter.com/pub/a/linux/2002/12/05/RAID.html)

**Ubuntu Fake Raid HOWTO In the community contributed documentation**
[https://help.ubuntu.com/community/FakeRaidHowto?highlight=%28raid%29](https://help.ubuntu.com/community/FakeRaidHowto?highlight=%28raid%29)

I hope this guide helps people understand and set up their raids :)

---

### Post by Fraoch on 2007-04-28
Thanks very much for this - it worked flawlessly!

---

### Post by mgrusin on 2007-05-06
Great howto!  Please consider adding this to the community documentaion wiki.  There is currently nothing in there (at least that I could find) on the use of mdadm.

-MG

---

### Post by bauhaus on 2007-06-13
Excellent information and really useful as I am about to setup a RAID 5 myself and very much needed some pointers. I already have a working install of Feisty so I it looks like I will have to install mdadm and go from there. I'll let you know if it works out ;)

---

### Post by gnychis on 2007-06-28
so i followed your guide, and i did the manual configuration because the minimal server installer CD was giving me problems.

so I created /dev/md0 and used mdadm --create to create a RAID0.

I made use of your note about RAID0 and boot partitions, so I created one on my first disk and made sure the two disks matched and all.

The install went perfectly fine, but when I reboot i get:
```

Starting up ...
Loading, please wait...
mdadm: No devices listed in conf file were found.

```

and nothing happens.

where is the config file stored?  how do i get it to reassemble my raid disks on boot?

thanks!

---

### Post by Qumefox on 2007-06-29
My feisty install hangs at the exact same spot when one of the discs of my raid5 array is missing. (which I don't understand, since it should still be able to run on the 2 remaining drives, since that's the whole point of raid5) You might try using the instructions on accessing your array via the desktop live cd, to make sure the array is indeed there and not corrupted somehow.  If it's corrupted, with a raid0 array, you'd be missing your whole root fs, and the kernel would have nothing else to load.

---

### Post by Qumefox on 2007-06-30
I just discovered that if you let it sit, it'll timeout and dump you to the initramfs prompt, and from there you should be able to see exactly why it's not booting correctly. 

My guess is that mdadm is trying to build the array before udev has found all the devices though, so your raid0 array isn't initializing. And therefor, you have no / filesystem.

At least this is what I gleaned from the bug reports about similar symptoms.

---

### Post by lns on 2007-07-13
Thanks for this howto!! This is great. I wish I knew that Feisty alternate-install (x86-64) CD didn't have an installer option for software RAID before I nuked my newly installed LTSP server :( Oh well. A RAID-1/5 HOWTO would be awesome. Maybe I'll try and write one up, although I'm not very experienced at writing HOWTOs.

---

### Post by gnychis on 2007-07-13
> **gnychis said:**
> so i followed your guide, and i did the manual configuration because the minimal server installer CD was giving me problems.

so I created /dev/md0 and used mdadm --create to create a RAID0.

I made use of your note about RAID0 and boot partitions, so I created one on my first disk and made sure the two disks matched and all.

The install went perfectly fine, but when I reboot i get:
```

Starting up ...
Loading, please wait...
mdadm: No devices listed in conf file were found.

```

and nothing happens.

where is the config file stored?  how do i get it to reassemble my raid disks on boot?

thanks!

bahhh... i fixed my problem by removing 'savedefault' from the grub config

---

### Post by uclalinux on 2007-07-18
thanks

---

### Post by Klingon on 2007-09-27
Question:

I have 2 disks atm which I want to make into one software raid (RAID0)

If at a later time I get a third new disk can I append this to the same raid without loosing any data in the current raid?

---

### Post by tommi-fi on 2007-10-01
I have Raid5 setup with 3 250GB ATA Discs. Two of the disk are Maxtor 250GB and one is 250GB Segate. Maxtor discs are a bit bigger than Seagate.

But...

There is something wrong with my setup. Once I reboot my system, array is broken. mdadm says two off the three dics are broken? Where should I start searching for error.

Here's my system
AMD Duron 700MHz
512M SDRAM
200GB System
3x250GB RAID
2x Promise PCI ATA controller
Ubuntu 7.04 Server.
mobo has its own HPT730 RAID controller. (Don't remenber model)

And sorry for my bad english.

---

### Post by cocodude on 2007-10-07
> **Klingon said:**
> I have 2 disks atm which I want to make into one software raid (RAID0)

If at a later time I get a third new disk can I append this to the same raid without loosing any data in the current raid?

Although I haven't done it myself, I think you can. Check out [http://ubuntuforums.org/showthread.php?t=517282&highlight=md0](http://ubuntuforums.org/showthread.php?t=517282&highlight=md0)

Cocodude

---

### Post by matthewcraig on 2007-11-14
Receiving an error saying device in use when running this command?

> mdadm --create /dev/md0 --chunk=4 --level=0 --raid-devices=2 /dev/sda1 /dev/sdb1

Use --verbose to be promoted to force the "device busy" error.

---

### Post by therufus on 2007-12-02
I have gutsy server version and can't get software RAID to work. mdadm isn't even installed. If I try to apt-get it, I get:

root@server:/usr/bin# apt-get install mdadm
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package mdadm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mdadm has no installation candidate

apt-get update works fine when I set everything to New Zealand servers (the Australian repository is always down - thanks for that Optus). I tried manually downloading mdadm and doing an install but make isn't even installed on gutsy. Installing make doesn't work either because of other dependencies, and further down the rabbit hole I go.

What am I doing wrong?

---

### Post by linuxhelp on 2008-01-16
Hi All

i want to setup ubuntu 6.10 with software raid on a Sun Qube 3

is there a little howto for help?

the qube does not support virtual tty's

hope to get it alive

how can a raid be rebuild after a crash easyly?

thanks tom
germany

---

### Post by sonofanickel on 2008-01-31
Please, don't forget the all important step of adding your new md array to the fstab file. This will ensure your array is restarted at bootup. I thought this was worth mentioning again (the original post somewhat glossed over it).

[here is a perfect example]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Edit_The_.2Fetc.2Ffstab_File")

---

### Post by SteveHillier on 2008-02-01
I am going to say thank you because you have pointed me in the right direction.
I am using an ASRock m/b and was trying to use the on board RAID.  If I do that I see no drives in Ubuntu.
Using Non-RAID settings of the m/b at lease allows Ubuntu to see the disks.  I have not been able to bet installed yet but I am heading in the right direction
I will update when I have got things working

---

### Post by SteveHillier on 2008-02-05
Further to my earlier comments it is an issue with Dapper.
I was trying to use Dapper because it is the LTS version, but Dapper only sees the first SATA drive.  No matter how many or where they are plugged only the first available drive is shown.
I know I can see them all in Gutsy - trouble is at the moment I cannot get the Live CD to install.  I get the first menu up but then it sits and goes nowhere.
I am at this very moment (on another machine) downloading the alternate CD so I might update this post later.
Bye for now!!

---

### Post by SteveHillier on 2008-02-06
Once again thanks to kragen for this thread.
However......
I wish it were that simple.  I am now on my umpteenth attempt at setting up a server with a mirrored RAID.
My history so far.
I want to set up a web server with a RAID so that I can have some measure of security for the sites I am going to host.  So initially I thought I will use DAPPER as this is the LTS offering.  Only to find that Dapper cannot cope with more than 1 SATA drive - it does not seem to recognise the others.  What ho, never mind.  I look at Plesk website and they offer support on Gutsy as well.
So I download the image from the Ubuntu website for AMD64.  I took the standard version.  Ran the CD which gave me the option to install and it just sat there looking at me.  I tried all the other options on the menu - the only one that did something was the check CD option.
Never mind, maybe it corrupted on its way to the CD, so burnt another copy.  Same - no options would go anywhere.
Well maybe it corrupted during the download.  Downloaded another copy from a different mirror.  Burnt the CD - just the same.  (if anyone wants a CD I have a few spare!!!)
I found the alternate version for the AMD64 desktop on the website and downloaded.  Burnt the image to disk.  Ran the installer.  It worked!!!
Next I got to the partitioner to find that I had got a disk missing.  Checked all connections and restated the installer.  I found all my disks.  Then set about partitioning.
OK I have three disks.  1 x 80Gb which I am using to install OS and normal stuff.  2 x 500Gb which are going to be mirrored for the sites.
This is where I differ from kragen in his (I assume his and not her - apologies if I have wrong gender) comments.
and this is where I am going to be slightly critical.  Kragen sets up how he is going to partition his disk.  1Gb for swap, 150Gb for RAID / home, 40Gb for root, some space for boot.  My criticism is that for someone who has never used a partitioner there is insufficient detail.
for example.  Go to disk 1.  set up partition by a) stating the format to be used, b) saying how it is to be formatted, c) giving it the mount point and so on.
On my system I have set partitions on the disks I am using for RAID as being Physical volume for RAID and I do this on both but then I have to set a RAID partition giving the same details - or so I think.
When I have worked out precisely what I have had to do I will create a new thread - referencing kragen .
I have twice got past the point of partitioning the disks only to have the install fail further down the line.  When I have nailed the little ...... I will wax lyrical once again.
Bye for now

---

### Post by secstate on 2008-02-08
I am trying to put together a raid1 configuration using two drives one of which is 200g and the other is 250g. I have one using the whole drive ending on cylinder 23241 and then created two partitions on the second, one ending at 23241 also and the other taking up the rest of the drive.

First off, should I even be trying this with two different drives (the only physical difference according to hdparm is a buffer of 8MB on one and 2MB on t'other)?

Secondly, and my problem now, is that mdadm stalls at 21.9% and slowly brings the computer to a freeze while doing a resync. Can anyone help me?

---

### Post by secstate on 2008-02-08
Next time someone just remind me to check my logs. There must have been 200 read/write errors on one of the drives . . . that'll do it.

---

### Post by Gabn on 2008-02-12
> **mgrusin said:**
> Great howto!  Please consider adding this to the community documentaion wiki.  There is currently nothing in there (at least that I could find) on the use of mdadm.

-MG

There is now i started writing this 
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

It's not complete but that's coming

---

### Post by Sam Lars on 2008-07-17
This has helped me more than once.  I switched motherboards and didn't realize that it changed hda, etc., to sda, etc., so after a lot of tooling around with it, this guide helped me figure that out!

---

### Post by jpkotta on 2008-07-24
I have software RAID, different levels (0 or 1), on several partitions, one of which is empty.  I want to install on the empty one, but I can't see how to do this without nuking the whole array with the installer.  If I chroot with the alternate CD, I see my md devices, likewise if I install mdadm on the desktop CD, but neither installer will show the md devices.

---

### Post by crtlbreak on 2008-07-25
I am not sure I understand  - do you already have a version of ubuntu installed on partition/s in your box?
or are you simply booting from live CD and are weary to continue the install to your HD? and are now trying to add the mdadm package at this stage? 

the mdadm you "install" to the desktop Live CD is actually installed to ram as the CD is not altered during the live CD bootup - to create raid devices and mirrors at this stage the  alternate install CD is needed

what I think you are trying to do is install ubuntu from a liveCD and simultaneously maintain the integrity of the other data and OS's on your box by installing ubuntu to a spare partition - being careful - right?
let us know if this is the case?
regards

---

### Post by jpkotta on 2008-07-25
> **crtlbreak said:**
> I am not sure I understand  - do you already have a version of ubuntu installed on partition/s in your box?
or are you simply booting from live CD and are weary to continue the install to your HD? and are now trying to add the mdadm package at this stage?

the mdadm you "install" to the desktop Live CD is actually installed to ram as the CD is not altered during the live CD bootup - to create raid devices and mirrors at this stage the  alternate install CD is needed

what I think you are trying to do is install ubuntu from a liveCD and simultaneously maintain the integrity of the other data and OS's on your box by installing ubuntu to a spare partition - being careful - right?
let us know if this is the case?
regards

Yes, that is exactly what I want to do.  I have Ubuntu installed, but I want to do a parallel installation, so I could boot into either.  I want to install a separate OS without messing up the current one.  

I understand that when I install mdadm on a live CD, it only exists in RAM.  I was just hoping that I could trick the installer into recogizing the md devices.

---

### Post by crtlbreak on 2008-07-26
grub will manage the separate installations quite fine if they are on different partitions - also not sure if you are installing the same OS version eg 8.04 hardy heron twice but on different partitions - I think that might need a bit more research?

---

### Post by jpkotta on 2008-07-26
> **crtlbreak said:**
> grub will manage the separate installations quite fine if they are on different partitions - also not sure if you are installing the same OS version eg 8.04 hardy heron twice but on different partitions - I think that might need a bit more research?

I'll deal with grub when I come to that.  I'm not at all worried about grub.  I put /boot on it's own partition so I can do this sort of thing.

I want / on a RAID0 device.  /boot, /home, and / for the already installed OS are on their own RAID devices (RAID 0 or 1).  My roadblock is that the Ubuntu installer will only install to physical partitions (e.g. /dev/sda3) but not general block devices (e.g. /dev/md2), OR it will install to a softraid device but requires destroying the disk.  I can't find a workaround, but it seems like a dumb limitation, so I'm hoping there is one.

I have Hardy installed, and I want to install Gutsy.  

This is for testing the upgrade procedure to Hardy, because I encountered a problem and I want to see if it's repeatable.  After coming across this problem, it is now just as much for my own curiosity as it is for investigating the upgrade.  I can't understand why such a limitation would be built into the installer.  What if I nuked my OS?  I would have to nuke my disk (along with my /home) to reinstall with softraid as well?

---

### Post by crtlbreak on 2008-07-27
from the "alternate" installation CD the installer will read your MD devices and you can choose to "do not format the partition" under the installation process. If you are installing on to a newly created partition/LVM/blockdevice then your existing partitions and data integrity should be unaffected if the correct selections have been made under the installation process.

you are in the classic situation where trying to solve or investigate one issue has created another far greater and more complex issue to try and resolve - how many times have we all been there before??:rolleyes::rolleyes:

a possible suggestion is to use an alternate physical disk rather than mess up your existing system

I will always apply my five rules
5 Rules of life
[LIST=1]
[*]Have you made a backup or can you recover?
[*]If its not broken - try and fix it till its broken as it probably needed replacing anyway
[*]Do not try and destroy one working object in the possibility of repairing another - you will end up with two broken objects.
[*]Paddy's law says that Murphy was an optimist.
[*]No major changes on a Friday - especially after lunchtime
[/LIST]
The rules are best applied in order - I think you are possibly past rule 1 entering in to rule 2? :-\"#-o

---

### Post by alecm3 on 2008-08-03
I decided to switch from SuSE to Ubuntu, and I am configuring my first production MySQL server with 8.04.
I am using software RAID 1.
The machine is not yet deployed, it's sitting in the office.
Suddenly, i hear loud fan noise, even though there are no tasks running, and I check the load average: 2.8! Using "top" I notice that
md2_resync process is the culprit.

Then I look at /proc/mdstat and see:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sda3[0] sdb3[1]
135347520 blocks [2/2] [UU]
[============>........] check = 62.9% (85253248/135347520) finish=7.9min speed=125122K/sec


So apparently, mdadm daemon decided to check the array. 
How can i disable or control the schedule of these "checks" without having to disable mdadm daemon alltogether in /etc/init.d?

It's not acceptable for a production database machine to suddenly start a maintanence process that saturates its I/O bandwidth.

---

### Post by bsmith1051 on 2008-08-03
I've never seen my array do that.  Are you sure there wasn't a hw prob with one of the drives?

---

### Post by AmJaD on 2008-08-03
Here is alot of messing about with Ubuntu when it came to setting up raid and for only 2 HDDz you wont really see the difference. i hope in the next ubuntu version they make it as simple as some of the other distros.
A name like "Raiding Rabbit" will be cool

---

### Post by bsmith1051 on 2008-08-03
> **AmJaD said:**
> for only 2 HDDz you wont really see the difference. i hope in the next ubuntu version they make it as simple as some of the other distros.
Which distros have simple/automatic support for RAID?

Also, in the process of configuring/testing that my RAID1 would boot degraded (by simply unplugging one drive) I found that the array booted-up and loaded OS, apps, etc about 25% faster than 1 drive alone. Not sure if that indicates an actual speed advantage to RAID1 (though it's supposed to intelligently distribute read requests between both drives) or if the degraded array simply ran slower than a 'normal' 1-drive system.

---

### Post by alecm3 on 2008-08-03
> **bsmith1051 said:**
> I've never seen my array do that.  Are you sure there wasn't a hw prob with one of the drives?

I doubt that, for several reasons:

1) When it does a rebuild, it looks like 

[>....................]  **recovery **=  0.1%

in my case, it was 

[>....................]  **check **=  0.1%

2) if there's a hardware problem, it will not try to check or even rebuild, it would simply mark disk as failed [U_].

3) I saw this thread [http://lists.clug.org.za/pipermail/clug-chat/2007-November/024059.html](http://lists.clug.org.za/pipermail/clug-chat/2007-November/024059.html) :

> Yes, current software RAID has an option to [B]check the arrays periodically.
> Apparently you have this enabled[/B]. I'm  not sure that checking involves
> re-syncing though. Perhaps there was some sort of problem found? If so it
> should be in your logs.

In my logs:

Aug  2 20:24:39 db2 -- MARK --
Aug  2 20:44:39 db2 -- MARK --
Aug  2 21:04:39 db2 -- MARK --
Aug  2 21:24:39 db2 -- MARK --
Aug  2 21:44:39 db2 -- MARK --
Aug  2 22:04:39 db2 -- MARK --
Aug  2 22:24:39 db2 -- MARK --
Aug  2 22:44:39 db2 -- MARK --
Aug  2 23:04:39 db2 -- MARK --
Aug  2 23:24:39 db2 -- MARK --
Aug  2 23:44:39 db2 -- MARK --
Aug  3 00:04:39 db2 -- MARK --
Aug  3 00:24:39 db2 -- MARK --
Aug  3 00:44:39 db2 -- MARK --
Aug  3 01:04:39 db2 -- MARK --
Aug  3 01:06:01 db2 kernel: [187105.414819] md: data-check of RAID array md0
Aug  3 01:06:01 db2 kernel: [187105.414824] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Aug  3 01:06:01 db2 kernel: [187105.414826] md: using maximum available idle IO bandwidth (but not more than 200000 K
B/sec) for data-check.

No I/O error prior to this "data-check", so it seems quite sudden.

I wonder if this check is an addition to the newest version of mdadm (I am using Ubuntu  8.04 server with mdadm - v2.6.3 - 20th August 2007
I cannot find more information on this however.

---

### Post by alecm3 on 2008-08-03
> **alecm3 said:**
> I doubt that, for several reasons:

1) When it does a rebuild, it looks like 

[>....................]  **recovery **=  0.1%

in my case, it was 

[>....................]  **check **=  0.1%

2) if there's a hardware problem, it will not try to check or even rebuild, it would simply mark disk as failed [U_].

3) I saw this thread [http://lists.clug.org.za/pipermail/clug-chat/2007-November/024059.html](http://lists.clug.org.za/pipermail/clug-chat/2007-November/024059.html) :

> Yes, current software RAID has an option to [B]check the arrays periodically.
> Apparently you have this enabled[/B]. I'm  not sure that checking involves
> re-syncing though. Perhaps there was some sort of problem found? If so it
> should be in your logs.

In my logs:

Aug  2 20:24:39 db2 -- MARK --
Aug  2 20:44:39 db2 -- MARK --
Aug  2 21:04:39 db2 -- MARK --
Aug  2 21:24:39 db2 -- MARK --
Aug  2 21:44:39 db2 -- MARK --
Aug  2 22:04:39 db2 -- MARK --
Aug  2 22:24:39 db2 -- MARK --
Aug  2 22:44:39 db2 -- MARK --
Aug  2 23:04:39 db2 -- MARK --
Aug  2 23:24:39 db2 -- MARK --
Aug  2 23:44:39 db2 -- MARK --
Aug  3 00:04:39 db2 -- MARK --
Aug  3 00:24:39 db2 -- MARK --
Aug  3 00:44:39 db2 -- MARK --
Aug  3 01:04:39 db2 -- MARK --
Aug  3 01:06:01 db2 kernel: [187105.414819] md: data-check of RAID array md0
Aug  3 01:06:01 db2 kernel: [187105.414824] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Aug  3 01:06:01 db2 kernel: [187105.414826] md: using maximum available idle IO bandwidth (but not more than 200000 K
B/sec) for data-check.

No I/O error prior to this "data-check", so it seems quite sudden.

I wonder if this check is an addition to the newest version of mdadm (I am using Ubuntu  8.04 server with mdadm - v2.6.3 - 20th August 2007
I cannot find more information on this however.


This problem is listed as Ubuntu bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212684](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/212684)

There is a cron script 
/etc/cron.d/mdadm
which runs /usr/share/mdadm/checkarray on the first Sunday of each month (which happened yesterday).

root@db2:/etc/cron.d# more mdadm 
#
# cron.d/mdadm -- schedules periodic redundancy checks of MD devices
#
# Copyright © martin f. krafft <madduck@madduck.net>
# distributed under the terms of the Artistic Licence 2.0
#
# $Id$
#

# By default, run at 01:06 on every Sunday, but do nothing unless the day of
# the month is less than or equal to 7. Thus, only run on the first Sunday of
# each month. crontab(5) sucks, unfortunately, in this regard; therefore this
# hack (see #380425).
6 1 * * 0 root [ -x /usr/share/mdadm/checkarray ] && [ $(date +\%d) -le 7 ] && /usr/share/mdadm/checkarray --cron --a
ll --quiet

Apparently, this cron killed the systems for quite a lot of people:
[http://ubuntuforums.org/showthread.php?t=748418](http://ubuntuforums.org/showthread.php?t=748418) etc

---

### Post by alecm3 on 2008-08-03
> **bsmith1051 said:**
> 

Not sure if that indicates an actual speed advantage to RAID1 (though it's supposed to intelligently distribute read requests between both drives) or if the degraded array simply ran slower than a 'normal' 1-drive system.

Reads on RAID 1 with N disks are N times faster than on a single disk. Writes are the same speed or slightly slower.

---

### Post by AmJaD on 2008-08-04
> **bsmith1051 said:**
> Which distros have simple/automatic support for RAID?


Well there is fedora. that was painless when it came to setting up raids but for some reason i just didnt like it.

also with raid1... thats more mirroring (had drive back-up). i dont really see the point on linux based desktops. (i mean its not like your going to get attacked by a win32 worm is it).
Raid0 is more performace
I was running vista with x2 hdds but i really noticed a difference when i had 4 hdds together (ram bus speed playes a big part as well).

---

### Post by crtlbreak on 2008-08-04
> **bsmith1051 said:**
> Which distros have simple/automatic support for RAID?
:-k :-k
I think simple & automatic are not necessarily RAID and nix approaches to anything - dont get me wrong I am not being critical of your comments or of the linux world - just a general approach of "rigid, manual and locked down" in the nix world versus automatic everything in the ms world.
just my observations. :D
regards

---

### Post by crtlbreak on 2008-08-04
> **alecm3 said:**
>  ....  Ubuntu, and I am configuring my first production MySQL server with 8.04.  .... 

Dear alecm3
Are you using Ubuntu Server? I know the respective kernels of desktop and server are different with server being more tweaked to perform server functionality as opposed to desktop.
Regards

---

### Post by alecm3 on 2008-08-05
> **crtlbreak said:**
> Dear alecm3
Are you using Ubuntu Server? I know the respective kernels of desktop and server are different with server being more tweaked to perform server functionality as opposed to desktop.
Regards


Yes, I am using 8.04.1 hardy heron server...

---

### Post by axcairns on 2008-08-16
This is doing my head in. I created my array and can see it in mdstat but I can't get any partitions created on it. When I fdisk /dev/md0, create the partition and write I get the following -

```
Disk /dev/md0: 1000.2 GB, 1000210300928 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00048f36

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1      121601   976760001   83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
```

Rebooting has no effect. The partition does not exist except inside fdisk! I checked /dev/disk/by-id/ and only the device itself (plus all the physical disks) was there. Opening fdisk again and the partition looks fine but exit and no sign.

/proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active linear sda1[0] sdb1[1]
      976767872 blocks 64k rounding
      
unused devices: <none>
```

/etc/mdadm/mdadm.conf
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Sat, 16 Aug 2008 14:15:06 +0800
# by mkconf $Id$
```

fdisk -l
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d73fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d73fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23eb23ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4678    37576003+  83  Linux
/dev/sdc2            4679        4865     1502077+   5  Extended
/dev/sdc5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0c32b920

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641   83  Linux

Disk /dev/md0: 1000.2 GB, 1000210300928 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00048f36

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1      121601   976760001   83  Linux

Disk /dev/sde: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       38913   312568641   83  Linux

Disk /dev/sdf: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       38913   312568641   83  Linux

Disk /dev/sdg: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       38913   312568641   83  Linux
```


Help!

Allan

---

### Post by axcairns on 2008-08-16
Never mind - I'm an idiot. I was trying to partition the raid device rather than just formatting it.

---

### Post by lleberg on 2008-09-02
I followed the howto and set up 2x500 gb raid0, for storage.

Now i'm moving what i want to keep there, then i plan to format my system disc and reinstall.

But the thought just hit me, how do i do to add the raid array on the new system? is et as simple as i hope it is?

---

### Post by crtlbreak on 2008-09-02
You would need to obatin the alternate install CD I not he liveCD version. During the install process at disk config you will need to choose "custom" rather than just the defaults.You will then have the option to customise LVM, set up raid 0, 1, 5 etc.
Then the rest you should be quite used to.

---

### Post by lleberg on 2008-09-02
Oh, that's too bad, since i'm in my new system now.

And oh, i didn't use the actual howto o page one, but one linked to in the post, the one at [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID)

Allthough i don't know the difference.

How do i go about to add the discs to the system?
Hopefully without destroying what's on them..

Edit:
Is it a bad idea to just recreate the raid array with

mdadm --create --verbose /dev/md0 --level=0 --raid-devices=2 /dev/sdb1 /dev/sdc1

Create the mdadm.conf Configuration File and 
create a mounting point for it?
For me to acces the data written on both discs (stripe)

---

### Post by cyberkost on 2008-09-02
> **crtlbreak said:**
> You would need to obatin the alternate install CD I not he liveCD version. During the install process at disk config you will need to choose "custom" rather than just the defaults.You will then have the option to customise LVM, set up raid 0, 1, 5 etc.
Then the rest you should be quite used to.

Well, yeah, but there's not much of "etc." there.  E.g. level 10 is not available, so one has to do it "by hand."

---

### Post by lleberg on 2008-09-02
Problems solved, everyhnig is now fine.

The command i was looknig for was

sudo mdadm -A /dev/md0 /dev/sdb1 /dev/sdc1

---

### Post by cyberkost on 2008-09-07
I'm trying install Ubuntu-8.04 desktop following the instructions here: [http://how2forge.org/install-ubuntu-with-software-raid-10]("http://how2forge.org/install-ubuntu-with-software-raid-10").  Everything seems to be fine, but soon after I leave partitioner and go into "Installing system" window I get a error pop-up that says "The installer needs to remove operating system files from the install target, but was unable to do so.  The install cannot continue."

Does anyone have any clue as to what might be happening?

Edit: I've done some poking around and it seems that the problem starts even earlier -- the partitioner does not see /dev/sdi, /dev/sdj, or /dev/sdk (that I have my /dev/md1, /dev/md2, and /dev/md3 aliased to).  The only way I'm able to make partitioner see the raid partitions is to have them aliased (using -f option) to /dev/sd[e-g], which are SD, CF and MMS cardreaders on my system.  SOS!!!

---

### Post by crtlbreak on 2008-09-08
I think that page actually has the answer for you

" ... Then create the file system on the RAID array. Format it now because [COLOR="Blue"]the partitioner in the installer doesn't know how to modify or format RAID arrays[/COLOR]. I used XFS file system, because XFS has great large file performance. Then you will create an alias for the RAID array with the link command because the Ubuntu installer won't find devices starting with "md"."

Does that seem logical?
Just to be sure -  it is RAID 10  you are requiring with 4 seperate devices?

---

### Post by cyberkost on 2008-09-08
> **crtlbreak said:**
> I think that page actually has the answer for you

" ... Then create the file system on the RAID array. Format it now because [COLOR="Blue"]the partitioner in the installer doesn't know how to modify or format RAID arrays[/COLOR]. I used XFS file system, because XFS has great large file performance. Then you will create an alias for the RAID array with the link command because the Ubuntu installer won't find devices starting with "md"."

Does that seem logical?
Just to be sure -  it is RAID 10  you are requiring with 4 seperate devices?

I've done *all* those steps and it did not work ... and yes, it's raid 10 with 4 identical drives.   It looks like this is a [known problem]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/44609") with a workaround (and, perhaps, a solution in future releases).  One can either use a workaround (which I did not try) or alternate install CD.
Back to my story -- I thought I was stuck between a rock and a hard place, b/c alternate install CD was not detecting my keyboard (and live CD was not detecting my raid) ... eventually I got this situation resolved by making alternate CD recognize my keyboard correctly.  Everything went smoothly from then on.

---

### Post by rickyrockrat on 2008-10-05
Gents,
Here is an excellent manual on setting up a raid array:
[http://www.linuxconfig.org/Linux_Software_Raid_1_Setup](http://www.linuxconfig.org/Linux_Software_Raid_1_Setup)
Here it states that you can't boot if your / or /boot is raid 5.
Secondly, nobody seems to know how to kill a md array once created.  The trouble is your raid drives have information about the raid array on them, so to keep raid arrays from 'magically (re udev)' showing up, you need to temporarily rename the mdadm command. I renamed mine to mdadm.x

The situation is that my server root file system stated to fail out, and I was down to one disk, and for whatever reason, that one disk had ext3 errors on it, but the disk that was not showing up in the array was good, so I needed to e2fsck the bad array to fix the ext3 file system, and create a new temporary second drive until my new server was up (i.e. bailing wire & tape). 
The plan is to create 2 arrays, copy data from one to the other (so I don't copy the ext3 FS error), then delete one array, change my new mirror drive to the correct array, and place both back on my server. md0 in this case is my old drive, md1 the new, and the array on my server I am trying to fix is md0 (which is why md0 is my old drive). 

I created two separate arrays on my development box with the old drive and my new mirror, and  created 2 different arrays with one missing:

sudo mdadm --create /dev/md1 --level=1 --raid-disks=2 missing /dev/sdb1
(I did that for md0 & 1), then created a new ext3 fs on my new mirror, then mounted & copied the data from md1 to md0.  But now I want to kill md1, and all attempts to do that failed...until I renamed mdadm to mdadm.x.

So go through the steps to fail your drives out:
mdadm.x /dev/md1 -f /dev/sdb1
mdadm.x /dev/md1 -r /dev/sdb1
Then stop the array:
mdadm.x -S /dev/md1
Then remove the drives from the system (I used USB-ide adapter...much easier). Then add back the new drive, which has become /dev/sdb1, and re-create the md0 array using /dev/sdb1:
mdadm.x --create /dev/md1 --level=1 --raid-disks=2 missing /dev/sdb1
Then fail the drive & move it to the server. 

A further note, for those of you who want some of the structure of the software raid: The hard drive you can think of as a container. In the container you have to make partitions (not always, but for the most part you do) These partitions are also containers. Then normally you put a file system in these partition containers, but software raid adds one more level. You add a software raid container to the partition container, then finally the file system, which is another type of container...it holds information on the data stored on the drive. Not sure if that really helped or not....

---

### Post by ShiftyPowers on 2008-10-15
Question for all you RAID knowledgeable peeps out there.  I just finished creating my first RAID5 array out of 3 x 1TB WD Caviar drives.  The problem was that I had a lot of data that I could not get rid of before creating the array.  So what I did is that on each drive I created two partitions, say sda1 (100G) and sda2 (900G).  I spread my existing data over the 3x100G partitions and was left with 3x900G blank partitions.

I created a new RAID5 array on the 3x900G partitions and put an lvm logical volume on top of it running ext3.  

I then transferred all the data from the 3x100G partitions into the RAID array.

So far so good.

Now what I want to do is expand my RAID array to include the 3x100G paritions which are now empty.  

Can that be done easily?  Is there a way to EXPAND the underlying partitions that make up the raid array (i.e. make each 900G partition, 1TB)?  or do I just add the 3x100G partitions as separate drives to the existing array (so that the array will have 6 partitions underneath it)?

Thanks for your help,
Shifty

---

### Post by jpkotta on 2008-10-16
> **ShiftyPowers said:**
> Question for all you RAID knowledgeable peeps out there.  I just finished creating my first RAID5 array out of 3 x 1TB WD Caviar drives.  The problem was that I had a lot of data that I could not get rid of before creating the array.  So what I did is that on each drive I created two partitions, say sda1 (100G) and sda2 (900G).  I spread my existing data over the 3x100G partitions and was left with 3x900G blank partitions.

I created a new RAID5 array on the 3x900G partitions and put an lvm logical volume on top of it running ext3.  

I then transferred all the data from the 3x100G partitions into the RAID array.

So far so good.

Now what I want to do is expand my RAID array to include the 3x100G paritions which are now empty.  

Can that be done easily?  Is there a way to EXPAND the underlying partitions that make up the raid array (i.e. make each 900G partition, 1TB)?  or do I just add the 3x100G partitions as separate drives to the existing array (so that the array will have 6 partitions underneath it)?

Thanks for your help,
Shifty

I think you can expand partions at the end.  As in:
```
[900GB(preserved)][100GB(destroyed)] -> [1000GB]
```
You wouldn't want this:
```
[100GB(preserved)][900GB(destroyed)] -> [1000GB]
```

I know you won't want to add the 100 GB partitions to the existing array.  The size of the array is determined by the smallest device.

Since you wisely used LVM, why not make a new RAID5 array, make it a physical volume under LVM, add it to your existing logical volume, and expand the filesystem.

---

### Post by yzf600 on 2008-12-01
I was having problems creating my array. I would get this error message:

```
user@machine:~$ sudo mdadm --create /dev/md0 --level=1 /dev/sdb1 /dev/sdc1
mdadm: error opening /dev/md0: No such device or address

```
But the /dev/md0 node was getting created. Turns out my problem was the "md" kernel module was not installed. I ran this:

```
sudo modprobe md
```


And that fixed my issue. 

I hope this helps someone.

---

### Post by brojard on 2008-12-08
> **therufus said:**
> I have gutsy server version and can't get software RAID to work. mdadm isn't even installed. If I try to apt-get it, I get:

root@server:/usr/bin# apt-get install mdadm
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package mdadm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mdadm has no installation candidate

apt-get update works fine when I set everything to New Zealand servers (the Australian repository is always down - thanks for that Optus). I tried manually downloading mdadm and doing an install but make isn't even installed on gutsy. Installing make doesn't work either because of other dependencies, and further down the rabbit hole I go.

What am I doing wrong?

Is this still true? That I have to point to new zealand mirrors to get mdadm? How do I change my mirror to point to new zealand? 
Thanks

---

### Post by cyberkost on 2008-12-08
Nope, no need to point to New Zealand.  All you need to do is to install using *Alternate* CD (text-based install).

---

### Post by melsen on 2008-12-15
Can anyone tell me if this guide still is valid for Ubuntu 8.04 ?

Thanks.

---

### Post by crtlbreak on 2008-12-15
Hi Melsen 
yes - this guide is valid for 8.04 Hardy.
I have a RAID1 setup (redundancy purposes) which is well managed by mdadm.
Regards

---

### Post by Kissell on 2008-12-19
I am setting up a raid-6 array today, and in doing so I realized that when I was brand new to Ubuntu and switched over a windows software raid server to ubuntu and used mdadm I didn't specify partitions, I created the array with the entire disks...  it worked...  and has been working since...  but I noticed that nobody is doing it that way in any of the tutorials I've been browsing through.  Anyone know why?  are there any advantages/disadvantages to doing it either way?

what I'm talking about is when you do "mdadm --create /dev/md0" and specify the drives to create the array with, all the tutorials are showing to use /dev/sda1 /dev/sdb1 /dev/sdc1, ect...  they're creating the array using a linux raid autodetect partition from each drive...  the way I did it when I didn't know any better was to do not specify a partition but the whole disk, like /dev/sda, /dev/sdb, /dev/sdc...  either way I want to use the whole disk for the raid array...  so since I want to use the entire disk is there an advantage to go through the trouble of creating partitions on each disk and then creating the raid array using those partitions instead of the disk itself?  It seems to have worked okay on that server I did it to.

---

### Post by cyberkost on 2008-12-19
Kissell, one advantage I can think of is that I can make my /boot partition RAID1 (so that if a disk or two fail I can still start the system).  Then for / partition I can use RAID0 for speed and for /home I can use RAID10 for redundancy & speed ... that's not quite what I do, but the idea is to have different RAID levels for different partitions.

Also, with RAIDing entire disks (as far as I understand) you're limited to RAID1 (mirroring) unless you're using a controller of some kind ... but, I gather, most folks here are into software RAIDs ...

---

### Post by Kissell on 2008-12-19
That's a good point about the boot partition, I've never done that, and I am out of hard disk slots in this particular box, and the root file system drive/partition is non-redundant in any way (been a concern of mine)...  so I could replace it with another drive (if i'd use partitions in raid creation) to both expand my raid size and add redundancy to my root file system.  Thanks

Oh, but I did create a RAID5/6 with the whole drive without partitions...  It's been running all year...  the only "problem" i've seen, is that Ubuntu creates/mounts a "Software RAID Drive" inside "Computer" in the GUI, and it's unaccessible...  I can still mount the volume and use it, but it also creates this unusable "Software RAID Drive" on it's own, which is confusing to people, because you can't not have it, and if you click on it, it doesn't open the RAID volume.  I'm 99% sure it's doing this because I created the RAID with the whole drive instead of partitions.  I've reinstalled the OS serveral times (different versions) and it keep doing it, even rebuilt the array (using drive not partitions) and it still does it...  but I've created another server as a backup to this server and used partitions when creating that array and this problem didn't happen when I used the partitions to create the array...  not a big deal at all...  

Anyway, I was hoping maybe there was a more technical reason... the server that I created the array without using partitions, it has some issues, sometimes it kicks a drive out of the array for apparantly no reason, rebuilds itself, and the drives test out fine...  so I was hoping maybe this wasn't a problem with hardware and was a potentially a problem with how I created the raid?  probably not huh?  but I'm grasping at solutions on that one.

---

### Post by impossibilechecisiaquesto on 2009-02-13
Can i change an active RAID 10 array to a RAID 5 without losting data??

This is my mdstat

```
md3 : active raid10 sda7[0] sdd7[3] sdc7[2] sdb7[1]
      1410089088 blocks 64K chunks 2 near-copies [4/4] [UUUU]
      [===============>.....]  resync = 76.0% (1071866432/1410089088) finish=49.4min speed=113904K/sec
      
md2 : active raid5 sda6[0] sdd6[3] sdc6[2] sdb6[1]
      73231872 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      
md0 : active raid1 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      682624 blocks [4/4] [UUUU]
      
unused devices: <none>
massabuntu@massabuntu-desktop:~$ 
```

I want to change the level of /dev/md3 from raid10 to raid5, it's possible??

Thanks.

---

### Post by kpatz on 2009-02-13
> **impossibilechecisiaquesto said:**
> Can i change an active RAID 10 array to a RAID 5 without losting data??No... the way the data is stored is completely different in RAID 5 vs. 10.  You would have to back everything up, rebuild the array as RAID 5, and then restore.  Or build a new RAID 5 array out of another set of drives and then copy everything over.

RAID 10 is RAID 0 and 1 combined... 2 redundant pairs of striped drives.  RAID 5 is striped w/parity.

---

### Post by impossibilechecisiaquesto on 2009-02-13
Ya, i know :(
was only  hoping in the magic of the penguin.

So, i move the data, recreate the raid array, and return the data?

I have to format the current partitions or i can just build a different raid level?

---

### Post by taisao on 2009-02-22
Can I also use mdadm to create a raid0 array for use with windows vista? (dual boot)

---

### Post by Kissell on 2009-02-22
I've never heard of a way you could use mdadm to create an array that would be usable in windows.  I'd also like this, not necessary, but would be nice to have that option.  It'd also be nice to be able to use microsoft created software raid arrays inside linux, without having to destroy the data and recreate them.  

Unfortunately, the Microsoft OS has its own way of doing software raid, so it is not compatible with mdadm.  Although, theoretically I don't see any reason an app couldn't be made for microsoft OS that would let you use mdadm raid'd disks inside of windows.  Don't wait around for me to do it, cause I don't need it, more of a novelty for me, but it should be theoretically possible to do.

---

### Post by Adam Ryczkowski on 2009-03-14
I've acquired a new hdd and decided to make let my Ubuntu server be more robust by using raid 1 on root filesystem (together with /boot). No, I don't want to install the system from scratch - I just need to _migrate_ an existing one into RAID 1. Preferably I would not like to use the LiveCD - I simply don't have CD drive on the server. I can use minicd from the local net PXE boot, if that is necessary. 

I use ubuntu 8.04 with openvz kernel.

My root partition is small (20 GB) and the empty extra hard drive is much bigger. The root partition doesn't use LVM, and I believe it shouldn't, since I had problems in using LVM on top of Raid 1 on /boot and /.

I have physical access to the host, but very uncomfortable one. (The hard drive is already installed.) 

What should I do, to migrate the filesystem into RAID?

---

### Post by kpictjl on 2009-05-03
> **mgrusin said:**
> Great howto!  Please consider adding this to the community documentaion wiki.  There is currently nothing in there (at least that I could find) on the use of mdadm.

-MG

Someone has added what looks like a though howto for raid installation using server edition.

[URL="https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html"]https://help.ubuntu.com/9.04/serverguide/C/advanced-installation.html
[/URL]

---

### Post by hashbrowns on 2009-06-08
This may seem like a dumb question, but while using MDADM, I'd like to make sure that I can mirror a current 160G sata drive to another 160G sata drive. Neither device is the boot filesystem. Both of them are currently formatted ext3. One has about 50G of stuff on it, the other is empty.

All I want to do is make a RAID1 array out of the two of them, but I don't want to bother copying this data somewhere else right now beforehand (unless I need to). So, if someone can confirm for me that the instructions listed on the first page ([or here]("http://www.faqs.org/docs/Linux-HOWTO/Software-RAID-HOWTO.html#ss4.4")) for RAID1 will not damage the original data, that would be awesome. Thanks!

---

### Post by cyberkost on 2009-06-08
> **hashbrowns said:**
> This may seem like a dumb question, but while using MDADM, I'd like to make sure that I can mirror a current 160G sata drive to another 160G sata drive. Neither device is the boot filesystem. Both of them are currently formatted ext3. One has about 50G of stuff on it, the other is empty.

All I want to do is make a RAID1 array out of the two of them, but I don't want to bother copying this data somewhere else right now beforehand (unless I need to). So, if someone can confirm for me that the instructions listed on the first page ([or here]("http://www.faqs.org/docs/Linux-HOWTO/Software-RAID-HOWTO.html#ss4.4")) for RAID1 will not damage the original data, that would be awesome. Thanks!

The instructions your linked to are for raidtools, so they would not go well with "while using mdadm" part of your request.  I would locate mdadm specific instructions on how to accomplish what you want to accomplish.

You would be much better off backing up your data first before creating a raid, even if it's possible to create raid leaving 50GB of data in place (which I doubt, as mdadm needs to put a superblock somewhere on the drive which existing partition(s) will likely not allow to .. but I'm no expert here)

---

### Post by moe19790 on 2009-06-13
thanks for this great how to.. it was really helpful :)

---

### Post by cyberkost on 2009-06-18
I've got 4 320GB Seagate 7200.11 drives and have the following RAIDs (using mdadm) across them:```
/dev/md0  /boot  RAID0
/dev/md1  /      RAID10
/dev/md2  /home  RAID10
```
I'm monitoring the status of my RAIDs via conky (screenshot below) ... I've noticed a strange thing that after about a day of running /dev/sdb fails for both of my RAID10 devices:```

cyberkost@raidbox:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid10 sdb3[4](F) sdc3[3] sda3[1] sdd3[2]
      552779776 blocks 256K chunks 2 far-copies [4/3] [_UUU]

md1 : active raid10 sda2[1] sdc2[3] sdb2[4](F) sdd2[2]
      67103232 blocks 64K chunks 2 far-copies [4/3] [_UUU]

md0 : active raid1 sda1[1] sdc1[3] sdb1[0] sdd1[2]
      1052160 blocks [4/4] [UUUU] 

unused devices: <none>
```
This is also signalled by the HDD activity LED being constantly on (though no audible HDD activity).  If I try to add /dev/sdb[2,3] partitions back to their respective arrays, I get:```

cyberkost@raidbox:~$ sudo mdadm --add /dev/md1 /dev/sdb2
[sudo] password for kost: 
mdadm: Cannot open /dev/sdb2: Device or resource busy
```
The HDD activity LED goes off after about a day or two and I can add the partition back after that.  Alternatively, I can just reboot the machine and although it takes a while (2-3 hours) to come up, I can add the /dev/sdb[2,3] partitions back to their RAID devices when start-up is completed (the machine comes up with /dev/sdb[2,3] missing).

Originally I thought that the HDD that corresponds to /dev/sdb is going bad or the corresponding SATA cable/channel on the motherboar have become faulty, but from reading [post1](http://ubuntuforums.org/showpost.php?p=7294387&postcount=25) and [post2 it references](http://ubuntuforums.org/showpost.php?p=7220050&postcount=19) I started to suspect that it's the upgrade to Jaunty 9.04 that messed my mdadm RAID up.

My suspicions are further deepened by the following facts:
1. sudo smartctl -a /dev/sdb days the drive is fine (and the output for /dev/sdb looks VERY similar to that for the other 3 drives)
2. I first noticed the problem shortly after the upgrade to 9.04, I have not had a problem for a year prior to that.
3. /proc/mdstat used to list /sdaX /sdbX /sdcX /sddX for all 3 RAID devices prior to upgrade (ABCD order).  It now has ACBD for /dev/md[0,1] and BCAD for /dev/md2.
4. Looking at mdadm.conf I find UUID contsucts to look rather suspicious -- the last two blocks are the same for all /dev/md[1,2,3], while the first two are different:```

cyberkost@raidbox:~$ cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=4 UUID=20eef32f:87dc5eba:e368bf24:bd0fce41
ARRAY /dev/md1 level=raid10 num-devices=4 UUID=bacf8d29:0b16d983:e368bf24:bd0fce41
ARRAY /dev/md2 level=raid10 num-devices=4 UUID=67665d86:1cc558d5:e368bf24:bd0fce41

# This file was auto-generated on Thu, 01 Jan 2009 00:37:24 +0000
# by mkconf $Id$
```
I'd naively expect those UUID fields to be the same across all 3 RAID devices (e.g., if each block is a refence to a particular physical HDD) or be completely different (e.g., if each block is a reference to a particular superblock/parition).
5. Lastly, I see that mdadm.conf has the date of my upgrade to Ubuntu 9.04 Jaunty Jackalope:```

cyberkost@raidbox:~$ ls -la /etc/mdadm/mdadm.conf 
-rw-r--r-- 1 root root 874 2009-04-25 23:09 /etc/mdadm/mdadm.conf
``` ... and no, there's no backup file left :(

I checked if following the advice offered in [post2](http://ubuntuforums.org/showpost.php?p=7220050&postcount=19) is going to help, but it seems that it will not ... b/c the command returns the configuration that's already part of my 9.04 mdadm.conf```

cyberkost@raidbox:~$ sudo mdadm --examine --scan --config=mdadm.conf
[sudo] password for kost: 
ARRAY /dev/md0 level=raid1 num-devices=4 UUID=20eef32f:87dc5eba:e368bf24:bd0fce41
ARRAY /dev/md1 level=raid10 num-devices=4 UUID=bacf8d29:0b16d983:e368bf24:bd0fce41
ARRAY /dev/md2 level=raid10 num-devices=4 UUID=67665d86:1cc558d5:e368bf24:bd0fce41

```

PLEASE HE-E-E-E-ELP!!!

---

### Post by freakalad on 2009-07-13
kragen: thanks for a nice guide

---

### Post by jonfleck88 on 2009-08-11
Great guide, wish somebody would write a GUI frontend for mdadm. The only way that I've found to [setup RAID with a GUI is with the Linux installer]("http://www.optimiz3.com/installing-fedora-11-and-setting-up-a-raid-0-1-5-6-or-10-array/").

---

### Post by Gary.M on 2009-08-21
Just to add to this. I struggled as there were details that seemed unclear or left out. I worked in a virtual machine to figure out a procedure that worked for me. My notes are below...

========================================================================

&#8232;Creating Raid1 array using as example partitions /dev/sda5 and /dev/sdb5

&#8232;&#8232;First the partitions to be used are created as unformatted, raid flagged using system partition editor gui (gparted)

&#8232;&#8232;Reboot

&#8232;&#8232;Install mdadm

#&#8232;sudo apt-get install mdadm&#8232;(postfix chose local)

&#8232;&#8232;Reboot

&#8232;&#8232;Create raid array md0:

#&#8232;&#8232;sudo mdadm --create --verbose /dev/md0 --level=raid1 --raid-devices=2 /dev/sda5 /dev/sdb5&#8232;

&#8232;Check what you made:

#&#8232;&#8232;sudo mdadm --detail /dev/md0

&#8232;&#8232;Put a file system on it:

#&#8232;&#8232;sudo mkfs.ext3 /dev/md0&#8232;

&#8232;Check status

#&#8232;&#8232;cat /proc/mdstat&#8232;

&#8232;Enter output of below in file /etc/mdadm/mdadm.conf

#&#8232;&#8232;mdadm --detail --scan --verbose

&#8232;&#8232;mount /dev/md0 in fstab

&#8232;&#8232;example add this line to fstab: (create /mnt/raid folder )&#8232;&#8232;

dev/md0        /mnt/raid             ext3       defaults      0     0&#8232;

&#8232;reboot

================================================================

---

### Post by reise.pt on 2009-09-18
Just something that I dind't find reading through the documentation of mdadm.
A need to mount a RAID1 array readonly using the ubuntu livecd

If I execute the command
```
mdadm --assemble /dev/md0 /dev/dba1 /dev/sdb1
```
it changes any data on the disks or just creates the md0 device?

And if I execute the command afterwards
```
mdadm --readonly /dev/md0
```
It will put the radi in readonly so I can't change anything inside?

And after that can i just mount it somewhere with?
```
mount /dev/md0 /tmp/md0_mount
```

Thanks for any help.

---

### Post by JayRobert on 2010-01-26
> **Kissell said:**
> I've never heard of a way you could use mdadm to create an array that would be usable in windows.  I'd also like this, not necessary, but would be nice to have that option.  It'd also be nice to be able to use microsoft created software raid arrays inside linux, without having to destroy the data and recreate them.  

Unfortunately, the Microsoft OS has its own way of doing software raid, so it is not compatible with mdadm.  Although, theoretically I don't see any reason an app couldn't be made for microsoft OS that would let you use mdadm raid'd disks inside of windows.  Don't wait around for me to do it, cause I don't need it, more of a novelty for me, but it should be theoretically possible to do.

I just set up a dual-boot system with Karmic 9.10 and XP SP3.  I have a 40GB SSD with 12GB for XP and the rest for /boot, swap and /.

Then I have 3 - 640GB Western Digital drives with each entire drive set up on RAID5, and the entire RAID array as a volume group.  Over that I have a logical volume for (I thought) Windows, formatted in FAT32, and then logical volumes (acting as partitions) for /home, /opt, /tmp, /var formatted in ext3.  Root on the SSD is also its own logical volume.  I have encrypted the linux partitions except /boot, but not the FAT32 partitions.

Of course, I went ahead and set up a RAID5 assuming I'd be able to make Windows XP see it, but it only sees the three drives.  Is there any way to make XP see the LV with the FAT32 file system on it, or do I need to start over?

Could I load the apps I need onto the FAT32 LV using Wine?

If I have to start over, would I be better off giving one of the 640GB drives to Windows and making the other two into a RAID1 for Karmic?  Part of the reason I want to use Ubuntu is because it makes doing RAID and LVM pretty easy, and it also supports KVM.  What I really want to do is only run XP as a virtual machine on top of Karmic so that XP never sees the Internet (I really hate viruses), but I'll worry about figuring that out after I figure this part out.

Also, my mobo does have a fakeRAID capability, but after reading many posts I am hesitant to use that.

I'm not worried about losing data (yet), as this is a fresh machine with nothing to lose but the time I've put into the current setup.  I do want to have either a RAID1 or RAID5 mirror, since I plan to use this machine for development and maybe to do some consulting crap for the suits and don't want to lose data if I don't have to.

Also, I'm a newb again, so if you have a fix, I would request that it be fairly explicit if possible.  (By 'again,' I mean that I learnt Unix over 15 years ago so I could get to Usenet through my dial-up ISP's menu system (yes, I remember when 14.4k modems were the hot thing, and the </blink> command was fresh!), but then I got married, raised a kid, got a series of tiresome management and analyst jobs that involved Windows only, and I have almost entirely forgotten the command line.  I want to learn it, though, so I can ultimately get the 12GB of malware off the SSD for good. ;)

Long post - sorry.  Any help is appreciated.

---

### Post by crtlbreak on 2010-01-27
jayrobert
LVM is not for windows - as I am sure you know by now.
EXT and VFAT are chalk and cheese (or more correctly cheese and chalk?)- but I am sure you could have told me that.
Dont use fakeraids - they are BIOS capable simulations of real raid. The only software raid that really works is mdadm.
RAID5 EXT3 vs RAID5 DOS (VFAT) are again cheese and chalk - not to have one mistaken for the other.
The best (IMHO) would be to 

[LIST=1]
[*]ditch windoze boot options completely and use virtualbox or vmware equivalent with windows installed on a designated partition within the virtual app
[*]dual boot causing you to install windoze first (which would mean you cannot use software raid options of debian)
[/LIST]
There are two edges to the sword ..... :D
Hope this helps?

---

### Post by Fafler on 2010-03-03
I'm going to build a encrypted RAID 5 array for data (no OS) with 3 1.5 tb drives. Do i just do it like that? Make array with mdadm --create..., put luks on it with[FONT=monospace] [/FONT]cryptsetup luksFormat /dev/md0 and finally mkfs.ext4... is it really that simple or are there any caveats i haven't thought of?

I want to be able to add another drive or two in the future and grow the array accordingly. Is that possible with this method? Also LVM still comes to mind, but i don't really see why i should need it, as i only need a single partition on the array.

---

### Post by Fafler on 2010-03-09
So i received the drives yesterday, and i really hope you guys can help me on this one, 'cause by now i'm out of ideas. mdadm only adds 2 out of 3 drives, no matter what i do.

```
~# mdadm --create /dev/md0 --level=5 --raid-devices=3 --size=max /dev/sda1 /dev/sdb1 /dev/sdc1
raid5: raid level 5 set md0 active with 2 out of 3 devices, algorithm 2
mdadm: array /dev/md0 started
~# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4]
md0 : active raid5 sdc1[3] sdb1[1] sda1[0]
1285199744 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]

```

So far i've tried; changing SATA cables, changing the order of the drives, changed from Ubuntu 9.10 to Debian 5.04, moved the drives to another motherboard, tried with and without partitioning the drives and i even tried making a partition on each drive with about 50% of the total space.

The drives can be read and written without any problems and i can even make RAID 1 array with all three drives for a total of 4.5 tb without and troubles at all. But no matter what, i can't get a working RAID 5 array.

I really hope someone here is able to help me out.

BTW; the motherboards i've tried are based on Intel 965 and G35, each with a C2D processor and a 32 bit kernel. I think both of them carry the ICH9 south bridge. The drives are all Western Digital WD15EARS.

---

### Post by bsmith1051 on 2010-03-09
Maybe it's defaulting to the 3rd drive being a spare? md0 shows all 3 partitions.  What does the mdadm detail show?

> sudo mdadm --query --detail /dev/md0

---

### Post by olesk on 2010-04-15
I've been setting up a RAID 10 with fours disks and I am about to add two more to it. The two new disks are smaller than the ones already in the set, but as I want them to be another RAID1 set that can then be added to the stripe, it should be irrelevant. (It consists of two RAID 1 mirrors, which are then striped - all in one go, i.e. true RAID 10 with only one raid device, not raid 0+1 - the terminology gets a little confusing sometimes).
 
I use mdadm v2.6.7.1 on Ubuntu 9.10 with a 2.6.31-21-generic kernel.
 
 
 
 
 
 
 

I was hoping to clear up a couple of points before beginning to add two more disks:[LIST=1]
[*]I essentially used *mdadm -v --create /dev/md0 --level=raid10 --raid-devices=4 /dev/sdb1 /dev/sdc1 etc... *to build the array. Thus I do not know which disk pairs are mirrored (RAID1 pairs) - it could in theory be any combination of my 4 disks. Is there any way of finding out? Neither */proc/mds*tat nor *mdadm* says anything about this (see below)
[*]If I simply add another disk (which is a smaller size than the existing ones) using *mdadm*, will it be listed as hot spare?
[*]If I finally add the second new disk, will *mdadm* realize that I now have two spares, build a mirror (RAID1) pair of them and add them to the RAID0 stripe, in effect expanding my RAID10 array, or do I have to do some sort of manual process here? *mdadm* does after all know that I am adding them to a RAID10 array...
[/LIST]Below is the output from cat /proc/mdstat (before adding any of the two new disks):
[INDENT]*Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]*
*md0 : active raid10 sde1[3] sdb1[0] sdd1[2] sdc1[1]*
*2930271872 blocks 64K chunks 2 near-copies [4/4] [UUUU]*
 
*unused devices: <none>*
 
[/INDENT]**Update**: *mdadm --grow --help* doesn''t mention raid10 at all, which perhaps means either that a) RAID10 cannot be grown, or b) I need a newer version of *mdadm*. It seems this has been discussed [before]("http://ubuntuforums.org/showthread.php?t=900546&highlight=grow+raid10"), but perhaps this has changed lately?

---

### Post by BMWolf on 2010-04-15
***EDIT: I changed fsck checking to 0 in fstab and everything boots. Is this required for raid? Problem solved, I guess.***

Sorry for such a long winded post, but I'm at my wits end,**PLEASE HELP!**

Here go's...
I've recently built a new machine and needed to move /home and everything in it from one raid1 array to a new larger raid 1 array. To make sure I didn't lose any data by accident, I removed one of the working drives, set it aside, stopped the array and mounted it's partition manually. I'm using Server 9.10 64-Bit and doing everything via ssh.

I then placed one of the new soon to be RAIDed drives in, partitioned the drive, and setup the new array. 'sdc1' is the new disk and 'missing' is the mounted old disk(sdb1):
```
mdadm --create /dev/md0 --level=1 --raid-disks=2 missing /dev/sdc1
```

I then formatted /dev/md0
```
sudo mkfs.ext4 /dev/md0
```

...and copied files over to it following this tutorial([link]("http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/")). I used sudo su because the files would not copy due to permissions. 
```
cd /home
sudo su
find . -depth -print0 | cpio --null --sparse -pvd /mnt/NEW_HOME
```

I shutdown removed the old smaller '/dev/sdb', added the new larger drive, powered on, and added the new drive to the array(after partitioning and formatting it). 
```
sudo mdadm --add /dev/md0 /dev/sdb1
```

It synced the drives. I then checked the files and they were all there and in working order and both drives were in active sync. I then changed fstab to use the new array as '/home'.
```
bryan@NAS:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0

# / was on /dev/sda1 during installation
UUID=6d1a79fe-7431-4a14-b10c-a1bad83e566d       /       ext4    errors=remount-ro       0       1

# swap was on /dev/sda5 during installation
UUID=fef142b2-2bd9-4d96-9384-770c409a8618       none    swap    sw      0       0

#CD Rom
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8       0       0

#data RAID1 array
UUID=ef49f27c:490d5346:cced5de7:ca715931        /home   ext4    nodev, nosuid        0       2

```

Then I reboot.

After the reboot I tried to log back on via ssh and the server would not connect. So I connected it to a monitor and it said it was waiting for /home UUID=ef49f27c:490d5346:cced5de7:ca715931 to come online. I entered the rescue shell, commented out the /home entry in fstab and rebooted. The server came up again but then complained that it couldn't chdir to /home as would be expected.

I check the array to make sure it is in working order; it's not:
```
bryan@NAS:/$ cat /proc/mdstat
Personalities :
md0 : inactive sdc1[1] sdb1[0]
      1953519872 blocks

unused devices: <none>

bryan@NAS:/$ dmesg | tail
...
[  293.858825] EXT4-fs (md0): unable to read superblock
```

So I stop the array and try to reassemble it:

```

bryan@NAS:/$ sudo mdadm --stop /dev/md0
mdadm: stopped /dev/md0

bryan@NAS:/$ sudo mdadm --assemble --scan
mdadm: /dev/md0 has been started with 2 drives.

bryan@NAS:/$ cat /proc/mdstat
Personalities : [raid1]
md0 : active raid1 sdb1[0] sdc1[1]
      976759936 blocks [2/2] [UU]

unused devices: <none>

```

OK... Then:
```
bryan@NAS:/$ sudo mount -t ext4 /dev/md0 /home

bryan@NAS:/$ ls /home/
bryan  cupsys  lost+found  samba
```

*EDIT: Forgot to mention that both drives are of type Linux_Raid_Autodetect(fd).*

It works, so what the F is going on and what did I screw up? The drives are WD10EARS. These drives are not certified for RAID use, but they work without error once I do the above steps, so what's the deal? Once I reboot I have to do it all again.

Are the drives junk? Did I screw up by issuing the original commands as sudo su? 

Which leads to my second question:
When looking at the ownership of most of the folders on these drives, root is listed as the owner and the group. Is this right? Wouldn't USER normally be the owner of /home/USER and all it's files?

Thanks in advance!!!

---

### Post by LiLoather on 2010-09-04
I created a 3 disk Linux software RAID 10 array to install Ubuntu 10.04 server on.  Everything seemed to go well and it all seems to be working, but doing a --query of the third disk brings up the following report:

tony@Debbie:~$ sudo mdadm --query /dev/sdc1
/dev/sdc1: is not an md array
/dev/sdc1: device 2 in 3 device mismatch raid10 /dev/md0.  Use mdadm --examine for more detail.
tony@Debbie:~$ sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 6e735543:3dc59b4b:a8204fbe:f33447b2
  Creation Time : Sat Sep  4 02:18:19 2010
     Raid Level : raid10
  Used Dev Size : 9765376 (9.31 GiB 10.00 GB)
     Array Size : 9765376 (9.31 GiB 10.00 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Sat Sep  4 13:25:59 2010
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 0 - expected 8a517f27
         Events : 40

         Layout : near=2, far=1
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
tony@Debbie:~$ 


What does the "device 2 in 3 device mismatch" and the "Checksum : 0 - expected 8a517f27" mean?  Does anything need reconfiguring or is this array fatally flawed?

---

### Post by AllGamer on 2011-03-15
I keep getting this error:

```
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: /dev/sdd has no superblock - assembly aborted

```
even after a successful creation, everytime after a reboot, and i try to re-assemble it manually :confused:

```
sudo mdadm --assemble /dev/md0 /dev/sdb /dev/sdc /dev/sdd /dev/sde
```

The part that it complains about the missing superblock or the device in use changes everytime i reboot the machine

If i destroy the array and create a new one, it will work for as long as i keep the server running.

I want to make sure the RAID5 is mountable everytime after a reboot to automate the mounting process

I'll welcome any hints or info you can provide

thank you

---

### Post by crtlbreak on 2011-03-15
Hi AllGamer
In your assembly process 

> **AllGamer said:**
> 

```
sudo mdadm --assemble /dev/md0 /dev/sdb /dev/sdc /dev/sdd /dev/sde
```



Shows you as trying to assemble a RAID5 with spare?
You are using the device /dev/sdx as opposed to the partitions /dev/sdxn - where n is the number.

---

### Post by AllGamer on 2011-03-15
> **crtlbreak said:**
> Hi AllGamer
In your assembly process 



Shows you as trying to assemble a RAID5 with spare?
You are using the device /dev/sdx as opposed to the partitions /dev/sdxn - where n is the number.

you mean the partitions?
like /dev/sdbp1?

the entire drive is used for the raid.

anyways i think i might have found what was causing the problem

when i did a mount, to list all the devices it shows this

```
/dev/sde1 on / type ext4 (rw,errors=remount-ro,user_xattr,commit=0)

```

that should definitely not be there, seems like i still got some remnants of the previous LVM RAID trials.

---

### Post by nathan58 on 2011-03-18
I am totally agree with all the views under that forum. make sure you are root and that you and the backup file are in the root of the filesystem.

---

### Post by TheR on 2011-03-18
> **AllGamer said:**
> you mean the partitions?
like /dev/sdbp1?

the entire drive is used for the raid.

anyways i think i might have found what was causing the problem

when i did a mount, to list all the devices it shows this

```
/dev/sde1 on / type ext4 (rw,errors=remount-ro,user_xattr,commit=0)

```

that should definitely not be there, seems like i still got some remnants of the previous LVM RAID trials.

Try to wipe out beginning of disk with dd.

by
TheR

---

### Post by Azyx on 2011-04-25
Hey I have for now 2 questions.

A) Under 5) It says:
"The partitioner should be straightforward enough to use - when you  create a partition which you intend to use in a raid, you need to change  the type to [COLOR=Red]**"Linux RAID Autodetect"**[/COLOR]."

I can't find it, It is the same as flag for RAID in Gparted?

B) I have problems with swifting sda, sdb, sdc, sdd, sde. May I or do I need to assign my partition in mdadm with UUID or does mdadm recognise the disk in the array automatically?

/Cheers

---

### Post by Azyx on 2011-04-25
> **AllGamer said:**
> you mean the partitions?
like /dev/sdbp1?

the entire drive is used for the raid.

anyways i think i might have found what was causing the problem



As I have understand it, mdadm use partions even if the hole disk are a partition, and not as preferred in ZFS, the disks.

/Cheers

---

### Post by AllGamer on 2011-04-25
> **TheR said:**
> Try to wipe out beginning of disk with dd.

by
TheR

update...

(i totally forgot i posted a question here :p )

So, yes after many trials & errors, i decided to wipe each driver again with **dd** and re-kill the head of each disk, that seems to have finally cleanup the mess the LVM left behind.

i've got the RAID5 up and running + automatically mounting everytime it boots now without any error

added the RAID5 volume UUID info into /etc/fstab so that it will automatically mount itself on boot



**On a site note:**

Now that I have both RAID5 via **mdadm** running vs. RAID5 hardware (cheap **softRAID** controllers) in the same machine, I can say with certainty that the softRAID hardware version of RAID5 has faster performance.

The speed difference is only noticeable on sustained Massive data transfers... like when you transfer all the content from one RAID5 to another RAID5.

Otherwise you'll not really be able to appreciate the difference if it's just your regular samba file sharing purpose or web server access.

in my setup all 4 separate set of RAID5 were composed of 4 Seagate 1.5TB 7200rpm, so for a total of 16 HDD of the same brand & speed

4 are attached to the motherboard (Intel ich9) running **mdadm** RAID5
4 are attached to rr1740 using the manufacture drivers + RAID management software
4 are attached to rr264x1 using the manufacture drivers + RAID management software
4 are attached to rr264x4 using the manufacture drivers + RAID management software

the ones that were on **softRAID** consistently completed massive data transfer (writes; commit to disk) faster than the **mdadm** RAID5 setup.

which now have been re-assigned to mirror the rr1740 instead, as a backup for catastrophic failure.




***** Off Topic *****

the rest of the server spec:

8GB DDR2 Corsair stock speed
stock on-board intel video
Intel Pentium D 820 (2.8 GHz Dual Core LGA775) stock speed
on-board intel 100 Mbps NIC (as backup connection)
2 x Intel PRO/1000 MT Dual Port Server Adapter (9k jumbo frame capable)

that makes 4 separate 1 Gbps connections, i set it up as a 2x2 (9k jumbo frame enabled via Cisco Manage Switches), so basically both ports in each NIC works as 2000 Mbps (2 Gbps) + the 2nd NIC as a fail over/load balancing in case the anything happens to the other NIC

of the 4 RAID setup, only 2 are accessible to the users, as the other 2 RAID are used to mirror the other 2 RAID

in a way you can imagine a RAID1 mirror for RAID5 of this server :D

and on a separate server there's yet another redundant RAID5 backup for this server's RAID5s data.

The only thing that is non-redundant in this server is the PSU, which i had to replace just a few days ago already due to overload :p which was no surprise as it was originally a 600W PSU running all that stuff + all the cooling fans

Now the new PSU is a 1200W, which gives ample room for expansion with aprox 350W free, vs 250W overboard on the old one.

So, the old PSU was pretty decent to have been able to push 250W over its limit for 2 years straight 24/7 :p

the power failure only damaged one of the RAID5, which was easily fixed by running a verification scan with the HighPoint Management software.

which incidentally the partial death of the 600W PSU was not its own fault, as the real problem was caused by a dying battery on the APC 1500VA that was running the whole thing.

which according to APC diagnostic... it died prematurely due excessive heat, which i would not deny; that server room is like a dry sauna :D

---

### Post by dedede12 on 2011-09-23
nice) are there any other helps? A RAID-1/5 HOWTO for example)




-------------[shoutbox script]("http://www.wilsontechnology.com/")

---

### Post by Azyx on 2011-11-04
Under point 7 it says:
......

     ```
mdadm --create /dev/md0 --chunk=4 --level=0 --raid-devices=2 /dev/sda1 /dev/sdb1
```will create a raid0 array /dev/md0 formed from /dev/sda1 and /dev/sdb1 with chunk size 4.
.........


I have problems with changing /dev/sd[a,b]1. Is it possible to use UUID# instead of /dev/sd[a,b]1 partitions ?

/Cheers

PS. I have seing the man-page [http://linuxmanpages.com/man8/mdadm.8.php](http://linuxmanpages.com/man8/mdadm.8.php) ,but I have problem to understand where you for instance shall put -u --userid. I have problem to understand man-pages :(

---

### Post by sdavmor on 2012-03-08
> **dedede12 said:**
> nice) are there any other helps? A RAID-1/5 HOWTO for example)




-------------[shoutbox script]("http://www.wilsontechnology.com/")

A RAID5 or RAID6 HOWTO would be huge....

Here's were I am tonight. I have two RAID arrays on a system.  The first is RAID1 and supports /boot swap / and /home.  The second is RAID6 and supports everything else.  It currently has 4 3TB drives.  I have 3 more sitting in the tower and want to add them to the RAID6 array.

I was using Disk Utility to try to add these three drives but it doesn't seem to want to do it with the array up and running. When I take the array down I'm denied access to the array controls in "Edit Components" so I can't tell it to add drives.

I remove the partitions from the 3 drives (initialized as GPT). Then I go into "Edit Components".  I see the three drives. I am told they each have no partitions and each have 3TB available for use.

I go to add one drive.  I click the box to add it and the click "Expand". I authenticate then get this message:

Error expanding RAID Array.
An error occurred while performing on operation on "hitchcock RAID6" (6.0 TB RAID-6 Array): The operation failed

Detail information says:

Error expanding array: helper script exited with exit code 1:
mdadm: added /dev/sdc1
mdadm: Need to backup 6144K of critical section..

I now see the new drive in the RAID6 array as a spare. Well...I now see all three spare drives that I want to activate.

What am I missing here?  If I can't figure this out I guess it will be a reboot into a run-level 1 root shell to use mdadm.  Any pointers from those of you who are quite familiar with using Disk Utility and RAID arrays? I'm now at the bang-my-head-on-the-wall point.:confused:

---

### Post by sdavmor on 2012-03-08
I'm going to answer my own query. I finally figured out what was going on. Digging further into the error message output I kept looking at the issue of bitmap removal. Why was this necessary? And removal from where? I had an epiphany 30 mins ago reading this mdadm man page:

[http://linux.die.net/man/8/mdadm](http://linux.die.net/man/8/mdadm)

Which then led me to search online and read this page which has some good information about speeding up working with Linux software raid:

[http://www.coderetard.com/2011/02/01/howto-speed-up-linux-software-raid-building-and-re-syncing/](http://www.coderetard.com/2011/02/01/howto-speed-up-linux-software-raid-building-and-re-syncing/)

What I wound up doing was removing the bitmap from the array with this shell command:

sudo mdadm --grow --bitmap=none /dev/md127

I was then able to expand the array using Disk Utility, though I could have done it from a terminal shell with this command:

sudo mdadm --grow /dev/md127 --raid-devices=7

Once I'm done with the reshaping I'll put the bitmap back after figuring out what it should optimally be. The RAID6 array is reshaping right now with the three new 3TB drives added. In a few hours I will seal it all back up. In the meantime I'm off to Fry's Electronics to return the extra pieces of hardware that I don't need.

The final configuration of the media center server will be a 8gb DDR3 machine with a AMD Phenom II X4 quad-core processor. It will have a RAID1 mirror of 2*2TB drives for boot, swap, / and home. And 7*3TB drives for the RAID6 array. 4 will be on the mobo along with the boot mirror. The other 3 drives will be on a 4port SATA card. 6 drives are mounted in the 3.5" drive bays and the other 3 plus the PATA DVD burner are mounted in the 5.25" drive bays. 4 big fans, plus 1 giant fan and a 1200watt power-supply. Hopefully I'm now done tinkering with it and can get back to software and music.

---

### Post by mintfrish on 2012-09-25
Hi, 

this is a great idea but unfortunately I am not able to get it to work. 
My idea is having one Linux System alongside one Windows 8 system. I don't want no dual boot. I just want to boot into one of the systems by choosing the boot priority in UEFI (bios).

This is what I tried. I created partitions with a gparted in "the linuxmint-13-cinnamon-dvd-64bit.iso" live system. Which would look like in screens attached. Then I did the following (md0 for root and md1 for /home)
```
sudo mdadm --create /dev/md0 --chunk=4 --level=0 --raid-devices=2 /dev/sda5 /dev/sdb5 
mdadm: /dev/sda5 appears to contain an ext2fs file system
    size=4096000K  mtime=Thu Jan  1 00:00:00 1970
mdadm: /dev/sdb5 appears to contain an ext2fs file system
    size=4096000K  mtime=Thu Jan  1 00:00:00 1970
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.
```and

```
sudo mdadm --create /dev/md1 --chunk=4 --level=0 --raid-devices=2 /dev/sda6 /dev/sdb6 
mdadm: /dev/sda6 appears to contain an ext2fs file system
    size=10240000K  mtime=Thu Jan  1 00:00:00 1970
mdadm: /dev/sdb6 appears to contain an ext2fs file system
    size=10240000K  mtime=Thu Jan  1 00:00:00 1970
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md1 started.
```After that I started "Install Linux Mint" to install the system. But first I did
```

sudo mkfs.ext4 /dev/md0
``` ```
sudo mkfs.ext4 /dev/md1
``` ```
sudo mkfs.ext4 /dev/sda1
```I chose manual install and changed md0, md1 and sda1. md0 and md1 to format as ext4 again with mount points for root and /home. sda1 I formatted with ext2 and mount point /boot. Which looked kinda like the screen attached. 


[[IMG]http://www.abload.de/thumb/screenshotfrom2012-09sxjhv.png[/IMG]]("http://www.abload.de/image.php?img=screenshotfrom2012-09sxjhv.png")[[IMG]http://www.abload.de/thumb/screenshotfrom2012-09uakdd.png[/IMG]]("http://www.abload.de/image.php?img=screenshotfrom2012-09uakdd.png")[[IMG]http://www.abload.de/thumb/screenshotfrom2012-094ljxe.png[/IMG]]("http://www.abload.de/image.php?img=screenshotfrom2012-094ljxe.png")




When I do it like this I get

```
Executing 'grub-install /dev/sda1' failed.

This is a fatal error
```Could you guys please help me out ?

---

### Post by Cavsfan on 2012-09-25
> **mintfrish said:**
> 

```
Executing 'grub-install /dev/sda1' failed.

This is a fatal error
```Could you guys please help me out ?

Not sure about the rest of the problem but, **sudo grub-install /dev/sda** would be the correct command not **sda1.**

---

### Post by mintfrish on 2012-09-25
Okay please step by step. I simplified the partitions a little bit so that I would have only one mdadm RAID /dev/md0 for root without a separate /home partition.

After manipulating with gparted fdisk -l gives me this now>

```
mint@mint ~ $ sudo fdisk -l

Disk /dev/sda: 16.0 GB, 16001269760 bytes
255 heads, 63 sectors/track, 1945 cylinders, total 31252480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00017dbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      309247      153600   83  Linux
/dev/sda2          309248    22247423    10969088   83  Linux
/dev/sda3        22247424    31252479     4502528    5  Extended
/dev/sda5        22249472    31150079     4450304   82  Linux swap / Solaris

Disk /dev/sdb: 16.0 GB, 16001269760 bytes
255 heads, 63 sectors/track, 1945 cylinders, total 31252480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d958a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    21940223    10969088   83  Linux
/dev/sdb2        21940224    31252479     4656128    5  Extended
/dev/sdb5        21942272    30842879     4450304   82  Linux swap / Solaris

Disk /dev/sdc: 31.6 GB, 31641829376 bytes
255 heads, 63 sectors/track, 3846 cylinders, total 61800448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

```So my next step in this case would be:

```
mdadm --create /dev/md0 --chunk=4 --level=0 --raid-devices=2 /dev/sda2 /dev/sdb1
```And right after I should be able to run the installation? I would choose manual installation and put md0 as root mounting point. I leave everything else alone except that i choose /dev/sda as 'device for boot loader' installation and that's it ?

[COLOR=Red]..continued[/COLOR]:

```
mdadm: /dev/sda2 appears to contain an ext2fs file system
    size=10969088K  mtime=Thu Jan  1 00:00:00 1970
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=10969088K  mtime=Thu Jan  1 00:00:00 1970
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.
``````
sudo fdisk -l

Disk /dev/sda: 16.0 GB, 16001269760 bytes
255 heads, 63 sectors/track, 1945 cylinders, total 31252480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00017dbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      309247      153600   83  Linux
/dev/sda2          309248    22247423    10969088   83  Linux
/dev/sda3        22247424    31252479     4502528    5  Extended
/dev/sda5        22249472    31150079     4450304   82  Linux swap / Solaris

Disk /dev/sdb: 16.0 GB, 16001269760 bytes
255 heads, 63 sectors/track, 1945 cylinders, total 31252480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d958a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    21940223    10969088   83  Linux
/dev/sdb2        21940224    31252479     4656128    5  Extended
/dev/sdb5        21942272    30842879     4450304   82  Linux swap / Solaris

Disk /dev/sdc: 31.6 GB, 31641829376 bytes
255 heads, 63 sectors/track, 3846 cylinders, total 61800448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    61800447    30899200    c  W95 FAT32 (LBA)

Disk /dev/md0: 22.5 GB, 22464675840 bytes
2 heads, 4 sectors/track, 5484540 cylinders, total 43876320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 4096 bytes / 8192 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

---

### Post by Cavsfan on 2012-09-25
> **mintfrish said:**
>  I leave everything else alone except that i choose /dev/sda as 'device for boot loader' installation and that's it ?

I don't know RAID configurations but, the above statement would be true. Grub has to be installed on sda not sda1, etc.

---

### Post by mintfrish on 2012-09-25
> **Cavsfan said:**
> Not sure about the rest of the problem but, **sudo grub-install /dev/sda** would be the correct command not **sda1.**

Okay I tried it by using /dev/sda. But still I get an error message during installation.


```
Executing 'grub-install /dev/sda' failed.

This is a fatal error.
```What do I do wrong with the boot partition? Can I create it manually after installation procedure?

[[IMG]http://www.abload.de/thumb/screenshotfrom2012-09wpqi9.png[/IMG]]("http://www.abload.de/image.php?img=screenshotfrom2012-09wpqi9.png")

---

### Post by mintfrish on 2012-09-25
Hmm after checking fdisk -l again 

```
sudo fdisk -l

Disk /dev/sda: 16.0 GB, 16001269760 bytes
255 heads, 63 sectors/track, 1945 cylinders, total 31252480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00017dbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      309247      153600   83  Linux
/dev/sda2          309248    22247423    10969088   83  Linux
/dev/sda3        22247424    31252479     4502528    5  Extended
/dev/sda5        22249472    31150079     4450304   82  Linux swap / Solaris

Disk /dev/sdb: 16.0 GB, 16001269760 bytes
255 heads, 63 sectors/track, 1945 cylinders, total 31252480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d958a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    21940223    10969088   83  Linux
/dev/sdb2        21940224    31252479     4656128    5  Extended
/dev/sdb5        21942272    30842879     4450304   82  Linux swap / Solaris

Disk /dev/sdc: 31.6 GB, 31641829376 bytes
255 heads, 63 sectors/track, 3846 cylinders, total 61800448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    61800447    30899200    c  W95 FAT32 (LBA)

Disk /dev/md0: 22.5 GB, 22464675840 bytes
255 heads, 63 sectors/track, 2731 cylinders, total 43876320 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 4096 bytes / 8192 bytes
Disk identifier: 0x00014576

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1              64    43875055    21937496   83  Linux

```I tried this:

```
sudo mkdir /home/tempo
``````
sudo mount /dev/md0p1 /home/tempo
``````
sudo grub-install --root-directory=/home/ubuntu/tempo /dev/sda1
```gave me 
```
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /home/ubuntu/tempo/boot/grub (is /dev mounted?).
```
:confused:

---

### Post by Cavsfan on 2012-09-26
Sorry, this is out of my league. Hopefully **Old Fred** or someone with grub knowledge will come along and help.

---

### Post by greenrubberducky on 2012-09-28
All I can say is YESSSSSSSSSSS!!!!!!!

I have a home storage server, self-made. AsRock Intel mobo, dual-core CPU, and 4 western digital 1TB drives in a RAID 5 config. It uses Ubuntu server 11.04 (or did...). It was awesome. Great little box. Then we had a good power surge during a storm, and the board died. Replaced the board, couldn't get another one for the LGA775 chip with 5-6 SATA inputs, so I had to start with a new base HD. 

Anyways, I followed the instructions on the first page, got a live CD environment going, and simply said 'sudo mdadm --A'. Ubuntu just figured out the 4 drives were a raid array, assembled them, I mounted them and BANG!

I'm really happy right now. I do love Linux.

---

### Post by mintfrish on 2012-10-05
> **Cavsfan said:**
> Sorry, this is out of my league. Hopefully **Old Fred** or someone with grub knowledge will come along and help.

Okay thank you very much mate. Event though I couldn't install the desired distro I was able to install ubuntu alternate. But still I run into problems here concerning the double swap space. 

When I enter 

```
swapon -s
```

I get 
 
```
Filename				Type		Size	Used	Priority
/dev/mapper/cryptswap2                  partition	4450300	0	-1

```

My fstab looks like this

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=86f44b73-1822-4f25-8482-03ce6e84184a /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=8a4ca2d8-dc7b-44e5-9448-e675d83120d6 /boot           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
#UUID=76cb7d4a-9fd7-4746-b690-b8a9a2663122 pri=1            swap    sw              0       0
# swap was on /dev/sdb5 during installation
#UUID=f0b88015-6906-4ec3-a178-1aa19a4cd7f5 pri=1            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/cryptswap2 none swap sw 0 0
```

and fdisk is the following

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 Köpfe, 63 Sektoren/Spur, 14593 Zylinder, zusammen 234441648 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0xc1a472a2

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *        2048   234440703   117219328    5  Erweiterte
/dev/sda5            4096   234440703   117218304   83  Linux

Disk /dev/sdb: 16.0 GB, 16001269760 bytes
255 Köpfe, 63 Sektoren/Spur, 1945 Zylinder, zusammen 31252480 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0x00017dbe

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *        2048      309247      153600   83  Linux
/dev/sdb3          311294    31150079    15419393    5  Erweiterte
/dev/sdb5        22249472    31150079     4450304   82  Linux Swap / Solaris
/dev/sdb6          311296    22249471    10969088   fd  Linux raid autodetect

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

Disk /dev/sdc: 16.0 GB, 16001269760 bytes
255 Köpfe, 63 Sektoren/Spur, 1945 Zylinder, zusammen 31252480 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0x000d958a

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdc1            2048    21940223    10969088   fd  Linux raid autodetect
/dev/sdc2        21942270    30842879     4450305    5  Erweiterte
/dev/sdc5        21942272    30842879     4450304   82  Linux Swap / Solaris

Disk /dev/md0: 22.5 GB, 22463643648 bytes
2 Köpfe, 4 Sektoren/Spur, 5484288 Zylinder, zusammen 43874304 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Festplattenidentifikation: 0x00000000

Festplatte /dev/md0 enthält keine gültige Partitionstabelle

Platte /dev/mapper/cryptswap2: 4557 MByte, 4557111296 Byte
255 Köpfe, 63 Sektoren/Spur, 554 Zylinder, zusammen 8900608 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0x084f234d

Festplatte /dev/mapper/cryptswap2 enthält keine gültige Partitionstabelle
```

So actually my swap partitions are /dev/sdb5 and /dev/sdc5. How would I set this up right so I can use both partitions ?

---

### Post by Cavsfan on 2012-10-05
Note the partitions and UUIDs from **sudo blkid**.

Edit fstab:
**gksu gedit /etc/fstab** and correct the UUIDs and/or delete the incorrect entries.

You should have just **one** ext4 and **one** swap. 
It is listing several which is probably the problem.

Correct the fstab entries, save it and reboot.

Any time you re-install a system or change a swap file, it "remembers" the old UUID and fstab must be edited.

Here is what my fstab looks like on Quantal:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=08562c83-a132-4997-b215-a3a1d2e076bb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=0416f9e3-4d20-4a9e-989f-b361bf7bbfc2 none            swap    sw              0       0
```

---

### Post by mintfrish on 2012-10-06
Thanks mate. I followed your instructions and commented everything off that was unnecessary. But why only one swap partition? Isn't it the intention of the op to create 2 swap partitions ? 
Anyways, first I had to get rid of the cryptswap. After doing that I created the 2 swap partitions with mkswap /dev/sdb5 and /dev/sdc5. With that done I got the UUID's and I could paste them into fstab. I set them both with pri=1. 

Theese are the two new swap partitions in fstab
```
#swap manuell hinzugefügt
UUID=eb377be2-1b3f-414c-bed3-92c28bfafeff pri=1            swap    sw              0       0
#swap manuell hinzugefügt
UUID=1aed75da-7159-43b4-9b1a-d3538c97b04b pri=1            swap    sw              0       0

```

and swapon -s is giving me 

```
Filename				Type		Size	Used	Priority
/dev/sdb5                               partition	4450300	0	-1
/dev/sdc5                               partition	4450300	0	-2

```

Is it normal that we still see priority -1 and priority -2 here ?

---

### Post by Cavsfan on 2012-10-06
> **mintfrish said:**
> Thanks mate. I followed your instructions and commented everything off that was unnecessary. But why only one swap partition? Isn't it the intention of the op to create 2 swap partitions ? 
Anyways, first I had to get rid of the cryptswap. After doing that I created the 2 swap partitions with mkswap /dev/sdb5 and /dev/sdc5. With that done I got the UUID's and I could paste them into fstab. I set them both with pri=1. 

Theese are the two new swap partitions in fstab
```
#swap manuell hinzugefügt
UUID=eb377be2-1b3f-414c-bed3-92c28bfafeff pri=1            swap    sw              0       0
#swap manuell hinzugefügt
UUID=1aed75da-7159-43b4-9b1a-d3538c97b04b pri=1            swap    sw              0       0

```and swapon -s is giving me 

```
Filename                Type        Size    Used    Priority
/dev/sdb5                               partition    4450300    0    -1
/dev/sdc5                               partition    4450300    0    -2

```Is it normal that we still see priority -1 and priority -2 here ?

That looks right according to page 1. As I said you are out of my league. I only subscribed to this thread so if I ever did have a RAID
configuration, this would help.
I will now butt out and "observe".

---

### Post by mintfrish on 2012-10-25
Me again. :( 
Wow, after using the mdadm ubuntu until yesterday I get this while booting 

```

Kernel Panic - not syncing: Attempted to kill init!
Pid: 1, comm: init Not tainted 3.2.0-32-gerneric #51-Ubuntu
Call Trace:...
```

What is that ? Can I do something or is my whole, with a lot of effort built system, gone ?

---

### Post by rickyrockrat on 2012-10-26
It just sounds like your raid didn't rebuild so it can mount. Is there more of the message? You should see something like can't mount xxx.

If you dump /dev/disk/by-id or /dev/disk/by-uuid like so (xxx replaced by however you want to list):

ls -l /dev/disk/by-xxx

It will give us a better understanding of how your system is configured. Did /etc/fstab change?  Is root on md0? If yes, your raid array did not assemble before the attempted mount of root.

---

### Post by mintfrish on 2012-11-05
Ooh thanks so much mate. Sorry I check back in so late. 

Unfortunately I already reinstalled ubuntu on my array. To know what caused the problem would be a good thing but now it's too late, isn't it ? Anyways memtest detected problems with RAM memory so it's likely that this was the wrongdoer.

---

### Post by reko420 on 2013-03-31
Everything went OK then I rebooted to complete install and I get a grub error

Error file not found

OK just kept trying got it to boot but it only loads the root aray

---

### Post by Tom_T on 2013-04-19
Today my Western Digital NAS drive has failed.

I've removed the single 1TB Disk and connected it via SATA -> USB to my Ubuntu PC.
Nothing is detected.

If I run gparted I get :

/dev/sdb1 - Unknown - 128MiB
unallocated - Unallocated - 931.39 GiB

I've been told :
It's a mdmadm software RAID volume, this is why you can't see your data.

Can any one advise how I get my data back ?

Thanks :(

---

### Post by Kissell on 2013-04-19
If you had a NAS that had a RAID array configured...  why did you remove the drive from it?  If a single disk failed, you should still have been able to access all your files on the NAS.  If you removed the failed disk and are trying to access files on it, that's not going to work.  If you removed the remaining good disk of a mirrored set, you should be able to view those files on a Ubuntu PC, assuming you have mdadm installed and have assembled the degraded array.

apt-get install mdadm

mdadm --assemble --force /dev/md127 /dev/sdb1 
NOTE: sdb1 needs replaced with the device letter of the disk you plugged in.

---

### Post by Tom_T on 2013-04-19
Hi
Thanks for taking the time to reply.

I removed the disk as the NAS drive has started flashing the LED's to indicate it couldn't boot.

I'm hoping I'll be able to recover the data.

I don't know if the disk was configured as raid. I was setup as default.
The NAS is a western digital my world book white light, single 1TB SATA disk.
I've not done any thing with it apart from copying data to it.

I've tried the command you've listed and it returns:
mdadm: no recogniseable superblock on /dev/sdb1
mdadm: /dev/sdb1 has no superblock - assembly aborted

Anything else I can try ?

Thanks :)

---

### Post by Kissell on 2013-04-19
mdadm is a tool for combining multiple disks into a redundant array, so that if a disk fails you can still access all your data.  

If you only had one disk in your NAS then it wouldn't have been using mdadm, and you'll have to use some other software to attempt to recover your data from the hard drive.  But if the disk is bad that might be impossible.  You should restore from your backup =p   or take the hard drive to a local PC repair shop that specializes in hard drive data recovery.  Sorry, but mdadm and "RAID" don't apply to NAS devices with only one disk.

---

### Post by Tom_T on 2013-04-19
Thanks again for your advise.
Any suggestions on recovering this using Ubuntu?

---

### Post by Tom_T on 2013-04-19
Running Test Disk
Shows this for the drive:


Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63
Analyse cylinder   402/121600: 00%


  MS Data                    64320    3984063    3919744
  Linux Raid                 64320    3984191    3919872 [md0]
  Linux Swap               3984192    4497967     513776
  Linux Raid               3984192    4498111     513920 [md1]
  MS Data                  4498176    6473983    1975808
  Linux Raid               4498176    6474111    1975936 [md3]
  Linux Raid               6474176 1953524869 1947050694 [MyBookWorld:2]

Doesn't this suggest it's a raid disk ?

Help !  thanks :)

---

### Post by rickyrockrat on 2013-04-20
It looks like your drive is partitioned as follows:
/dev/sdb1 MS Data (whatever that is - I assume it is a Microsoft something)
/dev/sdb2 is md0, a Linux software raid
/dev/sdb3 is Linux swap (just ignore this)
/dev/sdb4 is md1, the second Linux Software raid
/dev/sdb5 is again Microsoft something
/dev/sdb6 is md3, yet another Linux Software raid.

The last looks like it may be a vendor-specific partition. So use /dev/sdb2, /dev/sdb4, and /dev/sdb6 as input to mdadm.

---

### Post by Tom_T on 2013-04-22
Still not got anywhere with this..
Anyone will to help a bit ?

I've run a couple of Raid scanning apps and they are showing my data, so there is some hope.
I just need to find a way to get at it..

DiskInternal Raid Recovery seems to show my data, but that costs £299.00
A lot of money for a home user..

can anyone help ?

Thanks

---

### Post by rickyrockrat on 2013-04-22
This is from my personal notes (your disks and devices will be different):
mdadm --examine --scan  /dev/sda1 /dev/sda2 >> /etc/mdadm.conf
The lines in the mdadm.conf file should look like this:
ARRAY /dev/md0 level=raid1 num-devices=3 UUID=e03a952e:5ed1a43c:c79e3f2b:927be822

Use mdadm /dev/md0 --add /dev/sdc1 to add
If you have an existing software raid, you may have to create a new md:
MAKEDEV md4
mdadm -C /dev/md4 -l 1 -n 2 missing /dev/sdb1
if you have an existing disk that *was* on USB and put it in PATA, you may have
a device node that is incorrect. This will have mdadm saying "device is too small".
Fix it by deleting the device and making the new node: 
mknod /dev/sdb1 b 8 18 
but make sure the minor (last no) doesn't conflict.

Your md and devices are, apparently
 /dev/sdb2 is md0
/dev/sdb4 is md1
/dev/sdb6 is md3

---

### Post by Tom_T on 2013-04-23
The disk is an XFS disk
[http://en.wikipedia.org/wiki/XFS](http://en.wikipedia.org/wiki/XFS)

Using either 

NAS Data Recovery 
[http://www.runtime.org/nas-recovery.htm](http://www.runtime.org/nas-recovery.htm)

or 
Raise Data Recovery for XFS 5.8
[http://www.softpedia.com/get/System/Back-Up-and-Recovery/Raise-Data-Recovery-for-XFS.shtml](http://www.softpedia.com/get/System/Back-Up-and-Recovery/Raise-Data-Recovery-for-XFS.shtml)

I can see my data.. Raise is only around £20.00 for a licence.
So that seems to be the way to go.

Hope this helps someone else.

---

### Post by rickyrockrat on 2013-04-23
XFS is in the Linux kernel - I just checked CONFIG_XFS_FS is in the kernel config file, so if you have a Linux system you should be able to read those raid systems.

---

