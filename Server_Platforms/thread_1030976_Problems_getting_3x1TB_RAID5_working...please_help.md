---
title: "Problems getting 3x1TB RAID5 working...please help!"
date: 2009-01-04
forum: Server Platforms
---

### Post by mOOky on 2009-01-04
I have a newly minted (translated: scuttled from a former gaming rig) Ubuntu server with 3 shiny new Samsung 1TB drives to use for a home NAS/media server.

I want to use 'mdadm' to create a RAID5 using the ReiserFS file system, but am having issues getting the array active.

I'm able to create partitions on each disk using 'parted' and then set the 'raid' flag to 'on'.  I then, just for grins and giggles, laid out a ReiserFS on each partition to validate the disks were good.

I can even create the array using mdadm just fine, but this is as far as I get.  Once the array is created it won't come online as it appears that it is having issues with one or two of the disks.

I've attached a bunch of files (containing the dmesg entries, the mdadm --create and mdadm --query output, etc.).

Is there something I'm doing wrong?

I used the following command to create the array:
	**mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sd[abc]1**

In looking at the dmesg output, it is possible one of my new drives is pooched.  How would I validate this or refute it?  Is there a drive testing tool (hardware level) in Ubuntu?

---

### Post by mOOky on 2009-01-04
OK...I thought I posted the files...lemme try this again... [it appears I forgot to hit 'upload' how embarrassing]

---

### Post by Den_Citronen on 2009-01-05
I don't know that much about RAID, however... Parhaps one of these links can help you:
[http://linux-raid.osdl.org/index.php/Linux_Raid](http://linux-raid.osdl.org/index.php/Linux_Raid)
[http://www.gagme.com/greg/linux/raid-lvm.php](http://www.gagme.com/greg/linux/raid-lvm.php)

---

### Post by eldaria on 2009-01-05
Could you also post the output of:

```

sudo fdisk -l

```

---

### Post by jolx on 2009-01-05
[this]("http://wiki.archlinux.org/index.php/Installing_with_Software_RAID_or_LVM") might be of use

---

### Post by mOOky on 2009-01-05
> **eldaria said:**
> Could you also post the output of:

```

sudo fdisk -l

```

Yeah, sorry, I didn't include it in the original as it didn't seem that interesting...  here it is.

---

### Post by mOOky on 2009-01-05
> **jolx said:**
> [this]("http://wiki.archlinux.org/index.php/Installing_with_Software_RAID_or_LVM") might be of use
While the Arch article is a nice walk-through, I am neither installing Arch, nor using LVM, and it doesn't contain any troubleshooting advice whatsoever.  Aside from that, there are a number of inaccurate statements as to the speed and performance of RAID levels (the author asserts that RAID5 is as fast as RAID0 which is patently false) and other misleading ideas.  Thanks for trying though.

---

### Post by mOOky on 2009-01-05
> **Den_Citronen said:**
> I don't know that much about RAID, however... Parhaps one of these links can help you:
[http://linux-raid.osdl.org/index.php/Linux_Raid](http://linux-raid.osdl.org/index.php/Linux_Raid)
[http://www.gagme.com/greg/linux/raid-lvm.php](http://www.gagme.com/greg/linux/raid-lvm.php)
Those are both good resources, especially the OSDL site which has a plethora of information.  After scanning it for an hour or so I think that I've done everything correctly, but still may have a bad disk.  What I really need now I think is a physical disk testing tool, something like SpinRite to determine if my drive is bad.

---

### Post by smileypaul on 2009-01-05
Just as a test, format each disk individually as ext3, and mount them...

---

### Post by fjgaude on 2009-01-05
Well, **after** you create an array you have to add a filesystem to it:

```
sudo mkfs -t reiserfs /dev/md0
```

then you have to create a mountpoint for the array:

```
sudo mkdir /home/raid
```

or whatever point you wish.

Let us know how you are doing.

---

### Post by mOOky on 2009-01-05
> **smileypaul said:**
> Just as a test, format each disk individually as ext3, and mount them...

This is a good plan.  I am going to do just that and then do a fsck on them.

I also plan on diagnosing them with the SMART hdd tools suggested by this post [https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware) as referenced by nick_h here: [http://ubuntuforums.org/showpost.php?p=5442053&postcount=2](http://ubuntuforums.org/showpost.php?p=5442053&postcount=2)

---

### Post by mOOky on 2009-01-06
Well, the SMART control library commands yielded that the second disk (sdb) *does* in fact have errors.  The offline selftest stopped with read errors. [result attached]

The other two disks don't have errors in their SMART logs so I didn't bother doing offline tests.

I'm now performing a 'badblocks' scan of sdb to see what I get, and will most likely be submitting an RMA request to samsung for a replacement disk tomorrow.  I'll post the badblocks results and followup from samsung for closure.

Incidentally, I *was* able to create individual file systems on all three drives and mount them, and even write test text files to them all, without errors.  I can only assume that the fsck for ext3 doesn't actually test the disk, but only looks for the journal to be unclean or something.

If badblocks doesn't show anything up, I may run the DFT tool from the UBCD.

---

### Post by mOOky on 2009-01-06
Well, I'm now solidly convinced it is a bad disk.  After running 'badblocks' for about 5 hours it reported over 600 bad blocks on the read portion of the full destructive test, at which point I had to disconnect my session.

[in related news, is there any way to reconnect to an SSH shell session that was disconnected?]

The interesting thing is that the bad blocks (of 4096 bytes) seem to travel in chunks of 1 block then skip some, then another four consecutive blocks...rinse, repeat as necessary.  Does that mean there is possible damage on the platter due to a crashed head?

In any case, I'm starting the RMA process with Samsung, who also has their own test tool which I'll run this evening.

Thanks for everyone's help and ideas, especially nick_h who didn't reply to this thread, but posted the link to the Hardware page in another board which lead me to the 'smartctl' and 'badblocks' tools that confirmed my suspicions.

Cheers.

I'll close this out when I get a replacement drive and have my RAID array setup.  After reading some of the posts y'all referred me to it sounds like going with an LVM table on top of the RAID array will be the best bet for a scalable storage solution that I can expand down the road with minimal hassle.

---

