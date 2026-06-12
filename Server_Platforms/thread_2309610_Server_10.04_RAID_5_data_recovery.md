---
title: "Server 10.04 RAID 5 data recovery"
date: 2016-01-12
forum: Server Platforms
---

### Post by jus71n742 on 2016-01-12
I have been out of the game for a while so bare with me on getting my information out. I had a Media Server set up with 4x1TB HDD for media and pictures and music etc. I recently moved and after a power failure and fears of one HDD going down I am trying to resurrect the Server again and do one of 2 things. 
1. Rebuild as is 
2 save any and all data I can and scrap everything and build a RAID 1.

So having said that, I power up the machine and it will boot to either a live CD or it will still boot to the HDD with problems.
If I boot off the live CD I can see Every HDD and test it using the built in Disk Utility and ALL 4 HDD's show healthy and functional. 
If I boot off the HDD I receive the error that /home isn't available from the 10 GB partition I created for the boot process.
[ATTACH=CONFIG]266672[/ATTACH]
Where I am unable to mount the home directory

[ATTACH=CONFIG]266673[/ATTACH]
Where Nautilus can't create directories

[ATTACH=CONFIG]266674[/ATTACH]

[ATTACH=CONFIG]266675[/ATTACH]
Every Disk shows this or something very similar

[ATTACH=CONFIG]266676[/ATTACH]
What happens when I attempt to start the RAID

I have no way to tell what order these are in, but some are the boot to HDD and the ones showing the Disk Utility are Live CD. So my question is basically can I rebuild the RAID? If not can I save the Data?

---

### Post by jus71n742 on 2016-01-12
UPDATE: I remembered the root password on the original installation.
[ATTACH=CONFIG]266677[/ATTACH]
is what I am getting for those commands
Sorry for the pictures, but its the easiest way I can think of to show exactly what I am seeing

---

### Post by darkod on 2016-01-12
You mistyped the mdadm -D, you put two slashes //. Try with:
```
mdadm -D /dev/md0
```

That should give details of the md device. You should also get details from each partition member separately:
```
mdadm --examine /dev/sda3
mdadm --examine /dev/sd[bcd]1
```

I noticed /proc/mdstat says the members are sda3, sdb1, sdd1, sdc1 (in that order). Does that sound right? Usually you would make identical layout on all disks so the partitions in the array would have same numbers. But this is not a requirement. You seem to be using partition #3 from sda, and partition #1 from sdb, sdc and sdd.

At this moment according to mdstat all partitions are marked as S - spares. The above commands should show you more details, especially the --examine.

PS. If you can get into the server by ssh you can work like that, and post output of the commands (in code tags) rather than pics. Also that way you can post the whole output as opposed to taking pics where you lose the output that scrolled out of the screen.

---

### Post by jus71n742 on 2016-01-12
I do not have the ability of getting it on the network for ssh at this point in time. 
I changed the mdadm error and it still shows the same output 
```
 mdadm -D /dev/md0
mdadm: md device /dev/md0 does not appear to be active

```

As far as that being the correct order I have no clue. I am currently looking for my notebook I used to build this RAID that I wrote down the correct configurations, but either the Mrs. tossed it or I just haven't found it. 

Here is the output of the requested commands
[ATTACH=CONFIG]266681[/ATTACH]

So I am showing 2 failed devices. SMART shows them as Healthy drives healthy
I have 2 brand new HDD's ready to load into this thing already. 
Guessing I should just scrap everything and rebuild Mirrored RAID?

---

### Post by darkod on 2016-01-12
Sorry, the jpg shows all gray... Can't see a thing to comment... Failed disks in mdadm do not necessarily mean broken disks. They could have been marked failed and after that they will not activate into the array by themselves, especially if two dropped at the same time. Is this a raid5? Since I can't see the jpg I can't know for sure.

But in general, if the md device does not start it has a reason for it... At the minimum, it thinks there are not enough devices to start the array.

---

### Post by jus71n742 on 2016-01-12
Sorry I noticed that and fixed the post.

Also pulled this data
[ATTACH=CONFIG]266685[/ATTACH]

---

### Post by darkod on 2016-01-12
Run it for all four partitions, even the ones showing removed state. To compare the data, event counter, etc... In that pic you have only sda3. If you can only take pics, run it one at a time for sdb1, sdc1 and sdd1 and post them too. And pls rotate the pic before posting... :)

---

### Post by jus71n742 on 2016-01-12
For some reason it won't roate after upload. 
[ATTACH=CONFIG]266687[/ATTACH]


If I run it on each HDD it shows 
```
 No md superblock detected on /dev/sda(12)
```

Also I notice, 2 and 3 are faulty removed. So to me it seems one has possibly actually failed while the other has experienced an error and been moved to faulty.   That an accurate assumption to make? 
The HDD bay I have in this system shows HDD 2 with a yellow light suggesting something is wrong with it. When I did a test run with it and put the brand new WD HDD in the case it went back to solid green with the rest of the HDD's

---

### Post by darkod on 2016-01-12
> For some reason it won't roate after upload.

That's why I said to do it BEFORE posting. Rotate and save it first, then attach it. It helps me not to strain my neck while reading it. :)

We are still missing the examine for the three partitions. Be very precise with the commands, there is no need to run it on anything else except the correct partitions. Run these three commands EXACTLY, don't change even one character, and post the pic of each.
```
mdadm --examine /dev/sdb1
mdadm --examine /dev/sdc1
mdadm --examine /dev/sdd1
```

Yes, right now it shows two disks as faulty/removed, but only one could be actually bad, The other could be recoverable. Post the output of those commands, and don't replace any disks yet. We need the output of the original disks.

---

### Post by jus71n742 on 2016-01-13
>  For some reason it won't roate after upload.  mistyped. I tried several ways to get possibly right side up. Ill see if cropping it off the phone helps

[ATTACH=CONFIG]266713[/ATTACH][ATTACH=CONFIG]266714[/ATTACH][ATTACH=CONFIG]266715[/ATTACH]

There should show up right side up.

---

### Post by darkod on 2016-01-13
I don't know if you noticed but all members now say 'synced'. Have you try assembling the array again? Something happened because both members showing failed earlier are now synced and in theory it should assemble.

There is only slight difference in the Events counters, which should be equal. For sda3 and sdb1 the counter is at 1358544 and for sdc1 and sdd1 1358540.

Try assembling it now with something like:
```
mdadm --assemble /dev/md0 --verbose
```

Or if that fails:
```
mdadm --assemble --scan --verbose
```

Also you can check if it's already assembled with:
```
cat /proc/mdstat
```

---

### Post by jus71n742 on 2016-01-14
I am getting resource busy and not enough to start the array, and wrong UUID. 

[ATTACH=CONFIG]266736[/ATTACH]

There a way to correct the UUID issue? I haven't found anything as of yet?

[ATTACH=CONFIG]266737[/ATTACH]

---

### Post by darkod on 2016-01-14
OK, lets go one by one...

1. Don't worry about the UUID messages right now. I think they are a result of the --scan option which scans all disks and partitions and it simply reports that some of them have no mdadm UUID, which is correct. That's normal.

2. It still tries to assemble but using only 2 members which fails of course. And it reports resource busy. It probably does not assemble because of the small difference in the Events counters, as I noted down previously. But this difference is so small that you should be able to successfully force it to assemble, without significant data loss (the counter difference is only 4 events).

Try something like this:
First check if any arrays are reported/assembled in /proc/mdstat (even if they can't mount and be used):
```
cat /proc/mdstat
```

If you see any array there, like md0, stop it first using the correct md device (like /dev/md0):
```
mdadm --stop /dev/mdX
```

Try forcing the assemble with correct member order that we have from your previous commands:
```
mdadm --assemble --force --verbose /dev/md0 /dev/sda3 /dev/sdb1 /dev/sdc1 /dev/sdd1
```

Hopefully that should get it going...

---

### Post by jus71n742 on 2016-01-14
[code] Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sda3[0](S) sdd1[3](S) sdc1[2](S) sdb1[1](S)
         3889466112 blocks

unused devices: <none>
[\code]
I ran the code you suggested and it flags device sdc1 and sdd1 but mounts. so now in theory I should be able to recover data correct?

[ATTACH=CONFIG]266745[/ATTACH]

---

### Post by darkod on 2016-01-14
Yes, now in theory you should be able to mount /dev/md0 either to its designated mount point or to a temporary mount point, and check if you can read the data. For example you can use the existing /mnt temp mount point.
```
mount /dev/md0 /mnt
ls /mnt
```

That will show you the folder structure and you can search what you want...

On next reboot it will probably mount automatically to its original mount point, so if you want to you can simply try rebooting the server. Now the array is good and it should reassemble automatically on boot.

---

### Post by jus71n742 on 2016-01-14
AWESOME. I really thought this thing had died and lost all the data. Now to test and see if any data is corrupted.
THANK YOU

---

