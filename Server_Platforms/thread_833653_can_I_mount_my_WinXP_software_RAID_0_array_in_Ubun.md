---
title: "can I mount my WinXP software RAID 0 array in Ubuntu/Kubuntu?"
date: 2008-06-18
forum: Server Platforms
---

### Post by BobTheDinosaur9 on 2008-06-18
*posted here cos i figured the server guys would know a thing or two about raid...

The title pretty much says it all, i've got 4 500's in 2x RAID 0 arrays, i.e. two RAID disks

in ubuntu/kubuntu i can see them as unidentified volumes, thing is, i don't know how to mount them and when i just right click and choose mount it complains about RAID/LDM

please take into account that i'm a complete noob, i installed and viewed linux for the first time in my whole life 2 days ago

thanks in advance

p.s. i have managed to install my dell laptop wifi drivers using terminal, i didn't know what i was doing though...

---

### Post by beniwtv on 2008-06-19
Hi,
How did you create the raid? What program did you use?

Cheers,

---

### Post by BobTheDinosaur9 on 2008-06-19
window's built-in disk management software utility, i created dynamic disks and then raid 0'ed them

---

### Post by beniwtv on 2008-06-19
I think it's not possible then. Windows and Ubuntu use their own specifications for creating raid. AFAIK, they're not compatible (someone correct me if I'm wrong, though).

Cheers,

---

### Post by Martigen on 2008-06-19
> **beniwtv said:**
> I think it's not possible then. Windows and Ubuntu use their own specifications for creating raid. AFAIK, they're not compatible (someone correct me if I'm wrong, though).

Cheers,

Piffle, this is Linux, anything is possible :)

Bob -- yes you can, I do it myself. But as a less-than-common scenario there's no user-friendly tool to make it easy.

The Linux kernel includes the 'md' (multiple disk) driver to manage Linux software RAID devices. What isn't common knowledge is that Windows software RAID uses an identical structure, bar superblocks (don't worry about these for now). So, Linux being awesome as it is, can in fact mount Windows software RAID devices -- as long as you tell it where they are (and that's where superblocks come in for Linux, enabling auto-building arrays).

**Here'a a quick how-to:**

**1.** First make sure you've got the 'mdadm' tools installed:
```

sudo apt-get install mdadm

```

**2.** Now determine the partitions being used for your Windows array. If you know these already, great, if not check your partitions like so:
```

cat /proc/partitions

```
On my system, for example, I get:
```

major minor  #blocks  name

[...output cut...]

   8    32  146523384 sdc
   8    33   10485760 sdc1
   8    34   10483712 sdc2
   8    35  125548544 sdc3
   8    48  146523384 sdd
   8    49   10485760 sdd1
   8    50   10483712 sdd2
   8    51  125548544 sdd3


```
For me, my Windows RAID array is built from /dev/sdc2 and /dev/sdd2 (my sdc1 and sdd1 are my Linux RAID boot)

**3.** Start the array with mdadm, create a directory to mount it, and then mount it:
```

sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdd2 /dev/sdc2
sudo mkdir /media/Windows
sudo mount -t ntfs /dev/md0 /media/Windows

```

And that's it! The new 'Windows' mount will appear on your desktop to access.

**Helpful stuff to know**

***** Make sure Windows was shutdown cleanly before booting Linux. If not, both the array and mounting with NTFS will likely refuse to work.
***** If an array still won't build (an error is reported), try swapping the devices around -- for eg '/dev/sdc2 /dev/sdd2' instead of '/dev/sdd2 /dev/sdc2'. The order they are used to build the array is important.
***** Windows software RAID actually uses a chunk size of 128k, but the Linux md driver wants to know the chunk size per device in the array, and so we use 64. You can actually build it with 128 too, but if you mount it you'll see missing files and directories (and whatever you do, do not write to it in this mode!)
***** The 'mdadm' command comes with an --assemble option, but this is for super-block (Linux based) arrays. Hence we use --build which will assemble arrays regardless of superblocks and on the assumption the user knows what they are doing (and, in this case, allows us to mount Windows arrays).
***** Run 'cat /proc/mdstat' to see the active arrays on your system.

Finally you said you have two RAID 0 arrays -- don't forget to increment '/dev/md0' to '/dev/md1' for your second array, and create another directory to mount it on, so you can access both arrays from your desktop.

---

### Post by beniwtv on 2008-06-19
> **Martigen said:**
> Piffle, this is Linux, anything is possible :)


Ha! I stand corrected then. And yes, in Linux everything seems possible. :)

---

### Post by BobTheDinosaur9 on 2008-06-19
> **Martigen said:**
> Piffle, this is Linux, anything is possible :)

Bob -- yes you can, I do it myself. But as a less-than-common scenario there's no user-friendly tool to make it easy.

The Linux kernel includes the 'md' (multiple disk) driver to manage Linux software RAID devices. What isn't common knowledge is that Windows software RAID uses an identical structure, bar superblocks (don't worry about these for now). So, Linux being awesome as it is, can in fact mount Windows software RAID devices -- as long as you tell it where they are (and that's where superblocks come in for Linux, enabling auto-building arrays).

**Here'a a quick how-to:**

**1.** First make sure you've got the 'mdadm' tools installed:
```

sudo apt-get install mdadm

```

**2.** Now determine the partitions being used for your Windows array. If you know these already, great, if not check your partitions like so:
```

cat /proc/partitions

```
On my system, for example, I get:
```

major minor  #blocks  name

[...output cut...]

   8    32  146523384 sdc
   8    33   10485760 sdc1
   8    34   10483712 sdc2
   8    35  125548544 sdc3
   8    48  146523384 sdd
   8    49   10485760 sdd1
   8    50   10483712 sdd2
   8    51  125548544 sdd3


```
For me, my Windows RAID array is built from /dev/sdc2 and /dev/sdd2 (my sdc1 and sdd1 are my Linux RAID boot)

**3.** Start the array with mdadm, create a directory to mount it, and then mount it:
```

sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdd2 /dev/sdc2
sudo mkdir /media/Windows
sudo mount -t ntfs /dev/md0 /media/Windows

```

And that's it! The new 'Windows' mount will appear on your desktop to access.

**Helpful stuff to know**

***** Make sure Windows was shutdown cleanly before booting Linux. If not, both the array and mounting with NTFS will likely refuse to work.
***** If an array still won't build (an error is reported), try swapping the devices around -- for eg '/dev/sdc2 /dev/sdd2' instead of '/dev/sdd2 /dev/sdc2'. The order they are used to build the array is important.
***** Windows software RAID actually uses a chunk size of 128k, but the Linux md driver wants to know the chunk size per device in the array, and so we use 64. You can actually build it with 128 too, but if you mount it you'll see missing files and directories (and whatever you do, do not write to it in this mode!)
***** The 'mdadm' command comes with an --assemble option, but this is for super-block (Linux based) arrays. Hence we use --build which will assemble arrays regardless of superblocks and on the assumption the user knows what they are doing (and, in this case, allows us to mount Windows arrays).
***** Run 'cat /proc/mdstat' to see the active arrays on your system.

Finally you said you have two RAID 0 arrays -- don't forget to increment '/dev/md0' to '/dev/md1' for your second array, and create another directory to mount it on, so you can access both arrays from your desktop.

wow! thanks man, i must say linux is quite impressive, i'm an utter noob though, only acquired it about 3 days ago, so a lot of what your saying is greek to me, i've read a bit on how linux defines disks but that last bit about incrementing for my second array, could you help me understand that a little bit better?

---

### Post by jakub12 on 2008-06-19
I am joining in this thread since I am attempting to do the same thing, access my Raid 0 where my Windows is installed.
I followed the suggested procedure: here is what I got:

jakub@jakub-desktop:~$ cat /proc/partitions
major minor  #blocks  name

   8     0  156290904 sda
   8     1   30716248 sda1
   8     2   30716280 sda2
   8     3          1 sda3
   8     4   47664480 sda4
   8     5    1951866 sda5
   8     6    1951866 sda6
   8     7    9767488 sda7
   8     8    3903763 sda8
   8     9    5855661 sda9
   8    10     979933 sda10
   8    11    1951866 sda11
   8    12    1951866 sda12
   8    13   16603146 sda13
   8    14    2273166 sda14
   8    16  244198584 sdb
   8    17  244196001 sdb1
   8    32  244198584 sdc
   8    33  122881153 sdc1
   8    34          1 sdc2
   8    48  244198584 sdd
 253     0  488397056 dm-0
 253     1  122881153 dm-1
jakub@jakub-desktop:~$ sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdb1 /dev/sdc1
[sudo] password for jakub: 
mdadm: Cannot open /dev/sdc1: Device or resource busy
jakub@jakub-desktop:~$ sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdc1 /dev/sdb1
mdadm: Cannot open /dev/sdc1: Device or resource busy
jakub@jakub-desktop:~$ 

My Windows is on /dev/sdb1 and /dev/sdc1 array.It seems that there is something weird with my sdc2 partition- it's not supposed to be there, don't know where it came from. Is it possible that "Device busy" message is caused by that?

Thanks,
Jakub

---

### Post by jakub12 on 2008-06-19
I have solved my problem as per solution in this thread: [http://ubuntuforums.org/showthread.php?t=184934](http://ubuntuforums.org/showthread.php?t=184934).

The code:
sudo dmraid -r
/dev/sdd: nvidia, "nvidia_ibfbejec", stripe, ok, 488397166 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_ibfbejec", stripe, ok, 488397166 sectors, data@ 0

sudo dmraid -ay
RAID set "nvidia_ibfbejec" already active
RAID set "nvidia_ibfbejec1" already active

sudo mkdir /media/raid "should have named it something more imaginative

sudo mount -t ntfs /dev/mapper/nvidia_ibfbejec1 /media/raid

After that an icon named "raid" on my desktop appeared as if by magic.

Thanks a million guys for all your suggestions,
Jakub

---

### Post by Martigen on 2008-06-20
> **BobTheDinosaur9 said:**
> wow! thanks man, i must say linux is quite impressive, i'm an utter noob though, only acquired it about 3 days ago, so a lot of what your saying is greek to me, i've read a bit on how linux defines disks but that last bit about incrementing for my second array, could you help me understand that a little bit better?

Sure -- I'll break down the command and show you what it's doing:
```

sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdd2 /dev/sdc2

```
As you probably know commands take 'switches' and we have a number here:
```

--build        : Tells mdadm to build a new array
/dev/md0       : Is the RAID array under Linux we want to create
--chunk        : Specifies the chunk size to use (see my previous post)
--level        : The RAID level, of course, which is 0 for RAID 0
--raid devices : Number of drives or partitions in the array we are building
/dev/sd...     : The drives or partitions making up the array

```
On drives under Linux -- all devices exist under the /dev directory, and for drives specifically you'll find they all start with 'sd' for 'scsi disk'. SATA drives come under scsi for the purposes of the kernel. Pulling apart an example device:
```

/dev/sda1
      ^^^-- Partition number on drive
      ||--- Drive number on controller
      |---- Device type (scsi drive)

```
So for example /dev/sda1 is the first partition on the first drive, /dev/sdc4 would be the fourth partition on the third drive, and so on.

Now to your question about incrementing 'md'. Remember the 'md' driver builds RAID arrays under Linux so, just like a hard drive, an array appears to Linux as just another device. And since you can have many arrays, each one is numbered just like drives and partitions are. So for example /dev/md0 is the first array, /dev/md1 the second and so on.

So if you want to mount both your arrays, you will be creating two arrays with the 'md' driver using the mdadm command, and you'll want to specify a new md device to create for each, like so (note your specific partitions to build the arrays from are probably different, this is just an example):
```

sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdd2 /dev/sdc2
sudo mdadm --build /dev/md1 --chunk=64 --level=0 --raid-devices=2 /dev/sdd3 /dev/sdc3

```
Would create a RAID array /dev/md0 from partitions /dev/sdd2 and /dev/sdc2 and a RAID array /dev/md1 from partitions /dev/sdd3 and /dev/sdc3.

Hope that helps!

> **jakub12 said:**
> I have solved my problem as per solution in this thread: [http://ubuntuforums.org/showthread.php?t=184934](http://ubuntuforums.org/showthread.php?t=184934).

The code:
sudo dmraid -r
/dev/sdd: nvidia, "nvidia_ibfbejec", stripe, ok, 488397166 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_ibfbejec", stripe, ok, 488397166 sectors, data@ 0

sudo mkdir /media/raid "should have named it something more imaginative

sudo mount -t ntfs /dev/mapper/nvidia_ibfbejec1 /media/raid

It's VERY important to differentiate Windows software RAID arrays and fakeraid arrays. For everyone reading:

***** If you make an array in Windows using Windows' drive management tools -- aka converting one or more disks to 'dynamic' disks and RAIDing two or more partitons --> you have a Windows softraid array, and you need to follow the instructions in the fifth post of the this thread to mount them.

***** If you use motherboard based onboard RAID controllers, like Nvidia/Intel etc --> this is what's known as 'fakeraid' -- these controllers provide a hardware interface to an array, and present this to Windows and Linux as a pre-made device. They are called fakeraid because, despite being a 'hardware' solution, all processing is actually still done in software. In any event, RAID arrays made using onboard contollers need to be mounted with the 'dmraid' package, which jackub has covered above.

In summary -- there are two types of RAID array created from Windows, and just as they are accessed in two different ways under Windows, there are two different methods to use these arrays under Linux.

---

### Post by Martigen on 2008-06-24
^ bump for bob

---

### Post by windependence on 2008-06-24
I'll add to martigen's post a bit.

IMHO software RAID is not the best thing to do if you value your data and RAID 0 can be extrememly dangerous without very good verifiable backups. RAID 0 is for speed only and has NO redundancy at all. If one node in the array gets corrupted, you are screwed.

I'm not trying to be funny here but why does it seem that everyone here wants to put everything in RAID, because it's "cool"? I have moved away from RAID, even hardware RAID on my production boxes because it can be difficult to recover in a disaster, and SATA drives are cheaper, just as fast and just as reliable as SCSI drives. Unless you have a real need for RAID of some kind (and even then it should be hardware RAID), I don't see the point. </rant off>

-Tim

---

### Post by fjgaude on 2008-06-24
> **windependence said:**
> I'll add to martigen's post a bit.

IMHO software RAID is not the best thing to do if you value your data and RAID 0 can be extrememly dangerous without very good verifiable backups. RAID 0 is for speed only and has NO redundancy at all. If one node in the array gets corrupted, you are screwed.

I'm not trying to be funny here but why does it seem that everyone here wants to put everything in RAID, because it's "cool"? I have moved away from RAID, even hardware RAID on my production boxes because it can be difficult to recover in a disaster, and SATA drives are cheaper, just as fast and just as reliable as SCSI drives. Unless you have a real need for RAID of some kind (and even then it should be hardware RAID), I don't see the point. </rant off>

-Tim

Thanks, Tim, for your opinions... SATA is not as fast or as reliable as SCSI, except for the WD Raptor drives. SCSI has double the seek speed because only a smaller portion of the platter is covered. More Quality Control testing is performed on SCSI drives. Thus they cost more.

Software raid is just as reliable as hardware, using **mdadm**. Both hardware controllers on cards, PCI, PCI-X, and PCI-E depend on the motherboard. Any failure along the chain is potential data loss.

Software raid5, raid6 and raid10 are used for reliability and speed. One or more drives can fail and the system continues at reduced thru-put until replacements are made. No downtime.

Large server farms continue to use SCSI, with SATA second-, third-line off-line backup, for their superior thru-put.

Here's my humble 4-drive raid setup and its quickness:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=24C; under max load, temp=41C, fan=1167 RPM; VCore=1.39/1.38v:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   18948 MB in  2.00 seconds = 9487.52 MB/sec
 Timing buffered disk reads:  644 MB in  3.00 seconds = 214.42 MB/sec

```

Servers using 16 SCSI drives normally have thru-puts of over 400 MB/sec.

---

### Post by windependence on 2008-06-25
Please understand that I am not, in any way a n00b at this stuff. I work for a Fortune 100 company with world wide operations and server farms with thousands of machines.

I am going to agree to disagree with you on some points, namely software RAID and whether SCSi is faster than the new SATA II drives with NCQ. 

The point I was trying to make here is it seems like every n00b needs to do RAID whether they need it or not and then because rthey can't afford a good SCSI hardware controller, they do software RAID which consumes lots of CPU cycles and is difficult to recover from in the case of a catastrophic failure. Most run it with no backups too, thinking that a mirror is good enough. As you and I know, it's not. I also run a small consulting business on the side and for most of my customers there, I run 2 or 3 drives for the OS and data, and a totally separate drive for backups. In situations where RAID is warranted, the three dirves are run in RAID 5 and the backup drive is a separate raw drive. This way in case of failure, I still have easy acces to my data. I don't see the point of running RAID 1 like most people here do. You waste 50% of your space and if a drive gets corrupted, the mirror does too. I would say and probably pretty accurately that most people here on the forums do not need RAID at all, and are just making things more difficult for themselves in terms of complexity, especially if they are running software RAID with LVM on top of it.

As far as SATA II drives go, they are now hot pluggable, some have command queing like SCSI, and the difference in transfer rate is a toss up. With drives now having in excess of a 300,000 hour MTBFR rate, I cannot justify the cost of SCSI for most of my small business clients.

I respect the fact that you have a different opinion and of course that is what keeps things interesting. It's my opinion that SCSI is on the way out and will be replaced very soon with something cheaper AND faster whatever it is. :)

-Tim

---

### Post by beniwtv on 2008-06-25
Hey Tim,

I agree with you on two points, but on one point I beg to differ. :)

We all agree that RAID alone is NOT enough for your data safety. You still have to do backups, please people, on separate disks, tapes, whatever. Trust me.

It may be very well enough for your home casual data, but certainly not for your customer's data in your enterprise.

I also agree with you on people using RAID when they don't need it. For example, for my home laptop, I certainly don't need RAID, backups will do just as fine. However, RAID on a home server could come in handy sometimes. And certainly advised for enterprises.

But I do not agree that hardware RAID is better than software RAID. Well, it depends on what software RAID. I exclusively use Linux software RAID, in my company and my home. I found it extremely stable, compared to some other hardware RAID solutions. I also ran into incompatibilities between the different controller manufacturers using hardware RAID (no fakeraid, REAL hardware RAID), which I don't seem to have with Linux software RAID. And don't even get me started on fakeraid. IMHO, if you have a AMD Phenom Quad Core with 8GB of RAM, you don't mind the CPU overhead anymore.

Just my 2 € cents.

Cheers,

---

### Post by windependence on 2008-06-25
OK now you have my mind open so let me give you a scenario and tell me how I would handle it.

Suppose I want to set up software raid on a Linux box. If the OS takes a crap you can't rebuild the system. I want something I can recover from easily. How do you set up your box to do that? Do you put your OS on a separate drive? Can you boot from the RAID drive and what if it becomes corrupted? Let's say I have 4 500 GB disks and I want to be able to back up to one of them and run my apps and system on the other ones. How would you set up/partiion it? Would you use LVM? I am talking for a small business enterprise solution here. I am truly interested in testing this if you say if has been stable. What happens if a drive goes? can you hot swap it and how do you do it?

Thanks in advance,

-Tim

---

### Post by beniwtv on 2008-06-25
> Suppose I want to set up software raid on a Linux box. If the OS takes a crap you can't rebuild the system. 

You can. In fact, I just updated my Gutsy server to Hardy. The server uses RAID and LVM. By update I mean installing the whole new system from scratch.

You can mount all your existing RAID arrays and LVM devices, within the installer, with out even using the command shell (although only with the alternate installer).

A bit of background here: The server uses two 500 GB HDD's, with one partition for RAID, one for /boot and /tmp respectively on each disk, and swap. On top of the RAID I have a LVM, with / and /home on separate LVM partitions, formatted XFS. Of course, the installer detects that and you can mount /home and only overwrite /, like a hardware RAID. So you don't loose any data doing a new install, or even installing another distro.

If the RAID array is broken, there are utilities to recover it. You could use Knoppix to boot in Live-CD and fix your array. I have an article about that - however I'm at work right now so I can't give you the link.

> I want something I can recover from easily. How do you set up your box to do that? Do you put your OS on a separate drive? Can you boot from the RAID drive and what if it becomes corrupted?

Grub doesn't yet allow booting from RAID, that's why I have a small 200 MB partition for /boot in Ext3 (see above) However 200 MB on a 500 GB disk is not anything I'd miss. :)

> 
Let's say I have 4 500 GB disks and I want to be able to back up to one of them and run my apps and system on the other ones. How would you set up/partiion it? Would you use LVM? 


I certainly would use LVM. The nice part of that is that you can create as many RAID devices as you need, unify them, make separete LVM partitions out of them, etc... With XFS, you can add more RAID devices and expand /home to them WITHOUT even needing to unmount.

Best of all: With 4 disks you could use RAID1+0, for speed and some sort of reliability, or the four disks in RAID 1. Doesn't really matter as LVM allows you to partition the RAID arrays to your liking.

> 
I am talking for a small business enterprise solution here. I am truly interested in testing this if you say if has been stable. What happens if a drive goes? can you hot swap it and how do you do it?

Linux does support hot swapping of S-ATA drives. There are commands in mdadm that let you just do that. You can also expand raid arrays on the fly, or create new ones. However, your controller also has to support it.

Despite of all this: Do backups. As you said, there's no excuse for not doing backups of your RAID arrays.

Cheers,

---

### Post by rccvilla on 2008-09-03
THANKS Martigen!
You´ve saved my life :P
I have (still do, getting the data out) 3 HDs working in Windows Raid (0).
Yesterday they were working fine (created yesterday). Today, when I woke up, one of them was "illegible" (is that right?).
Following your simples steps, I mounted them on linux, and now I'm copying the data to the other computer!:guitar:

I'm very thankful!

(And sorry for my bad english, I'm brazilian)


Edit:
Just updating, after copying all data to the other computer, I booted back to windows and the Windows Raid was running ok... didn't understand that part...

---

### Post by timbellomo on 2008-12-12
A bit off topic, but is anyone knowledgeable in performing the reverse?  That is, can I mount my Linux software RAID 0 in Windows?

I made the switch about a year ago, but now I have software that needs Windows.  If possible, I'd like Windows to be able to read/write from/to my Linux software RAID (2 500GB SATA drives, separate from the 250 "OS" drive).

I checked out Ext2IFS, but that doesn't support raid, AFAIK.

Ideas?

Great thanks,
Another Tim

P.S.  If I'd know a year ago I'd know that Linux could have read my Windows array, this would be a moot point.  If need be, I'll switch my array back to a Windows Dynamic striped volume (reformat, restore from backup) and access it from Linux as noted previously... but I'd prefer to keep the Linux array since I do 98% of my tasks in Ubuntu.

---

### Post by beniwtv on 2008-12-12
> **timbellomo said:**
> A bit off topic, but is anyone knowledgeable in performing the reverse?  That is, can I mount my Linux software RAID 0 in Windows?

This tool claims it can read and write RAID:
[http://www.chrysocome.net/virtualvolumes](http://www.chrysocome.net/virtualvolumes)

However, I've not tested it so I'm not sure if it works (do a backup before, just in case...)

Cheers,

---

### Post by DarkStarZN on 2009-05-23
Sorry for the thread necro, but I need help in these regards.

I have a software RAID 0 created in Vista (2x259GB Samsung drives), and I need to mount it in Ubuntu.

I'm using 9.04 (the latest).

I followed [Martigen's]("http://ubuntuforums.org/member.php?u=322590") instructions on the first page and it all goes smoothly until I need to mount the new 'drive', where it tells me it can't find an NTFS partition (or somewhere along those lines).

There has to be a way for me to do this, as I can't really afford to lose the data on those drives in a format (and I have no means to back them up)

---

### Post by ronparent on 2009-05-23
9.04 the latest may not be the best in this regard.

Presuming you have a MB raid controller and you want to retain interoperabily with windows you would be using using dmraid referred to as a 'fakeraid'. Don't let the term throw you. To see it in ubuntu you need open a terminal and run:

**sudo apt-get install dmraid -y**

then if the install was successful continue with

**sudo dmraid -ay**

At this point you will see the results in /dev/mapper. I myself am stuck with the next step to mount the raid partitions automatically in ubuntu 9.04. In 8.10 I merely edited the /dev/fstab as sudo to link the symbolic links you see in /dev/mapper automatically to mount points created for that purpose. If you are using 8.10 I can tell you how to do this. If it is 9.04, I am still trying to figure that out! At this point you can do it manually with a mount command:

**mount /dev/mapper/<your raid partition entry> /media/<whatever you want to call it>**

It can do no harm to try it and see if it works.

---

### Post by kybel_gitu on 2010-06-20
> **Martigen said:**
> Piffle, this is Linux, anything is possible :)

Bob -- yes you can, I do it myself. But as a less-than-common scenario there's no user-friendly tool to make it easy.

The Linux kernel includes the 'md' (multiple disk) driver to manage Linux software RAID devices. What isn't common knowledge is that Windows software RAID uses an identical structure, bar superblocks (don't worry about these for now). So, Linux being awesome as it is, can in fact mount Windows software RAID devices -- as long as you tell it where they are (and that's where superblocks come in for Linux, enabling auto-building arrays).

**Here'a a quick how-to:**

**1.** First make sure you've got the 'mdadm' tools installed:
```

sudo apt-get install mdadm

```

**2.** Now determine the partitions being used for your Windows array. If you know these already, great, if not check your partitions like so:
```

cat /proc/partitions

```
On my system, for example, I get:
```

major minor  #blocks  name

[...output cut...]

   8    32  146523384 sdc
   8    33   10485760 sdc1
   8    34   10483712 sdc2
   8    35  125548544 sdc3
   8    48  146523384 sdd
   8    49   10485760 sdd1
   8    50   10483712 sdd2
   8    51  125548544 sdd3


```
For me, my Windows RAID array is built from /dev/sdc2 and /dev/sdd2 (my sdc1 and sdd1 are my Linux RAID boot)

**3.** Start the array with mdadm, create a directory to mount it, and then mount it:
```

sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdd2 /dev/sdc2
sudo mkdir /media/Windows
sudo mount -t ntfs /dev/md0 /media/Windows

```

And that's it! The new 'Windows' mount will appear on your desktop to access.

**Helpful stuff to know**

***** Make sure Windows was shutdown cleanly before booting Linux. If not, both the array and mounting with NTFS will likely refuse to work.
***** If an array still won't build (an error is reported), try swapping the devices around -- for eg '/dev/sdc2 /dev/sdd2' instead of '/dev/sdd2 /dev/sdc2'. The order they are used to build the array is important.
***** Windows software RAID actually uses a chunk size of 128k, but the Linux md driver wants to know the chunk size per device in the array, and so we use 64. You can actually build it with 128 too, but if you mount it you'll see missing files and directories (and whatever you do, do not write to it in this mode!)
***** The 'mdadm' command comes with an --assemble option, but this is for super-block (Linux based) arrays. Hence we use --build which will assemble arrays regardless of superblocks and on the assumption the user knows what they are doing (and, in this case, allows us to mount Windows arrays).
***** Run 'cat /proc/mdstat' to see the active arrays on your system.

Finally you said you have two RAID 0 arrays -- don't forget to increment '/dev/md0' to '/dev/md1' for your second array, and create another directory to mount it on, so you can access both arrays from your desktop.

This does not work for windows sortware raid5 arrays:

home@venux:~$ sudo mdadm --build /dev/md0 --chunk=64 --level=5 --raid-devices=4 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1
mdadm: Raid level 5 not permitted with --build.

Can someone advice me how to access win software raid5 in ubuntu (10.04) without destroying the existing data?

My setup looks like this:

home@venux:~$ cat /proc/partitions
major minor  #blocks  name

   8        0  156290904 sda
   8        1   81923436 sda1
   8        2          1 sda2
   8        5   71288406 sda5
   8        6    3076416 sda6
   8       16   80043264 sdb
   8       17   80035798 sdb1
   8       32  293057352 sdc
   8       33  293049666 sdc1
   8       48  312571224 sdd
   8       49  312567808 sdd1
   8       64  312571224 sde
   8       65  312567808 sde1
   8       80  312571224 sdf
   8       81  312567808 sdf1
   8       96  312571224 sdg
   8       97  312567808 sdg1

It confuses me that array disks are shown twice. I suppose one is drive and second is volume.
I admit that i have no idea. :)

thanx

---

### Post by k999 on 2011-02-07
Thanks for the info, it works on a software RAID0 I set up in Windows 7. It didn't work at first, but I had to change the order from:

```
sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdb1 /dev/sdc1
```

to

```
sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdc1 /dev/sdb1
```

For the record, nothing broke when I set it up wrong first and tried to mount the file system. :) I even tried with 128kb chunks before changing the order, and that didn't break anything either.

Anyway, now I'd like to set this up so it mounts automatically. I've been reading the mdadm.conf man page, but can't find anywhere to specify the chunk size. Has anyone done this?

---

### Post by afks101 on 2011-05-16
> **k999 said:**
> Anyway, now I'd like to set this up so it mounts automatically.

I'd like to do this as well. Setting up and mounting the raid works great, but it's such a pain to have to do this every time I start up. Any way to automate this?

---

### Post by wesleykins on 2012-07-20
Since this 4 yr. old thread was resurrected as recently as last year, I don't feel too bad bringing it up again ;)

I finally decided to make the switch**™**[FONT=Arial], and Grub2 is too stubborn to let me boot back into Windows XP to access my software array.

The difference is, My array is set up as a *span* of 7 volumes.

I tried building with the mdadm command:
[/FONT]```
mdadm --build /dev/md0 **--rounding=64** **--level=linear** --raid-devices=7 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1
```Based on the options here: [http://man-wiki.net/index.php/8:mdadm#For_create_or_build:](http://man-wiki.net/index.php/8:mdadm#For_create_or_build:)

It seemed to work;  I got the array built and started:
```
mdadm: array /dev/md0 built and started.
```...but it won't mount.
```
mount -t ntfs /dev/md0 /media/winraid
Failed to read last sector (26366742248): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/md0': Invalid argument
The device '/dev/md0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```Has anyone successfully built and mounted a Windows-created software-spanned array?

Any suggestions?

Thanks,

-Wes

---

### Post by wesleykins on 2012-07-26
Sorry for the bump, but I'm still looking for a solution to this.

Has anyone successfully mounted a Window "span" array using mdadm (or heck, using any other tool?)

-Wes

---

### Post by CharlesA on 2012-07-26
I doubt it. Dynamic disks are a Windows only thing.

---

### Post by wesleykins on 2012-07-27
> **CharlesA said:**
> I doubt it. Dynamic disks are a Windows only thing.

Thanks for the reply, Charles.

Linux actually can mount Windows dynamic disks; [see post 5]("http://ubuntuforums.org/showpost.php?p=5217561&postcount=5") in this very thread.

Many folks have reported mounting both striped and mirrored Windows Dynamic arrays.

The key is using mdadm --build instead of mdadm --assemble, because Windows softraid doesn't use superblocks like Linux RAID, so that tells mdadm to ignore superblocks when building.

--create does Bad Things to an array that already has data on it, or so I've read...

I thought maybe I was using the wrong chunk size, but I'm not sure what to do.  It looks like it should be 64k.

---

### Post by CharlesA on 2012-07-27
I don't like using dynamic disks in Windows due to the them being inaccessible from another OS, so I don't really have much information about that.

Also: Post 5 is from 4 years ago and something may have changed in the way they do dynamic disks since then.

---

### Post by CharlesA on 2012-07-27
I asked someone and they said Linux support for dynamic disks is fairly limited and to use the build command and the chunk size has to match the size uses in Windows.

Personally I would just boot Windows and pull the data off that way.

---

### Post by wesleykins on 2012-07-27
Maybe...

This seems to be what I was looking for:
[http://forums.linuxmint.com/viewtopic.php?f=42&t=68232](http://forums.linuxmint.com/viewtopic.php?f=42&t=68232)

The following kernel options need to be installed:
```
1. Multiple devices driver support (RAID and LVM)
2. Device mapper support
3. Device mapper debugging support
4. Advanced partition selection
5.Windows Logical Disk Manager (Dynamic Disk) support
6. Windows LDM extra logging
```

Then you use dmsetup to mount the mapped device instead of mdadm.

Now I have to figure out how to recompile my kernel.

I'll report back.

-Wes

---

### Post by wesleykins on 2012-07-27
> **CharlesA said:**
> ...and the chunk size has to match the size uses in Windows.
which is??? nearly impossible to figure out.

> **CharlesA said:**
> 
Personally I would just boot Windows and pull the data off that way.

Easier said than done.  It's over 8TiB.  So I'd have to use Linux RAID volume, but then I couldn't access *that* in Windows.

Or I guess I could split all the data up among separate volumes.

Either way, it's no fun.

Thanks for your help, though.

---

### Post by rubylaser on 2012-07-27
> **wesleykins said:**
> which is??? nearly impossible to figure out.



Easier said than done.  It's over 8TiB.  So I'd have to use Linux RAID volume, but then I couldn't access *that* in Windows.

Or I guess I could split all the data up among separate volumes.

Either way, it's no fun.

Thanks for your help, though.

If you have this much data, I'd really suggest moving this to a fileserver and share your data to your Linux/Windows machines rather than trying to access this via dual boot.  In the long run, you are really risking the stability of this data going back and forth.  Also, if I may venture to say, a 7 disk span is terrifying.  You really need parity or something like unraid or mhddfs to prevent the loss of a single disk causing all of your data to be gone.

---

### Post by CharlesA on 2012-07-27
> **rubylaser said:**
> If you have this much data, I'd really suggest moving this to a fileserver and share your data to your Linux/Windows machines rather than trying to access this via dual boot.  In the long run, you are really risking the stability of this data going back and forth.  Also, if I may venture to say, a 7 disk span is terrifying.  You really need parity or something like unraid or mhddfs to prevent the loss of a single disk causing all of your data to be gone.
Huge +1 to file server. I am only running a 4TB RAID5 array, but if you are using 7 disks as a spanned volume, you would probably be better off running on RAID 5 or 6 array, either with mdadm or as ruby suggested, unraid.

Having that much storage space with no fault tolerance makes me nervous.

EDIT: FWIW, I attempted to build my file server off a Windows box originally, but found out it was way easier to deal with if it was running off *nix.

---

### Post by wesleykins on 2012-07-27
> **rubylaser said:**
> If you have this much data, I'd really suggest moving this to a fileserver and share your data to your Linux/Windows machines rather than trying to access this via dual boot.  In the long run, you are really risking the stability of this data going back and forth.  Also, if I may venture to say, a 7 disk span is terrifying.  You really need parity or something like unraid or mhddfs to prevent the loss of a single disk causing all of your data to be gone.

Yes, that's the plan!  But I've got to get it off first :)

This span is built on top of a hardware RAID 6 controller though.  I've survived multiple drive failures.  The only reason for the span is the 2TB limit in Windows.

I'm not planning on dual-booting, I'm planning on running only Linux and moving this to a server.

What do you guys think of [OpenMediaVault]("http://www.openmediavault.org/features.html")?

It's basically a Debian-based fork of FreeNAS.

---

### Post by wesleykins on 2012-07-27
Well what do you know, it works!

I spent the last 3 hours reading about compiling a custom kernel (to enable the LDM options and device mapper support I posted above), and got as far as running *make xconfig* on the kernel sources, only to find out that all the options I needed appear to be enabled by default.

Nothing showed up when I grepped for "ldm", as the instructions said, so I thought it wasn't enabled.

All I had to do was create the "table file" like so:

```
# Offset into   Size of this    Raid type       Device          Start sector
# volume             device                                          of device
0              4294961152       linear          /dev/sda1       0
4294961152     4294961152       linear          /dev/sdb1       0
8589922304     4294961152       linear          /dev/sdc1       0
12884883456    4294961152       linear          /dev/sdd1       0
17179844608    4294961152       linear          /dev/sde1       0
21474805760    4294961152       linear          /dev/sdf1       0
25769766912    596975337        linear          /dev/sdg1       0
```
...based on the info from
```
blockdev --getsize /dev/sda1
```
etc., etc.  (Notice that the "offset into volume" is the *sum* of the total device sizes so far... each time it gets incremented by 4294961152.)

Then I just typed:
```
dmsetup create winraid /etc/winraid
```
...and it mounted!

This is an array of 20, yes *twenty* 750GB hard drives in RAID 6 on a 3Ware 9650SE-24M8 card with hardware Xor and battery backup.  If I were running this without the RAID, I would have lost my data several times.

I had to break it into 7 fake volumes and run the silly span on top of it because MBR partitions are limited to 2TiB and Windows XP doesn't support GPT partitions.

But since the RAID 6 array is transparent to the OS, I didn't want to muddy the discussion with the details.

I did this several years ago, and I'm smarter now :)

Anyway, it WORKS.  Thanks so much for your help.

:guitar:

-Wes

---

### Post by CharlesA on 2012-07-27
Nice. Back that sucker up and migrate. ;)

As for FreeNAS vs OpenMediaVault. I dunno. I've never used either of them.

My server is built off Ubuntu 12.04. Kinda tempted to migrate to SI with KVM, but too lazy to deal with it atm.

---

