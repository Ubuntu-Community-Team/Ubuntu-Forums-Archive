---
title: "Raid question and rsync cron question"
date: 2012-06-20
forum: Server Platforms
---

### Post by silverfox08 on 2012-06-20
Hi all, 2 questions.

I bought a used dell 2600 poweredge server to act as my file server.  I configured it using the hardware raid in a raid 1 configuration with (2) 300gb hard drives.  I couldn't afford to buy the drives I wanted and it came with them for cheap.  It's got room for 4 more drives and I plan to buy 4 more 300gb drives when i get some money.  

My question is, when I add the 4 new drives down the road and go in to configure the raid array, I assume I can add the 4 new drives to the existing array and change it to a raid 5 so it still shows up as a single logical drive?  Then ubuntu server will simply see that additional space?  I've just got the core ubuntu server installed.  No gui etc. and the only thing I've added is samba and rsync.  Will I need to re-partition the drive from ubuntu when I expand the array capacity?

I think I know what to do when the time comes in terms of rebuilding the array with the new drives, but if anyone here has experience with the dell hardware array management utility that could guide me that would be awesome!

I'm a newb to ubuntu server so sorry if this question is lame ;)

Second question.  I've got rsync setup to run as a cron job @hourly.  So it's syncing my file share to a NAS drive (western digital mybooklive) every hour.  Is this excessive?  I just figured it would give me the best backup scheme.  So if anything went wrong I'd have a copy from the previous hour.

I'm really happy so far.  The server is clicking along very nicely and I've got ssh access to it from my workstations.  Very nice and easy to manage w/out the gui etc. to deal with and pretty lightweight on the disk side.

any additional advice on the backup scheme is appreciated!

---

### Post by spynappels on 2012-06-20
I don't think you'll be able to add the disks to the array and convert it to RAID5, but you will be able to create a second RAID5 array using the 4 disks, giving you 900GB useable. You canthen create a partition on this array and mount it to a certain location such as /home/<username>/storage.

Another option would be to use LVM, but this is just as difficult (if not impossible) to retrofit.

An hourly rsync would be more than I'd use, but as it only transfers what has changed, it is not adding too much in the way of network overhead, so if it works for you, carry on.

---

### Post by silverfox08 on 2012-06-20
That's what I thought I might hear.  It will still work well for me though.  I can always add another machine or upgrade it if I outgrow the 900gb array plus the 200ish available on the first array.

I'm using a gigabit powerconnect managed switch with gigabit gear all around and my workstations are all using dual teamed nics so network traffic isn't too big of a deal.  I still have to figure out how to team the nics on the server and then latency shouldn't be a problem.

Thanks for the info and advice!

---

### Post by spynappels on 2012-06-20
> **silverfox08 said:**
>  I still have to figure out how to team the nics on the server and then latency shouldn't be a problem.

Have a look at this:

[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

HTH

---

### Post by silverfox08 on 2012-06-20
Thanks!  I had seen this.  I think it's time to give it a go.

---

