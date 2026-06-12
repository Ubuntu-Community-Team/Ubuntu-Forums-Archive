---
title: "Need help with backup solutions/filesystems"
date: 2006-03-20
forum: Server Platforms
---

### Post by ormandj on 2006-03-20
Hi,

I've been demoing ZFS for some time now, in Solaris. I'm not really a big fan of Solaris due to the pretty horrid HW support (understandable, but irritating regardless.) The general usability of the OS sucks too. It's made for 20+ year Solaris vets. ;)

That being said, I am looking for an alternative. As I was fairly impressed with Ubuntu Breezy Badger (I have a 1TB software raid5 running on Breezy) I was considering Dapper for my new needs.

My requirements are as follows, this is one example user. There are hundreds of these, so keep that in mind:

I have a user who has 25 gigs of data to backup. This will be the initial requirement. This will be transferred via an external HD. No problems here.

This user needs a backup kept for every day of the week, for one week. The last day of every week, for one month. The last day of the month, for one year.

The user needs the ability to grab any file from any of these points in time. Current, any day of the past week, any week of the past month, and any month of the past year.

Obviously, you can see why a full backup of every day would make this insanely expensive in storage. Considering there are a few hundred users like this. ;)

I need some kind of solution like ZFS snapshots. I take those once a day for the week, 4 times a month for the month, and once a month for a year.

I also need to be able to expand the storage pool/filesystem. I can't make new raids every time a user runs out of space/I need to add more users. IE - I'd like to buy a 30 drive cage or something, shove a few SATA drives in there, have something like raid6 (or something neat like zfs's raidz) running in software, so I could expand the array with more drives up to the max the cage could hold. Obviously, at some point I'd need to make another array, but I'd like to be able to expand at least a fair amount of time.

This is just one of the many questions I have, but this is the one on a rather short timeframe, so if you could help me out, I'd be super appreciative! Hopefully Ubuntu can work for me. :)

- David

---

