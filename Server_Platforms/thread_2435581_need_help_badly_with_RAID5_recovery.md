---
title: "need help badly with RAID5 recovery"
date: 2020-01-22
forum: Server Platforms
---

### Post by bohnnyjliss on 2020-01-22
i'm a programmer and not a IT guy.

i was asked to help a company my software company is partnered with (small business, no IT dept)

they had a guy configure a linux mdadm raid5 with 4 drives. one drive failed at some point (it still does click of death). at some point someone there removed the 5th drive that was getting backups put on it. their last backup is from almost 3 years ago :mad:

they had it booting off a USB which became corrupted somehow and it would no longer boot, they had a non IT guy there try to install linux, i dont know exactly what happened but the third drive won't assemble into the raid array anymore. it keeps saying it can't find a superblock, it has a linux (bootable) ext4 partition, which is different than the two good drives.

at the point this got put in my lap the two good drives have had the partitions written over, i'm using testdisk to recover the old deleted partitions but it is taking a long time to scan i'm waiting for it now...

the "good" drive that has the linux "bootable"  partition on it, i've backed up with DD. i'm going to back up the other two drives with DD but it took 40 hours to do the first one :popcorn:

if i try to assemble the raid array with "assume clean" does it need the partitions sorted out? can mdadm figure it out?

i'm learning as i go on some of this .

i think they are probably f'd and might have to send it to some company to try and recover stuff forensically 

[ATTACH=CONFIG]284877[/ATTACH]

[ATTACH=CONFIG]284878[/ATTACH]

at this point i think my only option is to use --create --assume-clean to try and get the raid array back.

---

### Post by darkod on 2020-01-22
Wow... Good luck, sounds like a really really messed up situation.

First of all, keep calm if you want to have any shot at this. Even then it might be impossible (not fault of yours).

So, not counting the dead disk, you have three of them left and probably one of them was overwritten installing the OS on it. I got that right?

Post the mdadm -E for each disk. Best if it's text output in CODE tags.

HINT: When using Ubuntu Desktop live mode to troubleshoot/rescue, if you want to you can add openssh-server inside the live session if the machine has internet. Doing that will allow you to ssh into it from another computer and like that you can easily copy/paste your terminal output into the forum. Instead of relying on pictures.

In live mode usually this setup wouldn't survive reboots, so you would need to install the openssh-server each time you reboot... Just an idea, you don't have to do it if you're not OK with it. But text output helps people have better idea and get full output while picture sometimes might be cutting things out etc.

---

### Post by bohnnyjliss on 2020-01-22
i ended up installing ubuntu on an old SSD drive i had.

im trying to get the partitions back on the two of the drives that were good in the raid.

right now the partitions are messed up, the screenshot for the -E on sdc is what two of them looked like. the third would show a normal ext4 partition like this:

now both the working drives only show this instead of the information that was in the first sdc screenshot. i'm trying to get it back to that state from the first -E screenshot. i'm hoping testdisk will let me bring back the old partition information. its taking a long time to scan its at 89% now

[ATTACH=CONFIG]284879[/ATTACH]

the fact that the testdisk partition scan is taking so long on sdc is makign me worried, before it would only take a couple mins and it would stop at about 57% and find the old partitions.

---

### Post by bunny9000 on 2020-01-22
Your screen says it's raid 0 so it's 2x disks acting as 1 now? and raid 5 can only recover from 1 disk failure which should have been switched when it failed.

Is this server using a dedicated raid controller or software raid.

---

### Post by bohnnyjliss on 2020-01-22
it was using software raid "mdadm"

i believe the underlying data and structure is on three of the drives its just a matter of getting it back configured properly

---

### Post by darkod on 2020-01-22
Don't worry about that raid0 message. Often you can receive inconsistent results during rescue work.

But it worrying that you can't get the same mdadm -E output now. If that disk was good, with detected raid partition, I assume you didn't try to change anything on it. So it should still be as it is.

Losing the first, dead, disk was not a problem. Even when a second disk goes out of sync it still not very big problem. The array would disassemble but you would have two good members and one just slightly out of sync (and one dead). With that you can force mdadm to re-assemble.

But if you had only two good members, one dead, and one that was overwritten, then that could be serious because you can't restore raid5 with two missing members. You had at least one disk overwritten, right? That is why you are using testdisk to try restore the old partitions on it?

---

### Post by bohnnyjliss on 2020-01-22
afaik just the partitions were changed. not the data.

i'm trying to use testdisk to bring back the partition(s) so that it shows the raid and not the regular linux ext4 partition.

the first screenshot of sdc is what im trying to get back at this point and move on from there.

this is what it shows for sdc now:

[ATTACH=CONFIG]284880[/ATTACH]

this is what i want:
[ATTACH=CONFIG]284881[/ATTACH]

---

### Post by darkod on 2020-01-22
First of all, do not forget that drive letters can change. When using usb sticks and/or new OS disk (you mentioned) then the disks might not get detected in the same order always.

Could we get the output of:
```
lsblk
sudo blkid
```

---

### Post by bohnnyjliss on 2020-01-22
does mdadm need to have the drives formatted correctly? if i try to create the array with assume clean and the old parameters does it care about how the drives are partitioned?

```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0  1008K  1 loop /snap/gnome-logs/61
loop1    7:1    0 149.9M  1 loop /snap/gnome-3-28-1804/67
loop2    7:2    0  54.4M  1 loop /snap/core18/1066
loop3    7:3    0  44.9M  1 loop /snap/gtk-common-themes/1440
loop4    7:4    0   956K  1 loop /snap/gnome-logs/81
loop5    7:5    0   3.7M  1 loop /snap/gnome-system-monitor/100
loop6    7:6    0  14.8M  1 loop /snap/gnome-characters/296
loop7    7:7    0   3.7M  1 loop /snap/gnome-system-monitor/123
loop8    7:8    0 156.7M  1 loop /snap/gnome-3-28-1804/110
loop9    7:9    0  42.8M  1 loop /snap/gtk-common-themes/1313
loop10   7:10   0     4M  1 loop /snap/gnome-calculator/406
loop11   7:11   0  88.5M  1 loop /snap/core/7270
loop12   7:12   0  14.8M  1 loop /snap/gnome-characters/375
loop13   7:13   0  89.1M  1 loop /snap/core/8268
loop14   7:14   0  54.7M  1 loop /snap/core18/1650
loop15   7:15   0   4.2M  1 loop /snap/gnome-calculator/544
loop16   7:16   0  15.8M  1 loop /snap/kolourpaint/44
loop17   7:17   0 260.7M  1 loop /snap/kde-frameworks-5-core18/32
sdb      8:16   0  55.9G  0 disk 
&#9492;&#9472;sdb1   8:17   0  55.9G  0 part /
sdc      8:32   0   3.7T  0 disk 
sdd      8:48   0   3.7T  0 disk 
&#9492;&#9472;sdd1   8:49   0     2T  0 part 
sde      8:64   0   3.7T  0 disk 
&#9492;&#9472;sde1   8:65   0     2T  0 part 
sdf      8:80   0   3.7T  0 disk 
&#9492;&#9472;sdf1   8:81   0     2T  0 part 
sdg      8:96   0   3.7T  0 disk 
sdh      8:112  0   3.7T  0 disk 
&#9492;&#9472;sdh1   8:113  0     2T  0 part 


```

```
/dev/sdb1: UUID="40ccaf56-2e46-4ba1-9eaa-042d8cd2ed54" TYPE="ext4" PARTUUID="c3e9cd3e-01"
/dev/sde1: UUID="6b50d3e4-e44e-4432-8c7c-7091a5569b80" TYPE="ext4" PARTUUID="1503067f-01"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sdc: PTUUID="42d38be4-ed7a-47d3-88cf-a5e8e6f60d2d" PTTYPE="gpt"
/dev/sdd1: UUID="396bdf0d-c756-4665-918f-691c38ce7a02" TYPE="ext4" PARTLABEL="Linux filesystem" PARTUUID="ef5721a2-5503-45ad-ac64-b0911eeca98b"
/dev/sdf1: UUID="6b50d3e4-e44e-4432-8c7c-7091a5569b80" TYPE="ext4" PARTLABEL="Linux filesystem" PARTUUID="cb8c8b8c-2c94-48dd-b987-374ab4e91b82"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/sdg: PTUUID="42d38be4-ed7a-47d3-88cf-a5e8e6f60d2d" PTTYPE="gpt"
/dev/sdh1: UUID="396bdf0d-c756-4665-918f-691c38ce7a02" TYPE="ext4" PARTLABEL="Linux filesystem" PARTUUID="ef5721a2-5503-45ad-ac64-b0911eeca98b"
/dev/loop17: TYPE="squashfs"

```

---

### Post by darkod on 2020-01-22
It depends. You can use the whole disk (no partitions) as mdadm member or a partition. Of course there is difference, even if the disk has only one partition using the whole space, it would be called for example /dev/sda1. When using the whole disk without partitions, it would be /dev/sda.

It makes a big difference which you put into the command, it has to match where the data is.

Please reply to my previous post, you go little too fast. We need an idea of the partitions layout first.

---

### Post by bohnnyjliss on 2020-01-22
they were using the entire disk if i remember correctly when the raid would assemble but only in an inactive state because of missing two members

```
ARRAY /dev/md0 level=raid5 num-devices=4 metadata=1.2 UUID=42d83b65:99781590:ddb09579:6bccfe76 name=ABMScaleServer:0

```

```
administrator@abmlinuxserver:~$ sudo mdadm --assemble --scan --verbose
mdadm: looking for devices for /dev/md0
mdadm: No super block found on /dev/loop17 (Expected magic a92b4efc, got 1bd7e597)
mdadm: no RAID superblock on /dev/loop17
mdadm: No super block found on /dev/sdh1 (Expected magic a92b4efc, got 00000401)
mdadm: no RAID superblock on /dev/sdh1
mdadm: No super block found on /dev/sdh (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdh
mdadm: No super block found on /dev/sdg (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdg
mdadm: No super block found on /dev/loop16 (Expected magic a92b4efc, got e04923f8)
mdadm: no RAID superblock on /dev/loop16
mdadm: No super block found on /dev/loop15 (Expected magic a92b4efc, got 63c186fe)
mdadm: no RAID superblock on /dev/loop15
mdadm: No super block found on /dev/loop14 (Expected magic a92b4efc, got e7e108a6)
mdadm: no RAID superblock on /dev/loop14
mdadm: No super block found on /dev/loop13 (Expected magic a92b4efc, got 14ea0a05)
mdadm: no RAID superblock on /dev/loop13
mdadm: No super block found on /dev/loop12 (Expected magic a92b4efc, got a2d4bb38)
mdadm: no RAID superblock on /dev/loop12
mdadm: No super block found on /dev/loop11 (Expected magic a92b4efc, got cd57a835)
mdadm: no RAID superblock on /dev/loop11
mdadm: No super block found on /dev/loop10 (Expected magic a92b4efc, got e5545a99)
mdadm: no RAID superblock on /dev/loop10
mdadm: No super block found on /dev/loop9 (Expected magic a92b4efc, got 4e454900)
mdadm: no RAID superblock on /dev/loop9
mdadm: No super block found on /dev/loop8 (Expected magic a92b4efc, got 1bd7e597)
mdadm: no RAID superblock on /dev/loop8
mdadm: No super block found on /dev/sdf1 (Expected magic a92b4efc, got 00000401)
mdadm: no RAID superblock on /dev/sdf1
mdadm: No super block found on /dev/sdf (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdf
mdadm: No super block found on /dev/sde1 (Expected magic a92b4efc, got 00000401)
mdadm: no RAID superblock on /dev/sde1
mdadm: No super block found on /dev/sde (Expected magic a92b4efc, got a0ddb71c)
mdadm: no RAID superblock on /dev/sde
mdadm: No super block found on /dev/sdd1 (Expected magic a92b4efc, got 00000401)
mdadm: no RAID superblock on /dev/sdd1
mdadm: No super block found on /dev/sdd (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdd
mdadm: No super block found on /dev/sdc (Expected magic a92b4efc, got 00000000)
mdadm: no RAID superblock on /dev/sdc
mdadm: No super block found on /dev/sdb1 (Expected magic a92b4efc, got 00000408)
mdadm: no RAID superblock on /dev/sdb1
mdadm: No super block found on /dev/sdb (Expected magic a92b4efc, got a0ddb71c)
mdadm: no RAID superblock on /dev/sdb
mdadm: No super block found on /dev/loop7 (Expected magic a92b4efc, got a2d4bb38)
mdadm: no RAID superblock on /dev/loop7
mdadm: No super block found on /dev/loop6 (Expected magic a92b4efc, got e5545a99)
mdadm: no RAID superblock on /dev/loop6
mdadm: No super block found on /dev/loop5 (Expected magic a92b4efc, got e5545a99)
mdadm: no RAID superblock on /dev/loop5
mdadm: No super block found on /dev/loop4 (Expected magic a92b4efc, got 27e7af3a)
mdadm: no RAID superblock on /dev/loop4
mdadm: No super block found on /dev/loop3 (Expected magic a92b4efc, got 78bc5e9c)
mdadm: no RAID superblock on /dev/loop3
mdadm: No super block found on /dev/loop2 (Expected magic a92b4efc, got e7e108a6)
mdadm: no RAID superblock on /dev/loop2
mdadm: No super block found on /dev/loop1 (Expected magic a92b4efc, got 1bd7e597)
mdadm: no RAID superblock on /dev/loop1
mdadm: No super block found on /dev/loop0 (Expected magic a92b4efc, got e5545a99)
mdadm: no RAID superblock on /dev/loop0
```

---

### Post by darkod on 2020-01-22
Well, you see the benefit of blkid output. According to that they were actually using partitions. sdd1 and sdf1 seem like members of the same array, the UUID matches. sdf1 also has some mdadm superblock but the UUID does not match with the other two.

sdc right now has no partitions.

Post the following now:
```
sudo mdadm -E /dev/sd[df]1
sudo mdadm -E /dev/sdf1
```

That will show us those superblocks.

PS. Hold on... I just noticed blkid sayd they have ext4 filesystem, and it says Linux filesystem. It shouldn't say that for mdadm.

And why are there so many disks? Are you cloning? That is why I see identical UUIDs?

If you are cloning first complete that process, power off, remove the clones, and then lets see the situation with only the original disks. We can't work with clones present too, it confuses everything.

---

### Post by bohnnyjliss on 2020-01-22
```
administrator@abmlinuxserver:~$ sudo mdadm -E /dev/sd[df]1
mdadm: No md superblock detected on /dev/sdd1.
mdadm: No md superblock detected on /dev/sdf1.

```

```
administrator@abmlinuxserver:~$ sudo mdadm -E /dev/sdf1
mdadm: No md superblock detected on /dev/sdf1.


```

---

### Post by darkod on 2020-01-22
Read the PS of my last post.

And how come blkid shows no mdadm partitions at all. What happened to the two good drives, how did they loose the mdadm superblock???

---

### Post by bohnnyjliss on 2020-01-22
ok i will do that in a few minutes.

yes i was using DD to copy the disks but they are huge and it takes about 40 hours

i think the partitions got copied from a different drive like using sgdisk -R

this overwrote the mdadm, i was hoping to try and bring it back using testdisk?

---

### Post by darkod on 2020-01-22
Well unfortunately that puts you from very bad to a much worse position.

You need to be very careful when copying over partition tables, and especially make sure you don't overwrite the good disks.

Until you get the partitions back I'm afraid we don't have anything to work with... :(

---

### Post by bohnnyjliss on 2020-01-22
what i believe happened in sgdisk -R got used and it copied the partition info from a non member drive to the member drive(S)

---

### Post by darkod on 2020-01-23
Did you manage to make some progress restoring the partition tables back?

---

### Post by bohnnyjliss on 2020-01-24
> **darkod said:**
> Did you manage to make some progress restoring the partition tables back?

hey,

i havent' yet. i switched to windows and have been trying some raid recovery software.

"reclaim me" raid recovery hangs after a minute or so of trying

"r-studio" seems to work better, but i dont think i have the raid parameters correct and it takes a very long time to scan but i think this software could work if i can get the parameters right. it supposedly has a "detect parameters" function but it doesn't seem to work and its a little confusing.

maybe you could help:

this is what the RAID5 should've originally looked like except i dont know the order. it should be able to detect that. i do know that the block size is 4096

in linux is says the layout is "left-symmetric" im guessing that is the same as left synchronous since the diagram matches.

what i dont know and can't seem to figure out is:

parity delay
first parity

i'm fairly certain that this raid5 is constructed with the default mdadm parameters


[ATTACH=CONFIG]284882[/ATTACH]

it would be nice to get the parameters right because it takes like 40 hours to scan. i am trying what you see in the screenshot now and it seems better than last time i scanned trying to use only the 3 drives and not specifying a fourth which i think was a mistake. hard to tell though

the scan has only been going for a few minutes but its found this so far the ext4 part looks right...?
[ATTACH=CONFIG]284883[/ATTACH]

---

### Post by slickymaster on 2020-01-24
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by bohnnyjliss on 2020-01-24
23kb is a "large image"???? ok

this seems right, i guess i just need to let it scan. 

[ATTACH=CONFIG]284884[/ATTACH]

---

### Post by darkod on 2020-01-24
Honestly I have never tried restoring like this, if you try to use software that tries to detect the whole array. Those 10TB are the whole array.

What I can give an advice about is the assemble of the array once you have the disks with the correct "old" partition tables. I thought you were gonna use testdisk to just get the layout back. In fact, if you knew the layout (numbers) you could even use sgdisk to "push" that as new partition table. But because you need to get it right it would be best if testdisk scan can point you the values when detecting what the old partitions start/end was. You said whole unpartitioned disks were used, so the layout might be very simple indeed.

But if you want to give this software a shot and try to restore the array as a whole (or the data from it, not sure what the software offers) you are free to try. :)

---

### Post by bohnnyjliss on 2020-01-24
Testdisk said it couldn't restore the old partitions

If this doesn't work I might have to go back to trying that

---

### Post by darkod on 2020-01-24
Even if it couldn't restore, did it at least show you some useful info? Like for example the old start/end of partitions?

And again I say, if whole disk was used maybe there were no partitions at all. Hence testdisk not being able to do a restore.

Anyway, if at least you have some info to work with, you can try a little risky process to produce a text file yourself that could act like "old backup" and tell sgdisk to use it to restore.

Because what sgdisk does when you use it to backup a partition table is basically dump info into a text file.

---

### Post by bohnnyjliss on 2020-01-24
It did tell me the start and end I don't know enough I guess on what to do. I'll post some more info Monday or something

---

### Post by darkod on 2020-01-25
OK. I might have spoken too fast about sgdisk. It seems the backup file it creates is binary coded, not simple text. So even if you know partition data you can't reproduce a file to simulate a backup file.

But there are other ways to try. When you create simple partition with parted or gdisk (without trying to create a filesystem at the same time!!!) I think it will only set the partition start and end without disturbing the actual data.

Once you post what you have we can see if something can be done about it.

You did clone the disks right? Do you have clones for trying out things without disturbing the original disks?

---

### Post by bohnnyjliss on 2020-01-26
i only cloned one of them at this point it takes 40 hours :/

filesystems did not get created on two of them, but the third it might have.

i should really try the freezer trick on the 4th drive that clicks

i tried it once but only left it in for a couple hours

---

### Post by darkod on 2020-01-26
Since it looks fairly certain that whole disks were used in the array, you could try the following. Your choice whether you want to try with the current (only) disks that you have or clones. Using clones gives you the possibility to keep the original disks as they are. But cloning takes time...

Another problem you have is that you only have two good disks out of four (I say good even if we ignore that the partition table was overwritten). So the best case for you is only two disks. You won't be able to re-assemble the array with that.

The disk where the OS was installed means it not only had the partiton table overwritten, but also new partitions created, formatted, AND files were written on them. Effectively overwriting part of the data that you want to have back.

Now depending how much was written into the disk, it would be only "small" portion of 4TB. Because the ubuntu OS is small.

So you could try the following:
1. Use parted to delete the partitions on all three disks (they had no partitions as raid members originally). DO NOT delete the partition table, just the partitions!!!
2. Try to use mdadm --create with --assume-clean to make a new raid5 with three members and one missing.

Obviously, even if the above works you will end up with part of the data corrupted (that was overwritten on one of the disks). But that's still better than losing all of the data.

Trying this is best on cloned disks, I go back to saying that...

If you wish to do that, let us know first and wait to double check the best command to use. You really didn't give us much to work with. Because mdadm might be sensitive to the disk order you use in the --create. And parameters like the chunk size, which according to your first post seems to have been 16M, not the usual 64K.

And I still don't understand something about your first two posts. If I understood correctly, all the damage (raid failure, OS reinstall over raid disk, wrong sgdisk -R usage) happened BEFORE this mess was handed over to you. Then how come you managed to pull what seems to be correct superblock info with mdadm -E /dev/sdc in your first post, and then immediately the second post had different output. But this is secondary now... What would have been good is to have few more superblock outputs so that we can figure out the disk order...

But if I understood correctly you can't provide any more correct superblock output for any disk.

---

### Post by bohnnyjliss on 2020-01-27
to clarify i was the one that accidentally sgdisk over the partitions, but i never created a filesystem or anything past that.

i got the mdadm -e info before i accidentally did that :(

i read the man wrong and had the partition copy backwards, i was going to try and copy the partition info from the "good" disk to the one that the previous person had tried to install linux (i believe not 100% sure, but thats what it seems like)

i'm DD'ing the two drives and i will try the assume clean when they are finished. i hooked them to faster connections and hopefully it will only take about a day to transfer both, they are going at the same time at about 60-70mb/sec

i'm also running a deep swearch using testdisk on one of the "good" drives and i will report back what partitions it finds.

---

### Post by darkod on 2020-01-27
If I'm not mistaken you already have one clone, you said earlier one has completed, right? Is that from sdc?

If you want to, you can try deleting the partitions on the clone, and we can see if that returns the mdadm superblock readable by any chance.

I don't think testdisk scans are useful on the disks. Because whole disks were used in mdadm there is no "partition layout" to detect...

I can understand the accident with sgdisk on one good disk, but what about the second one? You overwrote the partition table on both good disks?

I would try the --create --assume-clean as soon as you have the clones. At this time I see testdisk as something that is just taking you long time and not much usefulness.

---

### Post by bohnnyjliss on 2020-01-27
ok that info helps about testdisk, if the raid used the entire disk and had no partitions thats why i'm never seeing any partition info.

the DD's are at 50% another 10 hours and i can try to assemble the raid with assume clean.

unfortunately the clicking disk didn't fix itself with the freezer trick

[ATTACH=CONFIG]284911[/ATTACH][ATTACH=CONFIG]284912[/ATTACH]

[ATTACH=CONFIG]284913[/ATTACH]

---

### Post by darkod on 2020-01-27
Hmmm, honestly I don't think this helps you a lot. Not for the raid array recovery.

I would stick with the plan to complete the cloning at which point you will have three disks to work with (plus the original ones). We are not counting the clicking one...

With those three disks you can hope to re-create the array and accepting certain percent of data loss...

---

### Post by bohnnyjliss on 2020-01-27
sounds like a plan.

the transfer is going faster than i expected. they're at 1.78tb/2.2tb

i should be able to try something later today

---

### Post by darkod on 2020-01-27
Well, mdadm is very smart detecting existing data, but in your case you might have only two good disks out of four, so we can't be really sure how it will react. I have seen the following command with minimum parameters (it detects the rest). Again, it might not work in your case.

First, very important: Power off the server and take the original disks out (or the clones, depending what you want to work with). Never do this with the duplicate disks attached.

Second, I don't know which letters will the three disks have so lets say they will be sdb, sdc and sdd in my examples. You will need to modify the commands according to the drive letters.

Try the following to re-create first:
```
sudo mdadm --create --verbose --assume-clean /dev/md0 /dev/sdb /dev/sdc /dev/sdd
```

In case that works, you can try mounting the array and check the content. At this moment, NEVER mount it RW. Don't risk writing anything on it, on purpose or accidentally. Mount as RO to only check basic folder structure. You can create any temp folder to serve as mount point.
```
sudo mkdir /mnt/tempdir
sudo mount -o ro /dev/md0 /mnt/tempdir
```

Go inside and check around. I assume you have basic linux terminal browsing skills...
```
cd /mnt/tempdir
ls
```

After you're done with your tests don't forget to unmount it.

If the md0 from above didn't work, you will probably get an error when trying to mount. In that case stop md0 so that you can try different --create command. It might not even assemble into md0 so you might not need to stop it.
```
sudo mdadm --stop /dev/md0
```

Slightly different --create with 16M chunk:
```
sudo mdadm --create --verbose --assume-clean --chunk=16M --level=raid5 --raid-devices=4 /dev/md0 /dev/sdb /dev/sdc /dev/sdd missing
```

If that assembles try to mount it RO as above.

If the --verbose output gives you more useful info, like sdc is in slot 0 instead of slot 1, then shuffle the devices in the --create as necessary. I'm not 100% if it is smart enough to figure out device slot on its own or it depends on the order you put in your command. Because for the filesystem to be possible to read the order has to be correct.

You will have to see how it goes...

---

### Post by bohnnyjliss on 2020-01-27
thx for the info

its not quite done yet but should be any minute

---

### Post by bohnnyjliss on 2020-01-27
its still going, i guess it'll be a while yet ill try tomorrow

---

### Post by bohnnyjliss on 2020-01-28
i keep getting message "no-raid device specified"

```
mdadm --create --assume-clean /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 --verbose
```

---

### Post by bohnnyjliss on 2020-01-28
if i try different syntax it thinks "/dev/md0" is supposed to be part of the raid

```
mdadm --create --assume-clean --level=5 --raid-devices=4 --verbose /dev/md0 /dev/sda /dev/sdb /dev/sdc /dev/sdf missing
mdadm: You have listed more devices (5) than are in the array(4)!

```

---

### Post by bohnnyjliss on 2020-01-28
if i remove missing it gives an error saying /dev/sdf doesnt exist which is true, but if i add missing after /dev/sdf it says i'm trying to add 5 devices and it should be 4

---

### Post by bohnnyjliss on 2020-01-28
maybe i should just put another good drive in and use it blank? and if the array works it will recreate on it?

---

### Post by bohnnyjliss on 2020-01-28
i got the array to create but it wont mount

```
mount -o ro /dev/md0 /mnt/tempdir
mount: /mnt/tempdir: wrong fs type, bad option, bad superblock on /dev/md0, missing codepage or helper program, or other error.

```

---

### Post by bohnnyjliss on 2020-01-28
```
mdadm --detail /dev/md0
/dev/md0:
           Version : 1.2
     Creation Time : Tue Jan 28 08:56:48 2020
        Raid Level : raid5
        Array Size : 11720638464 (11177.67 GiB 12001.93 GB)
     Used Dev Size : 3906879488 (3725.89 GiB 4000.64 GB)
      Raid Devices : 4
     Total Devices : 4
       Persistence : Superblock is persistent

     Intent Bitmap : Internal

       Update Time : Tue Jan 28 08:56:48 2020
             State : clean 
    Active Devices : 4
   Working Devices : 4
    Failed Devices : 0
     Spare Devices : 0

            Layout : left-symmetric
        Chunk Size : 16384K

Consistency Policy : bitmap

              Name : abmlinuxserver:0  (local to host abmlinuxserver)
              UUID : 51b78884:68f35f06:b39d8aa1:aa9fb193
            Events : 0

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       64        3      active sync   /dev/sde


```

---

### Post by bohnnyjliss on 2020-01-28
```
fsck -n /dev/md0
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

```

---

### Post by darkod on 2020-01-28
I gave you an exact syntax for a reason. :)

First of all, with --raid-devices=4 you say there are 4 raid members. And they always have to be at the end, so don't put --verbose at the end.

The 'missing' is not a coincidence. It "replaces" one member. So you put sda, sdb, sdc, sdf and missing, which is in fact 5. That's why it complaint to you.

And why are you trying with 4 disks? No point, putting a brand new empty disk there won't help you. And I understood the clicking disk was dead long ago, so it brings no benefit.

The idea is to try assemble the 4 disk raid5 with the three disks and one missing member.

At the end, you said md0 assembled but it would have been better to post the --create output. That's why I put --verbose, to have more details both for you and for us. Knowing what mdadm said during --create could give us some info.

It doesn't mount because it can't find correct FS. That could be because the data is not restorable, or simply because the disk order is wrong.

That is why --assume-clean is important, and not to write to the array. You can try again with different disk order and it doesn't mess up anything.

Lets go few steps back. Please post the output of:
```
sudo blkid
```

I want to see that before trying to assemble again.

---

### Post by bohnnyjliss on 2020-01-28
```
root@abmlinuxserver:~# mke2fs -n -b 4096 /dev/md0
mke2fs 1.44.1 (24-Mar-2018)
Creating filesystem with 2930159616 4k blocks and 366272512 inodes
Filesystem UUID: 1372497b-e696-4c6c-86cd-522f6ebaf5f1
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000, 214990848, 512000000, 550731776, 644972544, 1934917632, 
    2560000000

root@abmlinuxserver:~# e2fsck -n -b 11239424 /dev/md0
e2fsck 1.44.1 (24-Mar-2018)
e2fsck: Bad magic number in super-block while trying to open /dev/md0

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

root@abmlinuxserver:~# 
```

---

### Post by bohnnyjliss on 2020-01-28
```
blkid
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="013b06c2-f75c-a678-6706-9b1c4c751f2f" UUID_SUB="d9d9687c-b071-cd44-8cbb-9014d329dd11" LABEL="abmlinuxserver:0" TYPE="linux_raid_member" PARTUUID="1503067f-01"
/dev/sdb: UUID="51b78884-68f3-5f06-b39d-8aa1aa9fb193" UUID_SUB="946ff12b-e3bb-4ecf-f7db-041328f09609" LABEL="abmlinuxserver:0" TYPE="linux_raid_member"
/dev/sdc: UUID="51b78884-68f3-5f06-b39d-8aa1aa9fb193" UUID_SUB="34cb639f-1215-5683-5e9d-1bbf92c3adb4" LABEL="abmlinuxserver:0" TYPE="linux_raid_member"
/dev/sdd1: UUID="40ccaf56-2e46-4ba1-9eaa-042d8cd2ed54" TYPE="ext4" PARTUUID="c3e9cd3e-01"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/sde: UUID="51b78884-68f3-5f06-b39d-8aa1aa9fb193" UUID_SUB="24f15fbc-e801-7ea4-2687-4105ddf99a93" LABEL="abmlinuxserver:0" TYPE="linux_raid_member"

```

---

### Post by darkod on 2020-01-28
Which are the clones of the two good disks and the overwritten disk? sdb, sdc and sde?

And don't try anything more with filesystem tools please... No fsck, mkfs or mke2fs...

---

### Post by bohnnyjliss on 2020-01-28
i believe sdb and sdc,

sda is the one i think they tried to install linux on, it it might have already had linux on it i dont know how it was setup in the first place

---

### Post by darkod on 2020-01-28
OK.

But you understand it makes big difference whether sda was or was not part of the array. We are basing all our assumptions on it.

There were 4 disks. One is dead, lets forget about it. There must be three others...

sda seems to have partition on it still. You can check with:
```
sudo parted /dev/sda unit MiB print
```

What does that say?

---

### Post by bohnnyjliss on 2020-01-28
```
parted /dev/sda unit MiB print
Model: ATA WDC WD40EZRZ-00G (scsi)
Disk /dev/sda: 3815448MiB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start    End         Size        Type     File system  Flags
 1      1.00MiB  2097152MiB  2097151MiB  primary  ext2         boot

```

---

### Post by bohnnyjliss on 2020-01-28
iirc this is how the drive looked when i got it in disk

[ATTACH=CONFIG]284931[/ATTACH]

---

### Post by darkod on 2020-01-28
Do you have maybe those screenshots of sdb and sdc?

---

### Post by darkod on 2020-01-28
Also, please post the same parted output for the other two 4TB disks, sdb and sdc.

---

### Post by bohnnyjliss on 2020-01-28
```
parted /dev/sdb unit MiB print
Error: The primary GPT table is corrupt, but the backup appears OK, so that will be used.
OK/Cancel? ok                                                             
Model: ATA WDC WD40EZRZ-00G (scsi)
Disk /dev/sdb: 3815448MiB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start    End         Size        File system  Name              Flags
 1      1.00MiB  2097152MiB  2097151MiB  ext4         Linux filesystem


```

```
parted /dev/sdc unit MiB print
Error: The primary GPT table is corrupt, but the backup appears OK, so that will be used.
OK/Cancel? ok                                                             
Model: ATA WDC WD40EMRX-82U (scsi)
Disk /dev/sdc: 3815448MiB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start    End         Size        File system  Name  Flags
 1      1.00MiB  2097152MiB  2097151MiB

```

---

### Post by bohnnyjliss on 2020-01-28
[ATTACH=CONFIG]284932[/ATTACH]

[ATTACH=CONFIG]284933[/ATTACH]

---

### Post by darkod on 2020-01-28
Unfortunately this looks worse and worse... If you take a good look at the parted output, sda has msdos table, and sdb and sdc have gpt (which we expect to see on sda too).

Not only that they installed OS over the raid disk, they created msdos table on it (and partitions of course).

Can you post one more output for comparison please?
```
lsblk
```

That will list the drives and partitions, I want to see how they compare with parted and blkid.

But honestly, you are far from getting this restored IMHO...

After you post the lsblk output we can try again to assemble.

---

### Post by bohnnyjliss on 2020-01-28
```
lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
loop0    7:0    0   956K  1 loop  /snap/gnome-logs/81
loop1    7:1    0  44.9M  1 loop  /snap/gtk-common-themes/1440
loop2    7:2    0  54.7M  1 loop  /snap/core18/1650
loop3    7:3    0  88.5M  1 loop  /snap/core/7270
loop4    7:4    0 260.7M  1 loop  /snap/kde-frameworks-5-core18/32
loop5    7:5    0  89.1M  1 loop  /snap/core/8268
loop6    7:6    0  54.4M  1 loop  /snap/core18/1066
loop7    7:7    0  14.8M  1 loop  /snap/gnome-characters/399
loop8    7:8    0  42.8M  1 loop  /snap/gtk-common-themes/1313
loop9    7:9    0 160.2M  1 loop  /snap/gnome-3-28-1804/116
loop10   7:10   0   4.2M  1 loop  /snap/gnome-calculator/544
loop11   7:11   0   3.7M  1 loop  /snap/gnome-system-monitor/123
loop12   7:12   0  1008K  1 loop  /snap/gnome-logs/61
loop13   7:13   0     4M  1 loop  /snap/gnome-calculator/406
loop14   7:14   0  14.8M  1 loop  /snap/gnome-characters/375
loop15   7:15   0  15.8M  1 loop  /snap/kolourpaint/44
loop16   7:16   0   3.7M  1 loop  /snap/gnome-system-monitor/127
loop17   7:17   0 156.7M  1 loop  /snap/gnome-3-28-1804/110
sda      8:0    0   3.7T  0 disk  
&#9500;&#9472;sda1   8:1    0     2T  0 part  
&#9492;&#9472;md0    9:0    0  10.9T  0 raid5 
sdb      8:16   0   3.7T  0 disk  
&#9492;&#9472;md0    9:0    0  10.9T  0 raid5 
sdc      8:32   0   3.7T  0 disk  
&#9492;&#9472;md0    9:0    0  10.9T  0 raid5 
sdd      8:48   0  55.9G  0 disk  
&#9492;&#9472;sdd1   8:49   0  55.9G  0 part  /
sde      8:64   0   7.3T  0 disk  

```

---

### Post by darkod on 2020-01-28
I would keep sde out. Like I said, only work with the disks from the previous array which are sda, sdb and sdc.

I don't like the fact that sda has partition on it, but mdadm can work ignoring that. I think we might do more damage trying to remove it right now. It will have to remain pending to do later.

So, right now I would stop the current md0, and assemble it only with sda, sdb and sdc.
```
sudo mdadm --stop /dev/md0
sudo mdadm --create --assume-clean --verbose --chunk=16M --level=raid5 --raid-devices=4 /dev/md0 /dev/sda /dev/sdb /dev/sdc missing
```

Please paste all mdadm output here. It would be interesting to see how it assembles it, which messages it gives.

Don't try anything else, not even mounting it RO. Lets see the mdadm output first.

---

### Post by bohnnyjliss on 2020-01-28
```
mdadm --create --assume-clean --verbose --chunk=16M --level=raid5 --raid-devices=4 /dev/md0 /dev/sda /dev/sdb /dev/sdc missing
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: /dev/sda appears to be part of a raid array:
       level=raid5 devices=4 ctime=Tue Jan 28 09:10:56 2020
mdadm: partition table exists on /dev/sda but will be lost or
       meaningless after creating array
mdadm: /dev/sdb appears to be part of a raid array:
       level=raid5 devices=4 ctime=Tue Jan 28 09:10:56 2020
mdadm: partition table exists on /dev/sdb but will be lost or
       meaningless after creating array
mdadm: /dev/sdc appears to be part of a raid array:
       level=raid5 devices=4 ctime=Tue Jan 28 09:10:56 2020
mdadm: partition table exists on /dev/sdc but will be lost or
       meaningless after creating array
mdadm: size set to 3906879488K
mdadm: automatically enabling write-intent bitmap on large array
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.

```

---

### Post by bohnnyjliss on 2020-01-28
i have the original drives in the recovery program and it seems to be working now that i know about the 16MB size.

dont know how much or whatever it can get, i need to try and continue both avenues so dont give up on me

---

### Post by darkod on 2020-01-28
Too bad you didn't post the mdadm output of the first try. As you can see above, the create time is now considered Jan 28. This is what you created earlier today.

I see it very difficult recovering from this honestly. If the recovery SW is giving you more hopeful results, go that way. Good that you had that first mdadm -E /dev/sdc output. That showed the chunk size as 16M clearly. And that is very important for re-assemble or scanning because the SW needs to know how big chunks to take.

---

### Post by bohnnyjliss on 2020-01-31
it looks like i'm able to get almost all the files but the directory structure isnt coming back very well. i have to grab the images "raw" some have filenames and some don't but almost all seem to work.

they will have to sift through the data and find out what is what.

---

