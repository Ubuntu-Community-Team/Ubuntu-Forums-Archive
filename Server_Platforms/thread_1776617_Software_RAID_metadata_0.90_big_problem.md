---
title: "Software RAID metadata 0.90 big problem"
date: 2011-06-06
forum: Server Platforms
---

### Post by jgoris on 2011-06-06
Hi All,

I've made a blunder using software RAID with metadata version 0.90 and component devices over 2TB in size.

I recently upgraded a system running 6 x 2TB HDDs with a new EFI motherboard and 6 x 3TB HDDs. The process took a while, but was successful. The final step in the process was growing /dev/md1 from 9.4TB to about 14TB. I did this two weeks ago and all was fine until late yesterday. I'm using the system for MythTV and watching live TV became very jittery. I remembered I had not rebooted since the last kernel upgrade and did so then. The system booted back up to a point, but could not mount a couple of file systems. After a fair bit of trouble shooting I determined that the problem was due to using software RAID metadata version 0.90 with component devices over 2TB. When using component devices over 2TB then metadata version 1, 1.0, 1.1 or 1.2 should be used. Here are the details of /dev/md1:

```
# mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90
  Creation Time : Wed May 20 17:19:50 2009
     Raid Level : raid5
     Array Size : 3912903680 (3731.64 GiB 4006.81 GB)
  Used Dev Size : 782580736 (746.33 GiB 801.36 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Tue Jun  7 02:19:18 2011
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 256K

           UUID : 6650f3f8:19abfca8:e368bf24:bd0fce41
         Events : 0.6539960

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3
       2       8       67        2      active sync   /dev/sde3
       3       8       51        3      active sync   /dev/sdd3
       4       8       35        4      active sync   /dev/sdc3
       5       8       83        5      active sync   /dev/sdf3

```And here is the partitioning layout of each drive. Note: have to use parted to support GUID partition table required for booting on drives over 2.1TB.

```
# parted /dev/sda print
Model: ATA Hitachi HDS72303 (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  1066kB  1049kB                     bios_grub
 2      1066kB  207MB   206MB   ext3               raid
 3      207MB   3001GB  3000GB                     raid

```It appears that software RAID now sees the devices as 0.8TB each instead of 2.8TB each. I'm presuming that it has dropped off the last 2TB of each device.

Note that my system has LVM on top of /dev/md1. Fortunately the root and swap filesystems are intact so the system does boot okay, with the exception of not being able to activate the /dev/mapper/radagast-media and /dev/mapper/radagast-mythtv logical volumes.

```
# dmsetup ls
radagast-root   (251, 0)
radagast-swap   (251, 1)
radagast-media  (251, 2)
radagast-mythtv (251, 3)

```Does anybody know of the best way to salvage the data on radagast-media. I presume that the data is still there and I just need some way of accessing it. My gut feeling tells me that I should boot using the rescue disk, grow the array using mdadm --grow to the maximum size to use the full 14TB again, then attempt to activate the logical volumes. I'm not sure if this will corrupt any of the data on /dev/md1. eg, will the superblocks be put in the same spot or will they go in new spots and overwrite some data?

If this process works then I can backup my data, rebuild the array using metadata 1.2, restore and away I go.

On an aside, is there a bug here? At the least, should mdadm warn that attempting to grow with component devices greater than 2TB in size using metadata version 0.90 should not be done.

---

### Post by YesWeCan on 2011-06-06
Ugh.

```
     Array Size : 3912903680 (3731.64 GiB 4006.81 GB)
  Used Dev Size : 782580736 (746.33 GiB 801.36 GB)
```
I notice that you say the original array size was 9.4TB and the array now says it is 4TB. This suggests over half your original RAID space is inaccessible.

Complete guess theory: the 0.90 format has 4 bytes for the sectors used on a drive and the 1.0+ formats have 8 bytes. This is why 0.90 is limited to 2TB (4 bytes max count of 512-byte sectors). So after it grew the array size to 14TB it then wrote the new sector size, which now exceeds 4 bytes, to a 4-byte location...did it simply truncate it? So the size now recorded in the superblocks is the truncated version of the real size.

What you do about this I shudder to think. An immediate thought is to manually modify the sector size counts in each superblock to the original values before you grew the array. You could do this using dd. Whether that would "free up" the lost space and allow you to get some of your data back is only a guess on my part.

Whether there is a slick way to do this using mdadm commands is beyond my expertise.

It is tempting to do a "grow" with "assume clean" but I personally don't know enough about how this works to recommend it. Personally, I'd trial it in a virtual machine first but you may not have that option.

---

### Post by YesWeCan on 2011-06-06
> On an aside, is there a bug here? At the least, should mdadm warn that attempting to grow with component devices greater than 2TB in size using metadata version 0.90 should not be done.
I certainly would have expected mdadm to refuse to grow an array beyond its own metadata limits. Sigh.

---

### Post by YesWeCan on 2011-06-06
This works in VirtualBox using Mint 11.
All data was preserved:
1) Zero all the superblocks
2) Recreate the array with the original metadata type -> If you change the metadata type the partition is wiped.

```
sudo mdadm --stop /dev/md0
sudo mdadm --zero-superblock /dev/sd[abcdef]1
sudo mdadm --create /dev/md0 --metadata=0.90 --assume-clean --verbose --level=5 --raid-devices=6 /dev/sd[abcedf]1
```

mdadm *appears* to be able to reconstruct the superblocks from the existing data. I'd get a second opinion ;). If true, then this should restore your array to its original size.

[edit]
One thing I just noticed is that in your --detail it says the version is 00.90 not 0.90. In mine is says 0.90. Does this matter?
My mdadm is: [COLOR="Blue"]mdadm - v3.1.4 - 31st August 2010[/COLOR]

---

### Post by jgoris on 2011-06-06
YesWeCan, thanks for all your help.

Not only is it disappointing that mdadm allowed the array to grow beyond its own metadata limits, it's disappointing that 0.90 is still the default metadata type. I suppose it is the most compatible and I know Grub can only boot off software RAID when using 0.90 (which I am doing with a separate array for /boot), but it would be nice if Ubuntu would default to 1.x when creating large RAID arrays, or give you the option to choose what Metadata to use given that it is not possible to change the metadata version at a later date.

I read about metadata versions after I'd created the array when it was too much effort to change. Then I forgot about it when I grew the array. I remember thinking that I must create a new RAID array with the additional space if I ever replaced the 2TB drives with larger drives and make this a new physical volume for LVM, but forgot about it a year or so later.

It makes sense what you say about having 4 bytes (2^32) used for the count of 512 byte sectors and this giving the limit of 2TB. What amazes me is that after the RAID grew to 14TB it worked fine for 2 weeks until the reboot. I'd definitely been using more than 10TB within 1 day of the grow operation and have been putting more files on there every day. I had not had any problems accessing any of the new files. Admittedly, there are (or should that be were) a huge number of files on there and I probably barely looked at 1% of them. I do know that I was creating lots of new files whilst ripping my CD collection to FLAC and they were all playing absolutely fine. Exactly where that data was written to will be interesting to find out.

My mdadm version is [COLOR=Blue]mdadm - v2.6.7.1 - 15th October 2008[/COLOR] and I'm running Ubuntu server 10.04 64-bit. It's strange that it reports version 00.90. I definitely won't be trying to update mdadm at this point. I think reporting 00.90 instead of 0.90 is fine.

Regarding recreating the array using the --assume-clean, I think you are right and this is the best way to go about it. However, is there really a need to zero the superblock of the existing array first. I assume that creating the new array will overwrite it anyway, but if the create command fails, I don't want to lose my OS.

Finally, after recreating the new array it will have a different UUID to the original array. Will this create any problems booting? Do I need to simply update /etc/mdadm/mdadm.conf with the new UUID (via mdadm --detail --scan) or should I manually modify the UUID of the new array (via mdadm --assemble --update uuid=...). Note that I'm not very confident with updating the UUID whilst assembling the array as I think that when the array is assembled that is when the problem with failing to understand the proper array size will reoccur.

---

### Post by YesWeCan on 2011-06-07
> **jgoris said:**
> Not only is it disappointing that mdadm allowed the array to grow beyond its own metadata limits, it's disappointing that 0.90 is still the default metadata type. I suppose it is the most compatible and I know Grub can only boot off software RAID when using 0.90 (which I am doing with a separate array for /boot), but it would be nice if Ubuntu would default to 1.x when creating large RAID arrays, or give you the option to choose what Metadata to use given that it is not possible to change the metadata version at a later date.
Yes.
It shows up a weakness in the collage that is linux: a change to mdadm metadata should have triggered a change to Grub2.
I would also like to see an mdadm command to update the metadata format from 0.90 to 1.x
But most of all I would like to see a professional user guide for mdadm. I find myself bleating about this so often that I am beginning to wonder whether it is incumbent upon me to write one. I really think the designer(s) should take responsibility.

> It makes sense what you say about having 4 bytes (2^32) used for the count of 512 byte sectors and this giving the limit of 2TB. What amazes me is that after the RAID grew to 14TB it worked fine for 2 weeks until the reboot. I'd definitely been using more than 10TB within 1 day of the grow operation and have been putting more files on there every day. I had not had any problems accessing any of the new files. Admittedly, there are (or should that be were) a huge number of files on there and I probably barely looked at 1% of them. I do know that I was creating lots of new files whilst ripping my CD collection to FLAC and they were all playing absolutely fine. Exactly where that data was written to will be interesting to find out.
That is intriguing. Again, guessing, it may be that before you rebooted the system had no idea that it was only 4TB because this limit existed only in the metadata parameter, which may not be read until reboot or reassembling the array. After reboot the RAID reassembled as 4TB and this broke LVM.

> Regarding recreating the array using the --assume-clean, I think you are right and this is the best way to go about it. However, is there really a need to zero the superblock of the existing array first. I assume that creating the new array will overwrite it anyway, but if the create command fails, I don't want to lose my OS.
Good point. I didn't really think about it. I suppose I didn't want any existing data to be able to influence it - in case it checked it first. But I have no idea how it works (re: earlier bleat).

> Finally, after recreating the new array it will have a different UUID to the original array. Will this create any problems booting? Do I need to simply update /etc/mdadm/mdadm.conf with the new UUID (via mdadm --detail --scan) or should I manually modify the UUID of the new array (via mdadm --assemble --update uuid=...). Note that I'm not very confident with updating the UUID whilst assembling the array as I think that when the array is assembled that is when the problem with failing to understand the proper array size will reoccur.
Should be fine. Un-mount and --stop the array. After the re-create do an --examine --scan to find the new UUID and substitute it in mdadm.conf. Then run 'update-initramfs -u' to make the boot process aware of the changes.

BTW I think the old method to add the ARRAY statement to mdadm.conf, mdadm --examine --scan >> mdadm.conf, doesn't work reliably with 1.x anymore. For example, the array can have a textual name now and if it has any spaces in it the ARRAY directive breaks!:? I think all that is needed is: [COLOR="DarkGreen"]ARRAY /dev/mdn UUID=a:b:c:d[/COLOR]

---

### Post by rubylaser on 2011-06-07
YesWeCan, this looks to be good support that you've provided here.  The 2TB limit for metadata version 00.90 is spelled out on the wiki.
[https://raid.wiki.kernel.org/index.php/RAID_superblock_formats#The_version-0.90_Superblock_Format]("https://raid.wiki.kernel.org/index.php/RAID_superblock_formats#The_version-0.90_Superblock_Format")
(not that it helps at this point :) )

I can understand why 00.90 is the default in older versions of mdadm (so it can support a bootable array), but it would be nice to get a grow error message if your partitions are greater than 2TB each when growing an array using the old metadata format.

Also, in newer versions of mdadm (3.1.4) the default is to set the metadata version to 1.2.  Finally, I couldn't agree more that the wiki needs to be updated, especially to include more scenarios like this rather than just man pages.

---

### Post by YesWeCan on 2011-06-07
> **rubylaser said:**
> YesWeCan, this looks to be good support that you've provided here.
Thank you, much appreciated. I'm glad you are here, you have a lot more experience of mdadm than I. It is an interesting predicament that jgoris has accidentally encountered.

> I can understand why 00.90 is the default in older versions of mdadm (so it can support a bootable array), but it would be nice to get a grow error message if your partitions are greater than 2TB each when growing an array using the old metadata format.
I am curious about this. Is it Grub or the kernel or both that has/had a problem booting off a 1.x metadata array? I believe that Grub 1.99 is compatible with v1.2 but 1.98 may not be.

I think "grow" should definitely report an error. This appears to me to be a serious design oversight. It needs reporting as a bug.

> Finally, I couldn't agree more that the wiki needs to be updated, especially to include more scenarios like this rather than just man pages.
Yep. Documentation aside, I appreciate the usefulness, versatility and reliability that I have experienced with mdadm.

---

### Post by YesWeCan on 2011-06-07
> **jgoris said:**
> Regarding recreating the array using the --assume-clean, I think you are right and this is the best way to go about it. However, is there really a need to zero the superblock of the existing array first. I assume that creating the new array will overwrite it anyway, but if the create command fails, I don't want to lose my OS.
One thing that just occurred to me is that because you have written more than 9.4TB to the array now, that when --create tries to generate the metadata it may just write the wrong value of sector size again. That is to say, it cannot recreate the 0.90 metadata correctly because the array is too big now. In my earlier post I assumed you had not increased the amount of data.

So the create might just set a weird value for the size again. If you are lucky, the create will make the same oversight as the grow did. So the metadata value will be wrong but the system will think it has a 14TB array and you'll be able to mount you LVs. If not, you are in trouble.

Alternatively, it would be nice to use the grow command to again increase the array to an illegally large size, but without affecting the existing data. Unfortunately, the man page implies that the grow will reformat the added array space and therefore trash some of your data.

Contact Neil Brown: [http://neil.brown.name/blog/](http://neil.brown.name/blog/)

---

### Post by rubylaser on 2011-06-08
> **YesWeCan said:**
> I am curious about this. Is it Grub or the kernel or both that has/had a problem booting off a 1.x metadata array? I believe that Grub 1.99 is compatible with v1.2 but 1.98 may not be.

The problem is Grub, and you're correct that Grub 1.99 now supports metadata versions 1.x
[http://lists.gnu.org/archive/html/grub-devel/2011-05/msg00032.html]("http://lists.gnu.org/archive/html/grub-devel/2011-05/msg00032.html")

Grub 1.99 is the default in 11.04, but I'm still running the LTS 10.04 release on my server at home, so booting from an SSD will have to do for me :)

---

### Post by YesWeCan on 2011-06-09
@jgoris
I have created a bug report for this on your behalf: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/794963](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/794963)
Would you mind adding a comment to this with a little more detail about exactly what you did for the benefit of the repairers? Thx.

---

### Post by jgoris on 2011-06-09
Thanks for your continued help on this problem. I've been busy  building a system with enough storage to take most of the old data so that I can  attempt the recovery this weekend. The array is so large that I'll actually need to split it over 3 different machines. The data is not irreplacable, it  will just take a long time to replace so it's much much quicker to  attempt to recover the data. I've decided to try to recover the data to a  temporary machine then rebuild the old machine with 11.04 creating a fresh RAID array with metadata 1.20. I think a fresh build is the safest and quickest strategy after getting the array up just long enough to recover all the data from it. I'm not going to entertain the idea of shrinking the array at all.

I'm convinced that almost all, if not all, of the data is currently intact and I just need to  work out how to make it available again. Since the machine was shut down I see no reason why any data would have been modified other than in the radagast-root and radagast-swap LVs. Also, I don't think that when the  data was written past the 2T mark on each component device that it  wrapped around to the beginning or else it would have overwritten  the OS which is at the start of the array. (I'm assuming that LVM puts  the first logical volume created at the beginning of the first and only  phyical volume). If it has "wrapped" and overwritten some data somewhere randomly and I  get 90% back I'll still be happy. How good e2fsck will be if this is the actual scenario I do not know.

> **YesWeCan said:**
> One thing that just occurred to me is that because you have written more than 9.4TB to the array now, that when --create tries to generate the metadata it may just write the wrong value of sector size again. That is to say, it cannot recreate the 0.90 metadata correctly because the array is too big now. In my earlier post I assumed you had not increased the amount of data.

So the create might just set a weird value for the size again. If you are lucky, the create will make the same oversight as the grow did. So the metadata value will be wrong but the system will think it has a 14TB array and you'll be able to mount you LVs. If not, you are in trouble.

Alternatively, it would be nice to use the grow command to again increase the array to an illegally large size, but without affecting the existing data. Unfortunately, the man page implies that the grow will reformat the added array space and therefore trash some of your data.

I'm leaning towards trying to recover the array with [COLOR=DarkGreen]mdadm --grow --assume-clean[/COLOR]. My understanding is that the --assume-clean option will cause mdadm not to do any kind of sync or resync on the array and the option may be used on both create and grow operations. Thus in theory it should not touch the data at all on the array and the grow should work. If the grow mistakingly worked before it is likely to work again. I can even do it from the partially booted OS, rather than the recovery disc. My original grow command with the --assume-clean added would be as follows:

```
sudo mdadm --grow --size=max --assume-clean /dev/md1
```

What do you reckon about this option?

> @jgoris
I have created a bug report for this on your behalf: [https://bugs.launchpad.net/ubuntu/+s...dm/+bug/794963]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/794963")
Would you mind adding a comment to this with a little more detail about  exactly what you did for the benefit of the repairers? Thx.

No problem. I'll get on to it after this post.

> It shows up a weakness in the collage that is linux: a change to mdadm metadata should have triggered a change to Grub2.
I would also like to see an mdadm command to update the metadata format from 0.90 to 1.x. But most of all I would like to see a professional user guide for mdadm.  I find myself bleating about this so often that I am beginning to  wonder whether it is incumbent upon me to write one. I really think the  designer(s) should take responsibility.

My biggest gripe about Linux is documentation. So much great open source software out there, but with relatively patchy and poor documentation.

Thanks again for all your help.

---

### Post by jgoris on 2011-06-10
I just tried to grow the array with the --assume-clean flag and here's what happened

```
$ sudo mdadm --grow --size=max --assume-clean /dev/md1
mdadm:option --assume-clean not valid in grow mode
```

The manpage indicates that the --assume-clean option is useable for create, build or grow. I'll now try booting from the rescue disk and recreating the array with the --assume-clean flag. Fingers crossed.

---

### Post by YesWeCan on 2011-06-10
That's too bad. Well at least it failed to do it this time ;)
Good luck.

---

### Post by jgoris on 2011-07-15
Sorry for the big delay in responding on how this went. Basically, it went terribly and I lost all data, including those partitions that were originally unaffected by the original problem.

Recreating the array with the --assume-clean option worked. I actually specified the chunk size and algorithm as per the original array and it worked fine. I used an array size of 2TB-512 per raid device. The logical volumes all reappeared fine and were actove, except for one which required the full array with 3TB raid device, which is as I expected. However, I could not mount any of the file systems. I received errors indicating that either the file system was in use or that it did not appear to be an ext4 file system.

This really surprised me that I lost everything and could not even access the file systems that were wholly within the array created with the original 2TB raid devices. If I was to attempt this again, and I really hope I never have to, I would simply try to regrow the array with the mdadm --grow command. As I udnerstand it, when the grow operation syncs the new space on each drive, it simply picks one drive and writes data on it to make sure that it is in sync with the other drives. If all the data was valid to begin with then it should be valid after the  sync for the grow operation completes. I plan never to have to test this though.

Despite the failure, thanks for all your help YesWeCan.

---

