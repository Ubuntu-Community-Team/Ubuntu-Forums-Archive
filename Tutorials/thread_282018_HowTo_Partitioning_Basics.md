---
title: "HowTo: Partitioning Basics"
date: 2006-10-22
forum: Tutorials
---

### Post by bodhi.zazen on 2006-10-22
[SIZE=4]**Partitioning basics**[/SIZE]

[IMG]http://img213.imageshack.us/img213/9572/25226vw1.gif[/IMG][COLOR=navy]bodhi.[/COLOR][COLOR=darkgray]zazen[/COLOR]

This is a brief guide on partitioning intended as a brief introduction to partitioning terminology and some tips.

_UPDATE 11/30/06_ [COLOR=blue]Thank you ImmigrantUS for your critical review[/COLOR].

_UPDATE 1/02/07_ [COLOR=blue]Thank you Bulldog for your review and suggestions[/COLOR].

_UPDATE 9/08/08_ [COLOR=red]Please note: as of Ubuntu 7.10 all drives are labeled **sd**xy (the terminology hdxy is depreciated)[/COLOR].

_UPDATE 6/04/2012_ - Added information fro ext4.

_Primary, Extended, and Logical partitions_.

_Primary partitions_: The original partitioning scheme for PC hard disks allowed only four partitions, thus you are allowed up to 4 primary partitions. Linux numbers primary partitions 1-4.[INDENT][COLOR=darkred]_Note_: Some OSs (Windows, BSD) can ONLY be installed into a PRIMARY partition.[/COLOR]
Linux (and swap) can be installed into a primary or logical partition.[/INDENT]_Extended and Logical partitions_: To overcome this limitation, extended partitions are used. A single primary partition may "converted" into an "extended" partition which is then further divided into sub-partitions called logical partitions. Sorry you may not convert more then 1 primary partition into an extended partition. You then create logical partitions within the extended partition. It may be possible to create further extended partitions within an extended partition, although this becomes complicated and I am not sure of any advantage this offers.

Linux numbers Logical partitions starting with 5:  The numbers 1,2,3 and 4 are reserved for the primaries, even if you have just one primary partition. So if you make one primary partition and one extended extended partition with one logical partition:

The primary would be sda1
The entire extended partition (and any logical partition(s) it contains) would be sda2.
The logical partition within the extended partition would be sda5.

Clear as mud ?

_Naming of partitions_.

_Windows_: Windows uses lettering (c:\  ; e:\ , etc).

_Linux_: Linux uses /dev/hd[COLOR=red]x[/COLOR][COLOR=green]y[/COLOR] or /dev/sd[COLOR=red]x[/COLOR][COLOR=green]y[/COLOR] (most distros now use "/dev/sdxy", see below).

[COLOR=red]x[/COLOR] will be a letter starting with a, then b,c,....
[COLOR=green]y[/COLOR] will be a number starting with 1, then 2,3,....

Thus sda1 = First partition on the master HD.

_GRUB_.
Grub numbers drives starting with 0.
Grub also names partitions starting with 0.
Thus grub (sd0,0) = Linux sda1.

_Examples of partition names_.

_Note_: Names without a trailing digit refer to the whole disk, while names with a trailing digit refer to a partition of that whole disk.

Using sda as an example with multiple partitions:

/dev/sda = Entire HD

3 primary partitions:[INDENT]/dev/sda1 = First partition  = GRUB (hd0,0)[/INDENT][INDENT]/dev/sda2 = Second partition = GRUB (hd0,1)[/INDENT][INDENT]/dev/sda3 = Third partition  = GRUB (hd0,2)[/INDENT]3 logical partitions (Note you can have more then 3 logical partitions within an extended partition:
    
    -----

**_Note_: /dev/sda4 = Entire Extended partition. sda4 is "theoretical" in that it can not be mounted as such, but it "takes up a number".**[INDENT]**This is true for both Linux and grub speak !**[/INDENT]-----[INDENT]/dev/sda5 = fourth partition = GRUB (hd0,4)[/INDENT][INDENT]/dev/sda6 = fifth partition = GRUB (hd0,5)[/INDENT][INDENT]/dev/sda7 = sixth partition = GRUB (hd0,6)[/INDENT]_HD vs SD_.
[COLOR=red]As of Ubuntu 7.10 all drives are sd. This information is thus depreciated, and is available as a reference for those people using a version of Ubuntu previous to 7.10[/COLOR]

_IDE/ATA cable_ = hd[COLOR=red]x[/COLOR][COLOR=green]y
[/COLOR]
[LIST=1]
[*]Hard Drives[INDENT]/dev/hda  = Entire first HD, master drive on primary IDE cable.[/INDENT][INDENT]    /dev/hda1 = First partition on master drive.[/INDENT][INDENT]    /dev/hdb  = Entire second HD, slave drive on primary IDE cable.[/INDENT]
[*]CDROM/DVD[INDENT]    /dev/hdc  = Master CD on secondary IDE cable[/INDENT][INDENT]    /dev/hdd  = Slave  CD on secondary IDE cable[/INDENT]
[/LIST]


_SCSI devices_ = sd[COLOR=red]x[/COLOR][COLOR=green]y[/COLOR]
[LIST=1]
[*]SATA HD
[*]SCSI HD
[*]Zip drives[INDENT]**_Note_: Although they contain only 1 partition, zip drives are numbered "4".**[/INDENT][INDENT]**ie /dev/sda4.**[/INDENT]
[*]USB devices- both flash drives and hard drives.
[*]Firewire devices.
[/LIST]


_Floppy_[INDENT]/dev/fd0  = First FD.[/INDENT]_Basic partitioning scheme_.

Ubuntu (Linux) "requires" 2 partitions: / and swap. Both / and swap may be either Primary or Logical partitions.[INDENT]/ = root  min size 5 GB (Yes, I know you can go smaller if needed), 15-20 Gb may be better if you have the HD space.[/INDENT][INDENT]swap size[/INDENT][INDENT]
[LIST=1]
[*]RAM < 1 Gb swap = RAM X2.
[*]RAM > 1 Gb swap = 2 Gb
[/LIST]
[/INDENT][INDENT]Some claim a swap size of  > 1 Gb is excessive. The 2 Gb recommendation is "conservative".[/INDENT][INDENT][INDENT](If you boot more then 1 distro you should share the swap partition)[/INDENT][/INDENT]_Options_.

_/home_: This is helpful if you need to re-install Ubuntu. /home stores user data and user configuration files.

Limitations:
[LIST=1]
[*]/home does not save all of the installed applications you have installed or removed beyond the base install.
[*]If you boot multiple distros those user config files can conflict.
[/LIST]

_/data_:  This is helpful and I use this in favor of /home.

Why?
[LIST=1]
[*]First, I boot multiple distros and user configuration files in /home can conflict as above.
[*]Those user config files are not "mission critical" to back up. They will be regenerated if deleted, although you will loose your application preferences.
[*]Backup /home to /data and you can restore /home.
[*]Data partition can be shared with other OS (Windows or other distro's) easier then /home.
[/LIST]

You can, of course, mount your data partition as any name (mount point) you like.

[COLOR=blue]**Bulldog's Partitioning advice**[/COLOR]
> Some suggestions for disk partition.
Windows as big as you like.

Create an ext4 10GB for /
Create an extended from the rest off the space.
In the extended,
Create a /home 10GB
Create a swap 1GB
Create a ext4 partition for data if you have space left.
You have a separate /home for some data and a separate /data partition to backup important data.

I think a 10GB / partition is necessary to install programs without running out of space to soon.
Yes it can be 5GB or even less,but I think you shouldn't promote that one._Advanced partitioning_.
You can give each system directory a separate mount point. This includes:
/boot
/tmp
/var

This is not needed on a desktop install but is more common in server installs.

Adding /boot, /home, /var, and /tmp partitions can increase security.

For further reading, see References section below.

_Partitioning and formatting can be done from the CLI_:
This works well with new discs/devices and, IMO, is faster then GParted.
You can delete, create, and format partitions easily.
**The CLI will not resize or move a partition**, use Gparted.
The CLI will not format a partition with ntfs (windows XP). 

[How to Gparted, graphical guide]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

_Partitioning with fdisk_: It is easy and fast. IMO fdisk is more reliable then GParted, although Gparted is improving. The main problem I have had GParted is that it likes to re-number existing partitions which can then be fixed with fdisk.

Unmount the HD or USB device you want to partition or boot from a Live CD.

Then start fdisk:```
sudo fdisk /dev/sda
```_Basic fdisk syntax_:

[COLOR=blue]p[/COLOR] = [COLOR=blue]p[/COLOR]rint the partition table

[COLOR=green]n[/COLOR] = create a [COLOR=green]n[/COLOR]ew partition

[COLOR=red]d[/COLOR] = [COLOR=red]d[/COLOR]elete a partition

[COLOR=navy]q[/COLOR] = [COLOR=navy]q[/COLOR]uit without saving changes

[COLOR=red]w[/COLOR] = [COLOR=red]w[/COLOR]rite the new partition table and exit 

[Partitioning with fdisk]("http://tldp.org/HOWTO/Partition/fdisk_partitioning.html")
[New HOWTO: Linux Partition HOWTO]("http://linuxplanet.com/linuxplanet/tutorials/3174/1/")
[Linux Partition HOWTO]("http://www.linux.com/howtos/Partition/index.shtml")

_Format with the command line_: Syntax mkfs.<fs> <option_label> label_name <device>[INDENT]See also man mkfs.* (man mkfs.ext3)[/INDENT]_Note_: If you are installing Linux you can format the target (install) partition during the install process. In this case you do not need do do more then partition your HD.

_ext2_:```
mkfs.ext2 -L <label_name> <device>
```_ext3_:```
mkfs.ext3 -L <label_name> <device>
```_ext4_:```
mkfs.ext4 -L <label_name> <device>
```_reiserfs_:```
mkfs.reiserfs -l <label_name> <device>
```_reiser 4_:```
mkfs.reiser4 -l <Device>
```_jfs_:```
mkfs.jfs -L <label_name> <device>
```_xfs_:```
mkfs.xfs -L <label_name> <device>
```[INDENT][COLOR=darkred]_Note_: If you use xfs for your root partition you will need a separate /boot partition.[/COLOR]
/boot may be formated as ext2 (saves space)[/INDENT]_FAT_:```
sudo mkfs.vfat -n <label_name> <device>
```_Examples_:```
mkfs.ext3 -L data /dev/sda1
```Will format sda1 to ext3 and add a label "data". 

```
mkfs.ext4 -L data /dev/sda1
```Will format sda1 to ext4 and add a label "data". 

```
mkfs.vfat -n data /dev/sda1
```Will format sda1 to FAT32 and add a label "data".


_References_.
See this as a primer to more advanced partitioning: [Linux Partitioning Guide]("http://www.overclock.net/linux-unix-mac/11208-linux-partitioning-guide.html").

For a more detailed, "short" review see also: [A Short Guide to Partitioning a Hard Drive for a Linux System]("http://www.linuxquestions.org/linux/answers/Hardware/A_Short_Guide_to_Partitioning_a_Hard_Drive_for_a_Linux_System")

For a shorter, yet through discussion see: [Ubuntu Partitioning]("http://www.psychocats.net/ubuntu/partitioning")[COLOR=red] Thanks aysiu[/COLOR]

_GParted_: [How to Gparted, graphical guide]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

_fdisk_:
[Partitioning with fdisk]("http://tldp.org/HOWTO/Partition/fdisk_partitioning.html")
[New HOWTO: Linux Partition HOWTO]("http://linuxplanet.com/linuxplanet/tutorials/3174/1/")

[COLOR=navy]bodhi.[/COLOR][COLOR=darkgray]zazen[/COLOR]

---

### Post by Malakia on 2006-10-24
I think its an excellent guide about partions. I have notice a lot of question on how to partion my harddrive or something to do with partioning. Hopefully this will eliminate a lot of questions.

---

### Post by DJiNN on 2006-10-27
Hey, bodhi..... this is a most "Excellent" guide indeed, and one that i shall certainly be pointing a lot of people towards..... In fact, i'm gonna add it to my Sig right now! :)  Then i'm going to check out the fstab guide.... Which i shall be reading most intently! 

Got your PM by the way, shall be replying soon. In the UK at the moment, just setting up the new laptop.... it's awesome, and of course i have just downloaded the new Edgy release (Server & Desktop CD's) which i shall be installing on it asap! 

Well done again, and talk to you soon........ :-D

---

### Post by ric_spam on 2006-10-27
One technical add

[COLOR="Blue"]sdxy[/COLOR]  ie  sda1  notation will indicate [COLOR="Blue"]SATA[/COLOR] disks.  As these are becoming more popular, I think users will start to see the convention more often.

I have had problems with some older kernels with SATA - both hdd and dvd's.  Typically, you can boot the live/install cd/dvd but during installation the devices are no longer detected.  If you are running older kernels,  keep that in mind.

Then again, if you have a mainboard which supports SATA, you are probably running as new a kernel as possible.  Sorry, I know next to zero on compiling a kernel, so I can't suggest what may or may not help if you are trying to roll your own.


Thanks for this fine HowTo,

---

### Post by bulldog on 2007-01-03
Bookmarked for further reference,just as the fstab How To,you made again a very complete Tutorial.

Thanks.

---

### Post by chinx21 on 2007-06-18
Thank You! It's all I need! I've  been searhing for guides about partitioning. Good job!

---

### Post by hidinginthemountains on 2007-11-02
Great guide. Answered a lot of questions for me. It's bookmarked for future reference. Thanks!

---

### Post by danbar on 2007-11-15
When I installed gparted, I saw that I cannot format, resize etc.....my partitions.  All I can do is to Unmount, manage flags and information. What's wrong?

Secondly, it's taking to long to open the partition editor (scanning devices).  Is it normal in Ubuntu 7.10 ?

---

### Post by bodhi.zazen on 2007-11-15
> **danbar said:**
> When I installed gparted, I saw that I cannot format, resize etc.....my partitions.  All I can do is to Unmount, manage flags and information. What's wrong?

Secondly, it's taking to long to open the partition editor (scanning devices).  Is it normal in Ubuntu 7.10 ?

FYI, managing your partitions is best done from a live CD. You should not format or resize a mounted partition, so unmounting a partition should be the first step (which is why it is easier to run from a live CD).

Just a guess, but are you running gparted as root :

```
gksu gparted
```

---

### Post by Scavok on 2008-02-05
Very well done--thank you.

It would be nice to add a quick explanation of the file system types (ext2, ext3, jfs, xfs, etc.) and/or links to detailed references, along with a brief explanation of the features/advantages/benefits of each.

---

### Post by bodhi.zazen on 2008-02-06
> **Scavok said:**
> Very well done--thank you.

It would be nice to add a quick explanation of the file system types (ext2, ext3, jfs, xfs, etc.) and/or links to detailed references, along with a brief explanation of the features/advantages/benefits of each.

You are most welcome. Here is a link re: file systems :

[http://www.linux.com/feature/31939](http://www.linux.com/feature/31939)

[http://wiki.novell.com/index.php/File_System_Primer#File_System_Comparison](http://wiki.novell.com/index.php/File_System_Primer#File_System_Comparison)

Wikipedia also has a nice overview :

[http://en.wikipedia.org/wiki/Ext2](http://en.wikipedia.org/wiki/Ext2)
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

[http://en.wikipedia.org/wiki/ReiserFS](http://en.wikipedia.org/wiki/ReiserFS)
[http://en.wikipedia.org/wiki/Reiser4](http://en.wikipedia.org/wiki/Reiser4)

[http://en.wikipedia.org/wiki/JFS_file_system](http://en.wikipedia.org/wiki/JFS_file_system)

[http://en.wikipedia.org/wiki/XFS](http://en.wikipedia.org/wiki/XFS)

You will get a lot of opinions regarding file systems.

IMO / In my experience : Outside of benchmarking I do not see a noticeable performance difference between the file systems on a day-to-day general use desktop.

In selecting a file system, keep in mind reliability - what happens if things go wrong, any additional options, and compatibility (between operating systems). Just be careful when you read the "benchmarks" as they are certainly not the full story.

If you use XFS on your root system, grub can not boot xfs, so you need to either use lilo or set up a (ext2) boot partition.

Personally I use ext3 as IMO it is the most reliable / stable (although I am sure not everyone would agree, as you can see in the comments in some of those links). You should do just fine with ReiserFS, JFS, XFS, or Ext3 (these 4 are all quite solid and reliable IMO). Reiser4 and ext4 are up and coming, I do not have any direct experience with either.

---

### Post by egalvan on 2008-05-12
Why can I not see the 'THANK YOU" tags on this thread?
This occasionally happens, haven't seen a pattern to the disappearance yet.

Anyway, 
A big THANK YOU for this thread.
Most useful.

An off-line edition would be ever so useful, such as a .pdf type.

---

### Post by bodhi.zazen on 2008-05-12
> **egalvan said:**
> Why can I not see the 'THANK YOU" tags on this thread?
This occasionally happens, haven't seen a pattern to the disappearance yet.

Anyway, 
A big THANK YOU for this thread.
Most useful.

An off-line edition would be ever so useful, such as a .pdf type.

This is an old thread, from the time before the "thanks" button.

Thank you for your reply though, that took longer then hitting a button.

---

### Post by dvdragon on 2008-06-25
Thank you for this amazing guide. It gives novices and experts what they need.:guitar:

---

### Post by imjscn on 2008-06-26
Thanks for the great Guide! I followed this guide and successfully installed Xubuntu. Now I wish to view the Partition Table to see if everything is alright. but in my Application/System menue, there isn't an "Administrator" entry. Where else I can find this entry? or, is there another way to view the Partition Table in Xubuntu?

---

### Post by bodhi.zazen on 2008-06-27
The two methods are to use the command line (terminal) and gparted.

gparted is on the live CD but is not installed (you can install it if you wish).

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

Open a terminal and type :

```
sudo fdisk -l
```

---

### Post by imjscn on 2008-06-27
thanks! fdisk-l shows all the patitions but not mount point. I wish to see both mount points and patitions, is there a way?

---

### Post by ssican on 2008-07-12
**imjscn**, GParted 0.3.5 show partitions and mount points.
Install GParted, or make use of GParted on LiveCD.
On Ubuntu 8.04 GParted is at: System > Administration > Partition Editor(GParted).
On Xubuntu 8.04 GParted is at: Applications > System > Partition Editor.

---

### Post by bodhi.zazen on 2008-07-12
> **imjscn said:**
> thanks! fdisk-l shows all the patitions but not mount point. I wish to see both mount points and patitions, is there a way?

You can issue the mount command :

```
mount
```

Or 

```
less /etc/fstab
```

---

### Post by Blackbeard1313 on 2008-07-31
Just wanted to say Thank You for this excellent post! I just tried out Linux for the first time about 5 days ago and Windows is now very lonely as I haven't used it since. This will be a big help as I am now going to replace Windows with Ubuntu.

---

### Post by btate on 2008-08-02
totally new to ubuntu so bear with me :)

I've installed ubuntu in a dual boot mode, everything is fine. So well in fact that I want to clean windows out and use the total hard disk for ubuntu or other distros.

I've managed to get Gparted to delete enough of my windows so it won't boot there. I've tried to Delete, Move, etc etc and get the drive cleaned up but to no avail.

the current situation is thus:
/dev/sda1    ext3           39.07 GiB    used 491.65 Mb
             unallocated    39.06 GiB
/dev/sda2    extended       70.92 GiB
/dev/sda5    ext 3          29.29 GiB     used 409.04 Mb
/dev/sda6    ext 3    /     40.19 GiB     used   3.19 Mb
/dev/sda7    Lnx swap        1.4  GiB

What I'm looking for is a quick and easy way to dump everything and start anew with a new linux install.

I realize that 40+ GiB is plenty probably I would just like to clean up my mess. As I've not got into adding a whole lot of stuff to the original distro, now is probably the time to do it.

I would appreciate any help for this dummy.

B

---

### Post by collinp on 2008-08-02
An excellent guide, I learned a few things from this :).

---

### Post by bodhi.zazen on 2008-08-02
what is it you would like your partitions to look like then ?

One tip I would give you, you should manage your partitions from a live CD.

---

### Post by btate on 2008-08-02
I've no idea to tell you the truth. I figured the distro would make the best of 140 GiB of space.

I would like extra (unallocated space) for future stuff so probably 40 percent to the current useage. 

maybe some day I will try and install a file server but that is waaaay down the road.

B

---

### Post by bodhi.zazen on 2008-08-02
LOL, use gparted :

Documentation: [Gparted Documentation]("http://gparted.sourceforge.net/documentation.php")

keep in mind, this is not a support thread so if you have additional questions, best start a thread in ABT or General Help.

---

### Post by prabath_fun on 2008-08-05
Thanks. Excellent guide on partitions.
Prabath

---

### Post by gabhla on 2008-12-26
This happens to be one of the problem area for me.  For some unknown reason I keep needing to be reminded of even the basics of partitioning, although I've done it sucessfully several times.  So, this very complete and helpful How To.  Thanks.  

Just got a new computer and, of course, it has Vista.  I've been using only Linux for so I forgot how Windows works.  So, getting the hard drive ready for Ubuntu, need to partition.

---

### Post by -kg- on 2009-01-02
A quick correction to your HOWTO:

I noticed the statement:

> A single primary partition may "converted" into an "extended" partition

near the beginning.  You can't convert an existing Primary partition to an Extended partition.  The only things you can do to a Primary partition is create it, reformat it to another file system, resize it, move it, or delete it.

Like a Primary partition, the only way you can make an Extended partition is to create it in Unallocated space.  If you already have 4 Primary partitions, in order to comply with the "4 Primary partition rule," you will have to delete one of the Primary partitions in order to create the Extended partition.

Once you have the Extended partition, of course, you can create a large number of Logical partitions within it (to a limit, of course, but a normal user shouldn't have to worry about reaching that limit).

Also:

> It may be possible to create further extended partitions within an extended partition, although this becomes complicated and I am not sure of any advantage this offers.

No, you can't create more than one Extended partition on a hard drive, and you can't create an Extended partition within an Extended partition.  The only thing you can create within an Extended partition are Logical partitions.

And you're right...it would offer no advantage, unless one faced the possibility of creating over 60 (I believe?) Logical partitions, which is as many as Linux will handle.  Other operating systems will handle even less, but it's not very likely that a normal person will come anywhere near that many (of course, I have intimate knowledge of such a person, but...*Don't look at me that way!*) ;)

<Now for a shameless plug! :P >

More information on Partitioning can be found at:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by betternotwriteme on 2009-02-12
awsome. very good guide. i have been using linux for a while, and hadnt fully understood the naming structure of the disks and partitions.

---

### Post by Andreas1 on 2009-02-13
i have once heard that performance may depend on the position of the partition on the harddrive, someone told me this was the reason why the swap partition is positioned at the end, elsewhere i read that the partitions at the beginnig are faster.

is there something to this?

---

### Post by bodhi.zazen on 2009-02-13
> **Andreas1 said:**
> i have once heard that performance may depend on the position of the partition on the harddrive, someone told me this was the reason why the swap partition is positioned at the end, elsewhere i read that the partitions at the beginnig are faster.

is there something to this?

yes , it has to do with the mechanics of the hard drive and how far the heads have to move.

The reality with new computer is that you are very unlikely to notice any appreciable increase in speed on day to day applications and you need to run benchmarks to detect the difference in speed.

Benchmarks are, for example, how much time does it take to fist make 10,000 1 Kb files and then delete them ? The activities performed on benchmarks are designed to test the I/O to disk and are not what "normal" people do on a desktop (desktop users say open 10 applications and run copmiz).

---

### Post by choben on 2009-06-28
Great guide but maybe too much to chew :confused: for some ultra-novices. I'm already familiar enough with the concepts so this help clear things up for my microsoftened brain. :)

---

### Post by hissyfut on 2009-07-08
> **bodhi.zazen said:**
> 
[INDENT](If you boot more then 1 distro you should share the swap partition)[/INDENT]

I was asked this the other day. How do you set windows to use a swapfile in another partition, and how should the partition be formatted?

---

### Post by Sepanderi on 2009-07-10
> **hissyfut said:**
> I was asked this the other day. How do you set windows to use a swapfile in another partition, and how should the partition be formatted?

I thought that only meant that Linux distros should use the same swap partition. :confused:

You can set Windows swap file from the control panel. In XP, that's Start -> Control Panel -> System -> Advanced -> Performance Settings -> Advanced -> Virtual Memory. There you can set the size and partition of the paging file.

Anyway, thanks for the nice guide. :)

---

### Post by jw5801 on 2009-07-10
> **Sepanderi said:**
> I thought that only meant that Linux distros should use the same swap partition. :confused:

You can set Windows swap file from the control panel. In XP, that's Start -> Control Panel -> System -> Advanced -> Performance Settings -> Advanced -> Virtual Memory. There you can set the size and partition of the paging file.

Anyway, thanks for the nice guide. :)

If you want Windows to use your Linux swap partition as it's paging file you can follow [this neat little guide](http://ubuntuforums.org/showthread.php?t=245393).

---

### Post by Vincent_Lin on 2009-07-25
Hi,

Sorry to ask question like this.

I accidentally delete an xfs partition using gparted.  Is there a way to "restore" it back?

The mistake happened because I was adding another USB external HD and thought the disk and partition was the one added (since the deleted one is also a USB external disk).

sort of like USB bus swapped /dev/sdd and /dev/sdc after a reboot and that caused the confusion.

Can anyone make some sensible suggestions?

Thanks.

Have a great weekend,

Vincent Lin

---

### Post by Dullstar on 2009-07-25
I must ask if you have any backups.  If you don't have a backup, then sorry, nothing I can do to help.

---

### Post by bodhi.zazen on 2009-07-25
If you know the exact geometry you can use fdisk.

If you do not know what fdisk is, go for testdisk (it is in the repositories)

[http://members.iinet.net.au/%7Eherman546/p21.html](http://members.iinet.net.au/%7Eherman546/p21.html)

---

### Post by Vincent_Lin on 2009-07-26
Thanks guys.

I apt-get testdisk and it brought in photorec as well.

I ran photorec first, hoping to retrieve files.  Well it did, as the ducuments said, but those restored files were renamed.  Well, there are also ways to "process" these restored files back to "usable" states, as documented in this link:

[http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)

Before I jumped in and spend time organizing those restored files, I went ahead to run testdisk, as I was equipped with the contents of those restored files.  The worst then was already planned.

The result was a total surprise - the partition (xfs) was restored perfectly by testdisk - as if the partition was not removed at all.  Got to find some time to delete those restored files :)

I am impressed.  And I am also very grateful.

Thanks guys.  

Have a nice weekend,

Vincent

---

### Post by godspiral on 2009-11-02
thank you for howto, a couple of questions though:

* if ntfs volume defrags with a hole in the middle, can gparted still shrink almost all of the unused space?

I'd like to install partly to a 2nd HD, and partly to USB drive.  (I already have an 8.04 install on the USB as ext3, but can't use it with desired computer due to bios that can't boot usb)

I'd like to put home, swap and tmp on USB drive, and rest on internal in order to minimize space on HD.

*Could such a system boot without the usb plugged in?
*Can all /home /tmp /data mount points use the same USB partition?
*Can HD use ext4 while USB ext3?
*Would you suggest more to be offloaded to USB?
*Can a wubi install use ext3 partitions for certain mount points?

---

### Post by godspiral on 2009-11-02
> **godspiral said:**
> thank you for howto, a couple of questions though:

* if ntfs volume defrags with a hole in the middle, can gparted still shrink almost all of the unused space?



gparted can indeed free up most of this space, and chkdsk doesnt complain on xp

---

### Post by jw5801 on 2009-11-02
> **godspiral said:**
> thank you for howto, a couple of questions though:

* if ntfs volume defrags with a hole in the middle, can gparted still shrink almost all of the unused space?

As you've discovered, yes it can.

> I'd like to install partly to a 2nd HD, and partly to USB drive.  (I already have an 8.04 install on the USB as ext3, but can't use it with desired computer due to bios that can't boot usb)

I'd like to put home, swap and tmp on USB drive, and rest on internal in order to minimize space on HD.

You can do this using your /etc/fstab (check man fstab for useful info).

> *Could such a system boot without the usb plugged in?

Yes, but you wouldn't be able to log in, as your user's home directory would not exist.

Also, the /tmp folder would still exist, so things would be written into it, which may mean that you will be unable to mount /tmp on reboot, depending on whether /tmp gets cleared before or after filesystems are mounted. It should most definitely be after, which would mean it wouldn't get mounted, as you cannot mount anything to a non-empty directory.

> *Can all /home /tmp /data mount points use the same USB partition?

Yes, however two of the directories would need to exist in two places, ie. if you had a partition for home, you could create /home/tmp and /home/data on that partition, then either create a symlink to the proper place in the filesystem, or use the 'bind' option to 'mount' the subdirectory into the correct place in the filesystem.

> *Can HD use ext4 while USB ext3?

Of course, provided you tell the system what each partition is (in /etc/fstab).

> *Would you suggest more to be offloaded to USB?

As mentioned earlier, putting things like /home and /tmp on an external device that may or may not be there is not a particularly good idea. A data partition would be perfectly fine to offload, but things like /home, /tmp, /var, /usr, /lib, /etc, etc, are needed by the system, and will render your system rather unusable if they are not present.

If the external device will always be there, then you can put whatever you want there. I have several complete installs on external hard drives which I use for testing things.

> *Can a wubi install use ext3 partitions for certain mount points?

I don't know much about wubi, but I can't see why not, once the linux kernel is booted, you can mount whatever you want, wherever you want, provided the kernel has the tools (modules) to recognize the filesystem, which it does for pretty much everything.

---

### Post by cmarley on 2010-01-04
Bodhi said in the begining of this post that it was useful to make a /data partition in order to back up files. Is this done automatically or do I have to download an application or just do it manually? If it is any of those three items; then how do I do it?

Thanks!

Also, I have been trying all sorts of different partiioning schemes for a dell latitude d600. this is not a very powerful machine and with one partition scheme I got everything to run as smooth as windows. well, i deleted windows entirely and have been trying to find that magical scheme again. 

Here is what I have in the order that they are presented on the partition manager install screen:

10 GB for /
800 MG swap
14 GB /home
800 MB swap
the rest GB /data

This final iteration has not completed its install just yet...but should that work? Thanks all!

---

### Post by bodhi.zazen on 2010-01-05
> **cmarley said:**
> Bodhi said in the begining of this post that it was useful to make a /data partition in order to back up files. Is this done automatically or do I have to download an application or just do it manually? If it is any of those three items; then how do I do it?

Thanks!

Also, I have been trying all sorts of different partiioning schemes for a dell latitude d600. this is not a very powerful machine and with one partition scheme I got everything to run as smooth as windows. well, i deleted windows entirely and have been trying to find that magical scheme again. 

Here is what I have in the order that they are presented on the partition manager install screen:

10 GB for /
800 MG swap
14 GB /home
800 MB swap
the rest GB /data

This final iteration has not completed its install just yet...but should that work? Thanks all!

It appears from your post as if you know how to make partitions on your hard drive, but if not simply use gparted on a live CD.

You have two swap partitions, but otherwise your partitioning scheme is fine. It is more a art then science.

Let us assume 

/dev/sda1 = 10 Gb = /
/dev/sda2 = 800 Mb = swap
/dev/sda3 = 14.8 Gb = /home
/dev/ssda4 = the rest = your data partition.

After partitioning the HD I always reboot =)

Install Ubuntu, as you install use manual partitioning, assign /dev/sda4 to a location, /media/data or /media/music or whatever you like.

If you do not assign it during installation, then you will need to add an entry in fstab :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by SoFl W on 2010-06-23
> **bodhi.zazen said:**
> 
[Linux Partition HOWTO]("http://www.linux.com/howtos/Partition/index.shtml")


I don't believe that is a valid link

---

### Post by bodhi.zazen on 2010-06-23
> **SoFl W said:**
> I don't believe that is a valid link

Looks dead to me as well, removed it.

---

### Post by COKEDUDE on 2010-07-30
I have a partition I want to format. How do I know if I want to use the -n or -L? 

```
mkfs.ntfs -L data /dev/sda1
```
```
mkfs.ntfs -n data /dev/sda1
```

---

### Post by bodhi.zazen on 2010-07-30
Read the man page :twisted:

What do you want to do ?

>      -L, --label STRING
              Set the volume label for the filesystem.


     -n, --no-action
              Causes mkntfs to not actually create a filesystem,  but  display
              what it would do if it were to create a filesystem. All steps of
              the format are carried out except  the  actual  writing  to  the
              device.-L labels the partition . From the man page I do not understand when one would use the -n option ???

---

### Post by webbdawg on 2010-08-01
I have an old laptop  hd that I put in a case and used as a usb drive. I can see the drive in Dolphin and all it's contents.

I want to remove the partitions and format it to a clean drive. 

I can find no utilities in Kubuntu to do this. I have looked everywhere.

How does one go about formatting external drives?

---

### Post by bodhi.zazen on 2010-08-01
> **webbdawg said:**
> I have an old laptop  hd that I put in a case and used as a usb drive. I can see the drive in Dolphin and all it's contents.

I want to remove the partitions and format it to a clean drive. 

I can find no utilities in Kubuntu to do this. I have looked everywhere.

How does one go about formatting external drives?

Personallt I use the command line

```
mkfs.ext4 /dev/sdb1
```

If you prefer a gaphical interface, install gparted.

---

### Post by hello2012 on 2010-09-10
[SIZE=3][FONT=Times New Roman] I partition my basic disk through the Partition Assistant, and I think this is the good software, not only has many features about hard drive partition, but also worked well , it has free edition, we can choose to experience its superiority in advance. And maybe you will have the same feeling if you use it, so, here, I introduce you a detail article about partition resize, create, format, and delete-- Guidelines on [COLOR=black][COLOR=red][COLOR=black][how to partition a hard drive]("http://www.extend-partition.com/resource/how-to-partition-a-hard-drive.html")[/COLOR][/COLOR] by Creating, Deleting, Formatting and Resizing Partition.[/COLOR] Go and read it.[/FONT][/SIZE]

---

### Post by bodhi.zazen on 2010-09-10
> **hello2012 said:**
> [SIZE=3][FONT=Times New Roman] I partition my basic disk through the Partition Assistant, and I think this is the good software, not only has many features about hard drive partition, but also worked well , it has free edition, we can choose to experience its superiority in advance. And maybe you will have the same feeling if you use it, so, here, I introduce you a detail article about partition resize, create, format, and delete-- Guidelines on [COLOR=black][COLOR=red][COLOR=black][how to partition a hard drive]("http://www.extend-partition.com/resource/how-to-partition-a-hard-drive.html")[/COLOR][/COLOR] by Creating, Deleting, Formatting and Resizing Partition.[/COLOR] Go and read it.[/FONT][/SIZE]

Thanks for the link, but that is a windows application. Personally I do not use windows, perhaps it will help others. consider posting on a windows forum.

---

### Post by Buntu Bunny on 2010-09-14
Excellent tutorial Bodhi.Zazen.  Very much appreciated.

---

### Post by bodhi.zazen on 2010-09-14
> **Buntu Bunny said:**
> Excellent tutorial Bodhi.Zazen.  Very much appreciated.

Glad it helped =)

---

### Post by vedavrata on 2010-09-21
Thank you! Very useful!

---

### Post by xyepblra on 2010-12-28
Do I necessarily have to run gparted from liveCD? Can't I simply run it from within the system?
I deleted my Vista partition, so now I'd like to dedicate the space I thus free-up to my /home location, which contains a 12 GB vmware folder with a WinXP beast caged in it. Besides, I use a lot of disk space for my mail and documents, so I would like to ask an advice from experienced users on how to redistribute the space aiming the productivity increase and increase of /home folder.
My current situation is as following (disk space figures are in GBs):

/dev/sda1		ext4			58,6	1,10 (*former VISTA*)
/dev/sda2		extended		164,96
	/dev/sda5	linux-swap		1,86
	/dev/sda8	ext4	/		23,29	6,58
	/dev/sda9	ext4	/home		23,28	20,86
	/dev/sda6	ntfs	/media/DATA	38,84	29,10
	/dev/sda7	ntfs	/media/MV	77,69	57,36
/dev/sda3		ntfs			9,32	6,56 (*HP recovery partition*)

Can I simply move my /home content from /dev/sda9 to /dev/sda1? Will my system boot up then? Can I shrink the current root partition to, let's say, 12 GB? Is safe restart guaranteed in that case?

Thus and so, please advise what should I do before I mess up my beloved Ubuntu.

---

### Post by lkraemer on 2010-12-28
bodhi.zazen,
GREAT HOWTO:.........THANKS......

I have a small question that may be appropriate to add to the end 
of the HOWTO: to help us in the near future..............

If I've been running my system and suddenly I suspect there may be a problem
with a specific partition,... How do I Test and Verify that the partition is good?
Are there other tests that can be run on the Partition other than fsck & e2fsck?
Under what circumstance do I use fsck vs e2fsck?  Maybe a few CLI samples would
be appropriate as I've not run across those yet either.  How often should I run
fsck on my partition, or should I even attempt it?

THANKS.

lk

---

### Post by Roberto S Cabrera on 2011-05-31
Needless to say that this is a great guide for a neophyte, as I am. my dilemma is that I need to use Windows (xp or 7) and want to grow my knowledge and dexterity of Linux Ubuntu 10.04 LTS, hence I want to be able to dual boot. The challenge is doing this in a Dell Inspiron 910 Netbook with 16 GB HD. **How do I best devi-up the drive?** Please can you provide some suggestions.

---

### Post by psusi on 2011-05-31
> **Roberto S Cabrera said:**
> Needless to say that this is a great guide for a neophyte, as I am. my dilemma is that I need to use Windows (xp or 7) and want to grow my knowledge and dexterity of Linux Ubuntu 10.04 LTS, hence I want to be able to dual boot. The challenge is doing this in a Dell Inspiron 910 Netbook with 16 GB HD. **How do I best devi-up the drive?** Please can you provide some suggestions.

I didn't even think Windows 7 could be installed on such a small drive.  How much free space do you have?  You will need at least 5 gb for Ubuntu, so that drive may just be too small.

If you have at least 5 gb of free space, then just go with the default side-by-side install.

---

### Post by Roberto S Cabrera on 2011-05-31
To address your inquiery - I'll be installing a "Light" Windows 7 w/ the help of vLite & WAIK. However, I do not know what you mean with "default side-by-side install", would you please explain or point me in the direction to read about it. :confused:

Thank you!

---

### Post by psusi on 2011-05-31
I mean just pick the side-by-side install option and let the installer worry about the partitions.

---

### Post by Parvaaz^^ on 2011-06-01
A great, useful article, well written. 
Thank you for sharing with us.

---

### Post by jannytra on 2011-06-01
Thank you very much for this detailed description of partitions :) I am new to Linux, just preparing to try it out dual-booting with Windows 7 and I needed to know, how to arrange my partitions :) and this was great guide, thank you :)

---

### Post by ubun2warrior on 2011-12-30
can i dual boot ubuntu with windows with an lvm implementation and also can i install another linux os after that on the single hard disk that i have with lvm implementation and, my data remains safe..

pls suggest

---

### Post by bodhi.zazen on 2011-12-30
> **ubun2warrior said:**
> can i dual boot ubuntu with windows with an lvm implementation and also can i install another linux os after that on the single hard disk that i have with lvm implementation and, my data remains safe..

pls suggest

If your data is valuable to you, back it up.

As long as you understand the partitioning scheme you can do all the things in your post.

---

### Post by leotan1041991 on 2012-04-19
about the choosing of primary, logical or extended partition. which is a best partition for each /, /swap, /home and why? is it ok if i will make them into all primary partitions?

---

### Post by bodhi.zazen on 2012-04-19
> **leotan1041991 said:**
> about the choosing of primary, logical or extended partition. which is a best partition for each /, /swap, /home and why? is it ok if i will make them into all primary partitions?

AFIK, does not matter.

---

### Post by techvish81 on 2012-06-04
thank you for this great & helpful guide, 
i want your updated opinion on ext4 when all(most) distros are now using it as default . secondly what will be the best scheme if i'm going to use my system as only single os (ubuntu or any derivative)?

---

### Post by nicolasforum89 on 2012-06-04
Always helpful to read before any big mistakes.

Thank you.

---

