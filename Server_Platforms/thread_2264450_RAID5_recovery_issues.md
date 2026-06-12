---
title: "RAID5 recovery issues"
date: 2015-02-07
forum: Server Platforms
---

### Post by meesterblack on 2015-02-07
Home server running Ubuntu Server edition went down last weekend.  Power supply failure.  

After installing a new power supply and reboot, I noticed I lost my RAID5 array (4x 1TB drives).  Upon closer inspection, I noticed that two of the drives showed faulty.  Checking the drives individually the drives did not appear to be faulty.

Admittedly, I am rusty working with RAID arrays.  I don't use linux much any more at work and this is my home setup.  I'm perfectly good at searching all over Google-dom, as I have, but it appears I may have made some mistakes here so this is my last ditch effort to find a solution for data recovery.  Thankfully the *most* important data that was on the array was backed up, but half of it (non-critical but would like to have back) was not.

So when I went to re-mount the RAID array, it no longer existed.

I used mdadm to examine the drives, here is what I found:

[IMG]http://i.imgur.com/rjBV4hI.png[/IMG]

As I checked two of the other drives, they claimed that two of the disks in the middle (/dev/sdc1 and /dev/sda1) were faulty.

I searched and searched.  Ultimately I went with trying to re-assemble the array with the following command:

```

sudo mdadm --create /dev/md0 -v -l 5 -n 4 /dev/sd[bcae]1

```

It then rebuilt the array.  I should mention that while I re-installed the power supply, I had to unplug some of the SATA cords and reinstall them.  They may have not been re-connected in the same original order.  However, I assumed that mdadm was smart enough to recognize which drives went in which order.  Maybe I was wrong?   Anyhow, after I ran my command, I noticed that mdadm began assembling the array in a different order than I prescribed in the command. 

I got this:

[IMG]http://i.imgur.com/N2dYszb.png[/IMG]

Since it took a while to rebuild, I went to bed.  Then, the next morning I woke up and tried to see if I could remount the drive.  No luck.   No filesystem found (should have been ext4).  Tried running **fsck** but nothing was found.  Also tried e2fsck, etc.

Then I remembered something.  I vaguely remembered when building the array several years ago (yes this array has been running for several years with no failures) that I think I might have used 128k chunk sizes.  I noticed the newly re-assembled array was 64k.  

Now I have the sinking feeling that I may have hosed the array.  At any rate, I'm lost and don't know what else can be done, if anything.

Thanks to anyone who might be able to help!

---

### Post by CharlesA on 2015-02-07
You should have used mdadm --assemble --scan instead of --create.

Check this out:
[https://raid.wiki.kernel.org/index.php/RAID_Recovery](https://raid.wiki.kernel.org/index.php/RAID_Recovery)

---

### Post by meesterblack on 2015-02-07
I just noticed as I stared at the first screenshot that it was a 128k chunk size for sure -- was right there in front of me.

Also noticed something as decided to stop the array and attempt to rebuild with correct chunk size -- only 2 of the disks show filesystems.

[IMG]http://i.imgur.com/EEi9NiB.png[/IMG]

---

### Post by meesterblack on 2015-02-07
> **CharlesA said:**
> You should have used mdadm --assemble --scan instead of --create.

Check this out:
[https://raid.wiki.kernel.org/index.php/RAID_Recovery](https://raid.wiki.kernel.org/index.php/RAID_Recovery)


I did at first.

I got:

```
mdadm:  no devices found for /dev/md0
```

---

### Post by darkod on 2015-02-08
Just because it didn't want to assemble at first, it's no reason to try a --create, especially how you did it. If you use --create without the --assume-clean option, it will simply create new blank array. It makes sense that it didn't have a filesystem after that. It's basically a new array after the initial sync after --create. The --assume-clean tells it to create the array but not to sync it, but you have to be sure data is good for that to work.

You should have investigated more after the initial assemble failed, like with:
```
mdadm --detail /dev/md0
mdadm --examine /dev/sda1   (for each partition member of the array)
```

That will show more details to work with...

Right now after the --create I can't be sure you can recover any data from it. If you didn't create new filesystem on the new md0 maybe you can still save something. I'm not sure honestly...

---

### Post by darkapec on 2015-02-10
Yes --create likely wiped everything. Given that you still have not written any new filesystem to the RAID you maybe able to recover the superblock with fsck if that fails one of your last shots of file recovery is photorec. Photorec file recovery is not pretty... especially if you had lots of media. It may find everything, but you will likely be missing sections of video within a movie or a few seconds of audio in songs. 

Hopefully you are able to recover your data. 

I do not want to plagiarize anyones work so I will post a link to serverfault.com, this article is worth the read. A very in-depth test was made on the resilience of an MDADM RAID5 array and how to fix certain user made mistakes. 

[http://serverfault.com/questions/347606/recover-raid-5-data-after-created-new-array-instead-of-re-using](http://serverfault.com/questions/347606/recover-raid-5-data-after-created-new-array-instead-of-re-using)

---

