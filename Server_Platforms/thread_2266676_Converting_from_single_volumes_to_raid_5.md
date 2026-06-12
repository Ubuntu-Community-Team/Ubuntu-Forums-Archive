---
title: "Converting from single volumes to raid 5"
date: 2015-02-24
forum: Server Platforms
---

### Post by Strandvasker on 2015-02-24
Hi there.

I'm currently running a server based on ubuntu server 10.04, it's a tough old girl, it's been running since back when 10.04 were new and exciting, so 4-5 years or so.

The system disk is an old 500 GB Samsung disk which were a disk I had lying around, already old at the time of the build. It has pulled off the incredible feat of running 24/7 since then, outliving several never data disks.

Currently I have 4 data disks in the server of which one is heading for the graveyard, it still mounts, but every time I start pulling data from it it dismounts, so in essence I currently have three 2 TB data disks. I ran 5 data disks at some point, had 3 disks die at different points in time, replaced a couple of them, but never bothered to get back to the full 5 data disk setup again. All single volumes, no raid.

Mainly the disks are filled with movies recorded from tv, a couple of series I watch, my ripped music collection and a tiny bit of important stuff. I already have the important stuff and the music backed up both on- and off-site with crashplan, so no real worries there. The rest doesn't really bother me, it's nice to have, but if a disk goes it goes and that's that - a bit annoying, but nothing major..

Now I'm thinking of reconfiguring it all to run raid 5 and I need your input on whether my plan will work or not.

My plan is to unplug the 3 data drives and retire the semi dead 4th one. I'll also retire my current system disk.

Then I'll buy 3 new 2 TB drives and partition them so each have a 50 GB system/swap partition and link those together as raid 1. I'll install a fresh version of ubuntu server on that. The remaining space on the 3 drives I will turn into a raid 5 volume.

Once that is up and running I'll mount one of my old 2 TB data drives and copy the data to the new raid 5 volume. Once that is done, I'll partition the old drive into a 50 GB system partition that gets added to the 3 existing raid 1 system partitions and then add the remaining space to the existing raid 5 data volume making it a 4 disk raid 5 data volume plus a 4 disk raid 1 system volume.

Then I'll repeat the process with the second of my old data drives, mount the drive, copy the data onto the new raid volume, then add the disk to the raid making it a 5 disk raid 1 system volume plus a 5 disk raid 5 data volume. 

Finally I'll mount the last of my old data drives, copy the data onto the new raid volume, but rather than adding the disk to the raid I'll unplug one of the new drives and replace it with the old drive. Naturally I'll make sure all the data from the old data drive has been written properly before unplugging the new drive. The raid should take care of rebuilding the data lost when I unplugged one of the new drives onto the last of the old drives. All in all I should end up with a 5 disk raid consisting of 2 new disks and 3 old ones and a brand new, barely used disk as a spare, to use once one of the old disks gives up the ghost. 

Question is, is it possible to do like described above?

---

### Post by darkod on 2015-02-24
It should work, but it's also risky. And it will stress the HDDs a lot. Are you aware that after adding each disk to the raid5 you need to do a reshape? It's not a simple add...

When you create the 3-disk raid5 mdadm will make the stripes on the disks accordingly. Two for data and one for parity. To make it a 4-disk raid5 it needs to restripe all disks to make a setup with 3 data + parity. And again the same to reshape it to 5-disk raid5. And by that time you will already have data on the array. Data that you will not have on the old disk(s) since you already copied it and added that old disk to the array.

For example, what happens if the last reshape goes wrong???

Also, are you sure you wanna run 5 disks raid5? That a large number of disks for a redundancy of only one disk...

Instead of keeping one disk aside (the 6th), what I would consider doing is this... Make a 6-disk raid6 array.

Since a raid6 can work with two disks (members) missing, you only need 4 for initial create. And you said you are buying 3 new. So... But the 3 new disks. Copy one of the old ones to any temp location (borrow a disk if necessary). Make a 6-disk raid6 with two members missing from the start (4 present, 2 missing). That should work... Copy all data to the array, from the temp location and from the other two old disks. Verify data is good... Add the two old disks to the array making it fully populated 6-disk array.

If a disk fails, you add a new and if during rebuild another disk fails the array is still running. It can handle two failed members. In raid5, especially with big arrays, there is big possibility a second disk to fail while doing a rebuild. If that happens, the array goes offline since the new disk is not synced yet, and another disk failed. raid5 can't handle two failed members of course...

That's what I would do.

PS. I was focusing only on the data array. You will make the raid1 for root as you mentioned, that's good. So you can have a 6-disk raid1 for root (OS).

PPS. I also forgot to mention, but you already know that probably. The 6-disk raid6 array will give you exact same usable space as your 5-disk raid5, 4x2TB=8TB. And there is no reshape. You create it once with missing members, and just add the missing disks later. That's why I like it better.

---

### Post by MAFoElffen on 2015-02-25
Agreed w/ Darko. Each time you do a reshape or rebuild, that really puts the disks at a state where they are really working harder than they do in probably the rest of the life of your array. Often, an older dive, if nominal, if it's going to fail at some time, it higher likely to fail during a high-stress event like that, So adding thing incrementally is going to put them in that high-stress state repeatedly. That and when you rebuild an array, there's a period of time before it drops out, where you risk corrupting what is there... and losing what is there anyways. (..and not to mention the time to do that x number of times!!!)

But-- you said you have all backed up already right? Instead of stressing the disks like that, wouldn't a better plan be to install and setup your new system, then restore your data to your newly built, completed array?

That's sort of the new theme of my current recovery plans. It takes so long and so much work to rebuild a large array with data, that it's just much simpler and faster just to start on a fresh system restore, then restore my data. (just saying...)

---

### Post by Strandvasker on 2015-02-26
@MAFo, I don't have everything backed up, just roughly 15 GB of important stuff (emails, tax papers, receipts and so on) and another 50 GB's of music (that I could just rip again from the originals if needed). The remaining 4-5 TB of movies is just something I would like to keep, but if **** happens, **** happens.. 

@Darkon, I didn't know you could create a raid with missing members right from the get go, it makes things a lot less complicated.

As for a 5 disk raid 5 vs. a 6 disk raid 6 I see your point. I have yet to see two disks fail at the same time, but still it's worth considering. Maybe just get 4 new disks rather than 3, build a 6 disk raid 6 with 2 missing with the 4 new disks, add the data from the 3 old disks, then add 2 old drives as the 2 missing. Would you recommending adding both the 2 missing at the same time or one at a time?

Finally, once the 6 drive raid 6 is up and running, would it make sense to replace one of the new drives with the last of the old drives, so that I have a brand new spare drive ready on the shelf or would it make better sense to leave the raid running with 4 new + 2 old and just keep the last old drive on the shelf as a spare?

---

### Post by rubylaser on 2015-02-26
These are all fine suggestions.  But I would keep your OS disks separate from your bulk data disks (I'd run the OS on a couple inexpensive 120GB SSDs in RAID1).  For bulk home media, I switched over to [SnapRAID]("http://snapraid.sourceforge.net/") from mdadm a few years ago and never looked back.  You could use your existing standalone data disks with no problem, and since data isn't striped, each disk works independently, and only one disk needs to be spun up to read a file (not the whole array).

If you are interested in setting up SnapRAID on Ubuntu, I have a tutorial in my signature.

---

### Post by darkod on 2015-02-26
rubylaser is the raid guru around here, so you can definitely investigate SnapRAID that he mentioned.

But to reply to the comment you made on my post. Yes, you can create mdadm with missing members, as long as you have minimum members specified according to the config. For example, a 6-disk raid6 needs at least 4 members to work. So you can create it with 4 disks present and 2 missing. You literary use 'missing' in the --create.

So, if you decide to go the mdadm way and raid6, the example commands to create the raid1 and raid6 would be (the disk names might change depending on your setup, you will modify that accordingly):
```
mdadm --create /dev/md0 --level=1 --raid-devices=6 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 missing missing
mdadm --create /dev/md1 --level=6 --raid-devices=6 /dev/sda2 /dev/sdb2 /dev/sdc2 /dev/sdd2 missing missing
```

One important note: Disks of "same" size do not have identical size depending on manufacturer and model. They can differ 1-2MB, sometimes even more but it should not be more than 10MB. So it is good practice when creating the last partition on the disk to leave 10-15MB unpartitioned at the end. That will make sure that you can create same size partitions even on slightly different disks.

Because you can add a bigger partition in raid but not a smaller one. And that is exactly what happened in another thread. The new 2TB disk is only about 1000KB smaller, which is not big difference, but you can't join it to the raid because of that small difference in size with the partitions already in the raid.

So don't use the disks up to the last sector. It can save you headaches in the future...

As for adding the missing disks, I would do it one at a time. Adding the first missing member is the crucial part because at that time you have a 4/6 array (4 out of 6). While the 5th member is still rebuilding, if any of the 4 fails the array will stop. And you might have issues getting to your data already on the array.

On the other hand, when the sync of the 5th disk finishes, you will have a 5/6 array and when adding the 6th disk if one of the 5 fails, the array is still working with 4 disks because it's raid6 and it can work with 4 out of 6.

In any case, it's smart to have as good backup as you can of the data, until the whole operation finishes.

---

### Post by Strandvasker on 2015-03-01
I've been looking into snapraid. I like the idea that the disks aren't striped, allowing me to mount them as single drives if need be. I dislike that I manually have to do snapraid sync (or set up a job to do it at regular intervals). Thing is, if I write a 2 GB file to disk 3 and disk 2 crashes before the sync is ordered, then a 2 GB chuck of disk 2 is going to be random garble once recreated on a new disk. 

While I can see snapraid working nicely for my collection of movies, I still need an alternative solution for the stuff that changes on a daily basis. I'm running my desktop computer completely silent with a small'ish ssd so I need my server as an offload for my daily storage needs too. So if I go with snapraid for my pretty static movie collection, I'll be needing a second solution for the more dynamic stuff.

Finally, my server board has only 6 sata ports, which means that doing 2 ssd's in raid 1 for root seriously cuts down on the number of data drives available. Adding more than 6 drives also becomes a physical challenge due to space available in the server case. I know both those issues could be solved by adding/replacing hardware, but I would prefer not to.

Currently I'm still leaning towards the raid 6 setup, maybe as a raidz2 instead to get the checksums and self healing abilities added to the mix. The more I read about zfs and raidz the better it sounds. Maybe even go freebsd to get native support?

As you can probably tell I'm still not decided and I value all your inputs, thanks a lot. ..and I'll keep in mind the bit about not using the entire disk but leave a little bit left to compensate for slightly different disk sizes, that's a world class tip if I ever saw one.

---

### Post by tgalati4 on 2015-03-01
I would get some newer hardware and set up a freenas server with ZFS.  Trying to make any RAID with old hardware, especially the PSU is risky.

---

### Post by darkod on 2015-03-01
ZFS with FreeNAS is one of the options but I don't think you can create raidz2 array with missing members, which means you would need all 6 disks free to work with. Since you don't have backup of the data or alternative location, you have to see how you will organize that.

Also, there is a ubuntu-zfs package for ubuntu, but I have not investigated if it's fully production ready. I have tested it in vbox, and it looked fine for a quick test. I even overwrote the OS disk with FreeNAS and it could import the zpool, and then again back to ubuntu. The test data was there. But that was only a short test and I am not sure about production use of zfs on linux (ubuntu). And again, I think you need all 6 disks from start, which is not what we discussed so far...

---

### Post by lukeiamyourfather on 2015-03-03
> **darkod said:**
> Also, there is a ubuntu-zfs package for ubuntu, but I have not investigated if it's fully production ready. I have tested it in vbox, and it looked fine for a quick test. I even overwrote the OS disk with FreeNAS and it could import the zpool, and then again back to ubuntu. The test data was there. But that was only a short test and I am not sure about production use of zfs on linux (ubuntu). And again, I think you need all 6 disks from start, which is not what we discussed so far...

ZFS on Linux is stable and ready for production. I've been using it for over year in a 24/7 environment on two machines with 36 drives each and on another few machines for personal use. It's possible to create a degraded RAID Z2 with a sparse file that then gets removed and replaced but of course there's risk in doing this as there is with running any array in a degraded state.

---

