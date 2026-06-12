---
title: "Ubuntu Storage Server - 5TB"
date: 2012-05-18
forum: Server Platforms
---

### Post by Dazza on 2012-05-18
Hi all.

I have 5x1TB drives. I plan to add more of different capacities later on.

I was considering ZFS, however great it is though, for a home environment it doesn't suit my needs because:
1.) You can't expand the pool as and when (you need to create a new pool). 
2.) You can't simply disconnect the drives and read them in another machine, for example if the server OS takes a dump (OpenIndiana or w/e).
3.) RAID size is limited by the smallest drive.

I am considering using Windows Home Server v1 again, as I liked the Pool features and it reads S.M.A.R.T data to indicate failure very early on.

Would mdadm or something similar utilising Ubuntu achieve what I am after? I do not need full redundancy as most of the data is movies - however certain files I would want full redundancy.

I am sharing to Windows computers, and would expect writes 40-100Mb/s as that is what I get at present.

---

### Post by Cheesemill on 2012-05-18
Have a look into Greyhole.
[http://www.greyhole.net/](http://www.greyhole.net/)

---

### Post by darkod on 2012-05-18
And what exactly are you after?

I would mdadm will give you much more flexibility than any version of windows. First, are you talking about some kind of windows software raid, or hardware raid with a controller or bios configuration?

Wouldn't hardware raid be limited to the smallest disk size too?

With mdadm you work with partitions, you the disk size doesn't really matter.

Also, hardware raid can't be easily read on another machine unless the same controller or board is used I guess. With mdadm you get exactly that, you can read the disks on any linux machine. It doesn't even need to have linux, you can boot the machine in live mode with a cd and read the disks.

You didn't say how much capacity you need? Will it be like two disks in RAID1 (for the redundancy you need), and the other three just for storage without raid?

---

### Post by Dazza on 2012-05-18
The whole intention is software RAID. 

I am going to put all 5TB in the RAID array. My concerns are  if the drive fails, will I kill another drive inadvertently rebuilding the data from the increased load?

I have looked at Greyhole, but mdadm seems more established hence why I arrived here!

---

### Post by Cheesemill on 2012-05-18
I mentioned Greyhole because it sounded like you weren't after a normal RAID solution

> 3.) RAID size is limited by the smallest drive.
As it is when using any sort of RAID, hardware or software. Using Greyhole allows you to mix and match drives of different sizes

> I do not need full redundancy as most of the data is movies - however certain files I would want full redundancy.
Normal RAID gives you a fixed level of redundancy over the entire array, you cannot specify more or less redundancy for certain directories. Using Greyhole you can specify a level of redundancy per share (No redundancy, 2 copies, 3 copies etc).

---

### Post by darkod on 2012-05-18
I wouldn't say rebuilding is such a risk for the disk. Otherwise no raid array would exist.

Depending how you want to organize it, you will probably be looking into RAID5 or RAID6.

Or a two disk RAID1 with three disk RAID5. But this will have the smallest usable capacity I guess.

---

### Post by Dazza on 2012-05-18
Greyhole seems to fulfill my requirements.

However it doesn't seem to do much that WHS didn't do.

Is there a reason why I would use Greyhole? Or even Amahi? And just use Windows Server 2011 for backups?

---

### Post by rubylaser on 2012-05-18
What else do you expect Greyhole to do?  Your original post explained what you wanted to accomplish and it can do all of those things when coupled with smartmontools and a working email setup to alert you to disk errors. If you're happy with WHS and you understand it, I'm not sure why you'd be looking at a different solution. You've already paid to buy WHS, so it's not a debate over cost. 

[mhddfs]("http://romanrm.ru/en/mhddfs") is another option, although Greyhole does seem a little more suited to what you're trying to accomplish, and I've never gotten fantastic throughput with mhddfs (limited to around 60 MB/s). It is VERY simple to setup though :)

---

### Post by Dazza on 2012-05-18
> **rubylaser said:**
> What else do you expect Greyhole to do?  Your original post explained what you wanted to accomplish and it can do all of those things when coupled with smartmontools and a working email setup to alert you to disk errors. If you're happy with WHS and you understand it, I'm not sure why you'd be looking at a different solution. You've already paid to buy WHS, so it's not a debate over cost.

It's because I started researching ZFS and it's thrown serious spanners in the works.

I was just seeing if there was a faster alternative to WHS, and it seems there isn't. 

If greyhole does raid5 but has no performance benefit then I'm back to mdadm discussion.

---

### Post by rubylaser on 2012-05-18
> **Dazza said:**
> 
I was considering ZFS, however great it is though, for a home environment it doesn't suit my needs because:
1.) You can't expand the pool as and when (you need to create a new pool). 
2.) You can't simply disconnect the drives and read them in another machine, for example if the server OS takes a dump (OpenIndiana or w/e).
3.) RAID size is limited by the smallest drive.

Also, I'd like to explain some of these better, as what you've written isn't technically correct.
1. You can expand a pool, you just need to add a new vdev to the pool.  So, if you have an array built out of mirrors, you just add a new mirrored vdev and you can add it to the pool.  This works with raidz or raidz2/3 as well.
2. Sure you can, you just need a system that understand ZFS and you can mount the array on that machine. You can even do this on the Ubuntu LiveCD now as zfsonlinux works great with pools up to version 28.
3. This is how all RAID systems work.

---

### Post by Dazza on 2012-05-18
> **rubylaser said:**
> Also, I'd like to explain some of these better, as what you've written isn't technically correct.
1. You can expand a pool, you just need to add a new vdev to the pool.  So, if you have an array built out of mirrors, you just add a new mirrored vdev and you can add it to the pool.  This works with raidz or raidz2/3 as well.
2. Sure you can, you just need a system that understand ZFS and you can mount the array on that machine. You can even do this on the Ubuntu LiveCD now as zfsonlinux works great with pools up to version 28.
3. This is how all RAID systems work.

1. Expanding by adding drives 'as and when' isn't really achieved in ZFS (you need to add 3 drives at a time minimum)
2. If the files are shared over all the disks, you can't. It does it by block size not file. Parts of 1 file can be on other discs.
3. Greyhole and WHS DE don't. You add a 2TB drive to a 1TB pool of drives and you use all of the storage. I appreciate these aren't strictly speaking 'proper RAID' but they offer similar redundancies over JBOD.

---

### Post by rubylaser on 2012-05-18
> **Dazza said:**
> It's because I started researching ZFS and it's thrown serious spanners in the works.

I was just seeing if there was a faster alternative to WHS, and it seems there isn't. 

If greyhole does raid5 but has no performance benefit then I'm back to mdadm discussion.
How is it going to be faster, you mentioned getting speeds up to 100MB/s?  That's almost saturating a gigabit ethernet connection.  I guess I need to know, what do you mean by faster (bootup times, network transfer speeds, etc)?  And, what would your ideal system do and what tasks would it perform?  

mdadm works great, and I really like it for home use (my tutorials in my signature would walk you completely through the process), but I also really enjoy ZFS as well.

---

### Post by rubylaser on 2012-05-18
> **Dazza said:**
> 1. Expanding by adding drives 'as and when' isn't really achieved in ZFS (you need to add 3 drives at a time minimum)
2. If the files are shared over all the disks, you can't. It does it by block size not file. Parts of 1 file can be on other discs.
3. Greyhole and WHS DE don't. You add a 2TB drive to a 1TB pool of drives and you use all of the storage. I appreciate these aren't strictly speaking 'proper RAID' but they offer similar redundancies over JBOD.

1. You don't need 3 disks if you're extending a mirror. You'd only need 2 disks in this scenario.  If you're extending a 8 disk raidz2, you'd want to add a second 8 disk raidz2 vdev if you wanted to expand.  ZFS just takes better planning than traditional RAID.
2. You're talking about something different than I am.  You're mentioning individual disks, you can't do that with mdadm or other hardware solutions either (unless it's a RAID1).  Disk parity by it's nature requires that enough disks are present to assemble the array to read the data from it.  But, you can easily take the disks out of one machine and import them on another and read the data.
3. These aren't traditional RAID solutions and only provide 1 disk worth of parity not something I'd want with 5TB on the line.  I opt for RAID6/raidz2 on larger home arrays just for added protection.

I'd suggest you stick with what you know and use WHS if you already have a license for it.

---

### Post by Dazza on 2012-05-18
> **rubylaser said:**
> How is it going to be faster, you mentioned getting speeds up to 100MB/s?  That's almost saturating a gigabit ethernet connection.  I guess I need to know, what do you mean by faster (bootup times, network transfer speeds, etc)?  And, what would your ideal system do and what tasks would it perform?  

mdadm works great, and I really like it for home use (my tutorials in my signature would walk you completely through the process), but I also really enjoy ZFS as well.

I am happy with the performance of WHSv1, but it is running 2k3 so it's very old.

I have rebuilt my server to the following:
Intel DQ67SW
Intel Xeon E3 1230
16GB non-ECC RAM

Hence why I am trying to rebuild it as best as I can rather than just going back to normal. It's running ESXi and Vt-d also.

What I want:
Redundancy with monitoring. WHSv1 offers SMART data readouts and notifications. 
Ideally I want the disks to maintain whole files individually (so I can pull the drives and access the files worst case)
Ability to add drives. I tend to stick to 1TB but I may use 2TB or 3TB as their prices are dropping. This is my main gripe with ZFS as I can't add individual disks as and when.

I'll check out your signature, thanks!

---

### Post by Dazza on 2012-05-18
The other reason I am apprehensive about ZFS is that I do not have ECC memory. I just seem to be stuck with every solution because of my relatively low end setup. 

I would love ZFS but there is lots of risk - or at least lots of people over stating the risk!

---

### Post by rubylaser on 2012-05-18
> **Dazza said:**
> I am happy with the performance of WHSv1, but it is running 2k3 so it's very old.

I have rebuilt my server to the following:
Intel DQ67SW
Intel Xeon E3 1230
16GB non-ECC RAM

Hence why I am trying to rebuild it as best as I can rather than just going back to normal. It's running ESXi and Vt-d also.

What I want:
Redundancy with monitoring. WHSv1 offers SMART data readouts and notifications. 
Ideally I want the disks to maintain whole files individually (so I can pull the drives and access the files worst case)
Ability to add drives. I tend to stick to 1TB but I may use 2TB or 3TB as their prices are dropping. This is my main gripe with ZFS as I can't add individual disks as and when.

I'll check out your signature, thanks!

Thanks, this clears up your goals :)  mdadm is not able to do this... "Ideally I want the disks to maintain whole files individually (so I can pull the drives and access the files worst case)", because it uses parity.  But, you can always pop the disks into a new system and mount the array.  The SMART portion is easy to do, and I cover that in one of my tutorials, so you should be able to get that working. You can easily add disks to mdadm, but it would use the smallest disk size by default (it's using traditional raid, so that's how it works).

That's a very nice setup you have there.  I assume that you built the [all-in-one]("http://www.napp-it.org/doc/downloads/all-in-one.pdf") with napp-it on Openindiana originally?

---

### Post by rubylaser on 2012-05-18
> **Dazza said:**
> The other reason I am apprehensive about ZFS is that I do not have ECC memory. I just seem to be stuck with every solution because of my relatively low end setup. 

I would love ZFS but there is lots of risk - or at least lots of people over stating the risk!

Non-ECC memory isn't more dangerous than it is in any other fileserver situation, and frankly ZFS picks up checksum errors and repairs them that no other filesystem would.  The only downside with non-ECC memory is that you "might" get a flipped bit and ZFS wouldn't be able to identify it.  This really isn't a big deal imho in a home environment. One of my fileservers at home has (9) 2TB disks in raidz2 with 8GB of non-ECC memory, and it's worked great.  It's even picked up a few checksum errors (and repaired them).

What other risks have you heard about?

---

### Post by Dazza on 2012-05-18
> **rubylaser said:**
> Non-ECC memory isn't more dangerous than it is in any other fileserver situation, and frankly ZFS picks up checksum errors and repairs them that no other filesystem would.  The only downside with non-ECC memory is that you "might" get a flipped bit and ZFS wouldn't be able to identify it.  This really isn't a big deal imho in a home environment. One of my fileservers at home has (9) 2TB disks in raidz2 with 8GB of non-ECC memory, and it's worked great.  It's even picked up a few checksum errors (and repaired them).

What other risks have you heard about?

Mostly that if a disk fails in a raidz1 array, when you are rebuilding the stress on the other disks can cause those to fail also.

EDIT: Also power failure, killing the array.

Maybe I will just bite the bullet, buy an additional 1TB drive and do raidz2 - if ZFS really is that good and you have had good luck with non-ECC memory.

> **rubylaser said:**
> Thanks, this clears up your goals :)  mdadm is not able to do this... "Ideally I want the disks to maintain whole files individually (so I can pull the drives and access the files worst case)", because it uses parity.  But, you can always pop the disks into a new system and mount the array.  The SMART portion is easy to do, and I cover that in one of my tutorials, so you should be able to get that working. You can easily add disks to mdadm, but it would use the smallest disk size by default (it's using traditional raid, so that's how it works).

That's a very nice setup you have there.  I assume that you built the [all-in-one]("http://www.napp-it.org/doc/downloads/all-in-one.pdf") with napp-it on Openindiana originally?

Originally I had a simple Pentium E5200 running WHSv1 (and it's been perfect for around 2 years - hence my reluctance to migrate!)

I think ZFS is back on the table. I won't fill 4tb of usable data and if I do I will just delete movies (or save up and buy enough to mirror a new pool).

Now the question is, mdadm or zfs - performance and security wise!

Both of those posts are invaluable to me. Many thanks dude, owe you a pint most definitely.

---

### Post by darkod on 2012-05-18
I'm not a real expert in raid, but I think you guys are focusing too much on the "smallest disk size" thing.

Nothing is stopping you to have one /dev/md0 device from the smaller disks, and /dev/md1 from the larger ones after you buy them, right?

Even if you insist the storage space to be continuous, you have a solution if you add LVM on top of the raid.

Configure you initial raid device(s), configure LVM to use them as physical devices.

When you add later more disks, you don't even need to grow the existing array even if the disks are the same size. Configure new raid device, add it to the LVM, expand the LVs, that's it.

On the recovery side, even though LVM adds another "layer" on top of raid, it doesn't make it much more complicated to read the array on another machine.

Of course the minimum raid requirements will have to be met anyway. If it's raid1, you need one working disk at least. For raid5 you can read the array if a single disk is missing, but not more, etc.

I might be wrong about the above, but it looks to me like a nice solution when you want to expand later.

---

### Post by rubylaser on 2012-05-18
> **Dazza said:**
> Mostly that if a disk fails in a raidz1 array, when you are rebuilding the stress on the other disks can cause those to fail also.

EDIT: Also power failure, killing the array.


Originally I had a simple Pentium E5200 running WHSv1 (and it's been perfect for around 2 years - hence my reluctance to migrate!)

I think ZFS is back on the table. I won't fill 4tb of usable data and if I do I will just delete movies (or save up and buy enough to mirror a new pool).

Now the question is, mdadm or zfs - performance and security wise!

Both of those posts are invaluable to me. Many thanks dude, owe you a pint most definitely.

That's one of the reasons, I suggest raidz2/RAID6 for home use, just for an added layer of protection (coupled with offsite backups of your critical items (home movies, family pictures, etc).

I've had great luck with both mdadm and ZFS over the years. I also use both at work on MUCH fancier hardware than I have at home and neither has let me down.  ZFS is not the absolute peak in terms of performance, but you shouldn't have a problem saturating gigabit ethernet (my array I mentioned earlier writes around 350 MB/s and reads at 525 MB/s on the machine, and I'm limited by my old AMD 4600+ X2 processor).  So, performance wise, ZFS is "good enough" for home use. If you haven't added napp-it to Openindiana, you should as it makes managing everything VERY simple.

It terms of data security, ZFS is outstanding, so I'd give that an edge over mdadm + ext4/xfs/jfs/etc.

---

### Post by Dazza on 2012-05-18
> **rubylaser said:**
> That's one of the reasons, I suggest raidz2/RAID6 for home use, just for an added layer of protection (coupled with offsite backups of your critical items (home movies, family pictures, etc).

I've had great luck with both mdadm and ZFS over the years. I also use both at work on MUCH fancier hardware than I have at home and neither has let me down.  ZFS is not the absolute peak in terms of performance, but you shouldn't have a problem saturating gigabit ethernet (my array I mentioned earlier writes around 350 MB/s and reads at 525 MB/s on the machine, and I'm limited by my old AMD 4600+ X2 processor).  So, performance wise, ZFS is "good enough" for home use. If you haven't added napp-it to Openindiana, you should as it makes managing everything VERY simple.

It terms of data security, ZFS is outstanding, so I'd give that an edge over mdadm + ext4/xfs/jfs/etc.

What about power failure? Will the array become unreadable worst case scenario or can I recover it?

NTFS seems to deal with power loss pretty great.

---

### Post by Gyokuro on 2012-05-18
OP forgot to post more specs about HW but ZFS with less then 8GB RAM is no fun

---

### Post by rubylaser on 2012-05-18
> **Dazza said:**
> What about power failure? Will the array become unreadable worst case scenario or can I recover it?

NTFS seems to deal with power loss pretty great.

Power failure is no problem because of Copy on Write (there is no RAID5/6 write hole in ZFS).  I would always suggest you have a UPS in front of your server to gracefully shut it down, but ZFS is very resilient.

---

### Post by rubylaser on 2012-05-18
> **Gyokuro said:**
> OP forgot to post more specs about HW but ZFS with less then 8GB RAM is no fun

He said a couple posts back that he has 16GB of RAM and a Xeon E3-1230 processor.

---

### Post by CharlesA on 2012-05-18
> **Dazza said:**
> What about power failure? Will the array become unreadable worst case scenario or can I recover it?

NTFS seems to deal with power loss pretty great.
Get a UPS and set it to shut the machine down if there is a power failure. A controlled shutdown is always better then a hard shutdown no matter the file system.

In any case, ruby is spot on. ;)

---

### Post by rubylaser on 2012-05-18
> **darkod said:**
> I'm not a real expert in raid, but I think you guys are focusing too much on the "smallest disk size" thing.

Nothing is stopping you to have one /dev/md0 device from the smaller disks, and /dev/md1 from the larger ones after you buy them, right?

Even if you insist the storage space to be continuous, you have a solution if you add LVM on top of the raid.

Configure you initial raid device(s), configure LVM to use them as physical devices.

When you add later more disks, you don't even need to grow the existing array even if the disks are the same size. Configure new raid device, add it to the LVM, expand the LVs, that's it.

On the recovery side, even though LVM adds another "layer" on top of raid, it doesn't make it much more complicated to read the array on another machine.

Of course the minimum raid requirements will have to be met anyway. If it's raid1, you need one working disk at least. For raid5 you can read the array if a single disk is missing, but not more, etc.

I might be wrong about the above, but it looks to me like a nice solution when you want to expand later.

This is another idea, although I like having only one array to manage with extra parity disks (RAID6 rather than two RAID5 arrays), and I really like to avoid LVM (one extra thing to troubleshoot if something goes wrong), unless I need it for LVM snapshots.

---

### Post by Dazza on 2012-05-18
Final Q I forgot about.

To run a DLNA/transcoding application, will I still be okay to use ZFS?

---

### Post by CharlesA on 2012-05-18
> **Dazza said:**
> Final Q I forgot about.

To run a DLNA/transcoding application, will I still be okay to use ZFS?
You should be fine.

---

### Post by airtonix on 2012-05-19
> **Dazza said:**
> Hi all.

I have 5x1TB drives. I plan to add more of different capacities later on.

I was considering ZFS, however great it is though, for a home environment it doesn't suit my needs because:
1.) You can't expand the pool as and when (you need to create a new pool). 
2.) You can't simply disconnect the drives and read them in another machine, for example if the server OS takes a dump (OpenIndiana or w/e).
3.) RAID size is limited by the smallest drive.

I am considering using Windows Home Server v1 again, as I liked the Pool features and it reads S.M.A.R.T data to indicate failure very early on.

Would mdadm or something similar utilising Ubuntu achieve what I am after? I do not need full redundancy as most of the data is movies - however certain files I would want full redundancy.

I am sharing to Windows computers, and would expect writes 40-100Mb/s as that is what I get at present.


1) you can expand pools by create new vdevs and adding them to the pool.

2) yes you can.

3) meh

---

### Post by memilanuk on 2012-05-19
So backing up a few posts... what exactly was wrong with greyhole again (assuming for a home setup)?

---

### Post by CharlesA on 2012-05-19
> **memilanuk said:**
> So backing up a few posts... what exactly was wrong with greyhole again (assuming for a home setup)?
Pretty much this, I suspect:

> **Dazza said:**
> Greyhole seems to fulfill my requirements.

However it doesn't seem to do much that WHS didn't do.

Is there a reason why I would use Greyhole? Or even Amahi? And just use Windows Server 2011 for backups?

---

### Post by rubylaser on 2012-05-19
Greyhole is a nice solution and would have fit the OP's goal, although in terms of data security, it's no match for ZFS raidz2.

---

### Post by memilanuk on 2012-05-19
While I suppose the OP having already had a WHS license in hand... generally speaking if there is a MS solution and an equivalent Linux solution... I tend to prefer the Linux version (assuming its not obscenely annoying to implement, which sometimes can be the case).

As far as ZFS... I've used it a bit on a FreeNas 0.7x install for a while; seemed to work well enough on an older P4 w/ 1GB RAM and 3 500GB HDDs, but then again I wasn't trying to set any speed records.  The whole OpenIndiana/Nexenta/FreeBSD thing bugs me a little, though.  I know a lot of people have set up some pretty whamplidyne storage systems using them, judging by the 'Data Storage' forum over on [H]ardForum... for whatever reason, I'm not sure that route is for me.  Very much looking forward to btrfs coming of age...

---

### Post by kgatan on 2012-05-19
I have been over this question for a long time and still have not decided on the best approach.

At the moment it seams like FreeBSD with ZFS will be my best option. But that is mostly because i want zfs + encrytion which pretty much limits you to Nas4Free, Solaris and FreeBSD.

There is also a packaging of FreeBSD called ZFSGuru which is still in its early stage but focused on a web gui for easy sharing and ZFS setup.

Performance wise over cifs/nfs Nexenta and Solaris seams to shine over all the other when using ZFS.

You can also evaluate unRaid which is a more and more popular alternative for home storage use. It has both a free and paid license, 3 disk array is free where 6 and 21 disks are licensed starting from $69.

Personally i love Linux over all the above but i just cant live with the write hole problem since its silent and undetectable.
If I have understand correctly the problem will occur during a rebuild of an array and toast your data.

---

### Post by Cheesemill on 2012-05-19
> **kgatan said:**
> I have been over this question for a long time and still have not decided on the best approach.

At the moment it seams like FreeBSD with ZFS will be my best option. But that is mostly because i want zfs + encrytion which pretty much limits you to Nas4Free, Solaris and FreeBSD.

There is also a packaging of FreeBSD called ZFSGuru which is still in its early stage but focused on a web gui for easy sharing and ZFS setup.

Performance wise over cifs/nfs Nexenta and Solaris seams to shine over all the other when using ZFS.

You can also evaluate unRaid which is a more and more popular alternative for home storage use. It has both a free and paid license, 3 disk array is free where 6 and 21 disks are licensed starting from $69.

Personally i love Linux over all the above but i just cant live with the write hole problem since its silent and undetectable.
If I have understand correctly the problem will occur during a rebuild of an array and toast your data.

Have you seen the napp-it web front end for running ZFS on Solaris / OpenIndianna ?
[http://www.napp-it.org/doc/downloads/napp-it.pdf](http://www.napp-it.org/doc/downloads/napp-it.pdf)

---

### Post by rubylaser on 2012-05-19
> **Cheesemill said:**
> Have you seen the napp-it web front end for running ZFS on Solaris / OpenIndianna ?
[http://www.napp-it.org/doc/downloads/napp-it.pdf](http://www.napp-it.org/doc/downloads/napp-it.pdf)

Napp-it is awesome, I use it on my home box.  This is a great suggestion for users that have never used ZFS and even makes the transition to Solaris/Openindiana/EON/Nexenta very simple because it basically sets all of the common fileserver pieces up for you.  

If a user wants to go the FreeBSD route ZFSguru is also pretty nice too.

---

### Post by rubylaser on 2012-05-19
> **kgatan said:**
> I have been over this question for a long time and still have not decided on the best approach.

At the moment it seams like FreeBSD with ZFS will be my best option. But that is mostly because i want zfs + encrytion which pretty much limits you to Nas4Free, Solaris and FreeBSD.

There is also a packaging of FreeBSD called ZFSGuru which is still in its early stage but focused on a web gui for easy sharing and ZFS setup.

Performance wise over cifs/nfs Nexenta and Solaris seams to shine over all the other when using ZFS.

You can also evaluate unRaid which is a more and more popular alternative for home storage use. It has both a free and paid license, 3 disk array is free where 6 and 21 disks are licensed starting from $69.

Personally i love Linux over all the above but i just cant live with the write hole problem since its silent and undetectable.
If I have understand correctly the problem will occur during a rebuild of an array and toast your data.

You could always use zfsonlinux, it works well at this point and will work with version 28 pools.  Personally, if you want encryption, ZFS pool version 31+ (only on Solaris) is really the best option imho.  It is completely integrated with ZFS and works very well.  This doesn't matter for me in my home, so I run Openindiana on one server and Ubuntu + mdadm on my other box.

Unraid is another option, but I have a hard time paying that price for what boils down to a customized Slackware. Ubuntu  + snapraid can basically accomplish the same thing; drive spanning + parity. Obviously, it takes a little bit more work, but it is free and open source.

---

### Post by kgatan on 2012-05-19
I had no idee about napp-it. Looks very interesting!
Will definitly try it on solaris 11 asap!

Thanks!

---

