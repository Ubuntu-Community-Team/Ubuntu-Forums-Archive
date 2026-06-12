---
title: "Need to reduce the size of a volume group"
date: 2012-04-22
forum: Server Platforms
---

### Post by ClientAlive on 2012-04-22
Hi,

I wasn't familiar with the Ubuntu 12.04 Server partitioner and wasn't sure how to make it create two volume groups on the same pv (/dev/md0 is the only pv I have available) - or how to set the size of that volume group. What I ended up doing is allow the volume group to be the entire size of the pv and then made a logical volume in it that is much smaller. So what I have is a single volume group of around 6 TB in size on /dev/md0 and a single logical volume in it that's around 30 GB in size. That logical volume is where Ubuntu server is installed to (mounted as / ). I need to find a way to reduce the size of the volume group (not the logical volume, the volume group) to match the size of the logical volume on it, so I can use the resulting free space to create a second volume group for other logical volumes to reside in. I'm seeing a lot of info on the net about changing the size of logical volumes but nothing for changing the size of volume groups. If there's another way to reach my goal besides the resizing route, I'm open to it - just need an idea what to do. Ultimately I need to have, not one, but two volume groups on the single physical volume. One of which containing Ubuntu server in a single logical volume, the other for other purposes. Can anyone please help me along?


Thanks in advance
Jake

---

### Post by darkod on 2012-04-22
This thread is rather old but post #5 seems to have what you need:
[http://www.linuxquestions.org/questions/linux-enterprise-47/shrink-lvm-without-dataloss-557746/](http://www.linuxquestions.org/questions/linux-enterprise-47/shrink-lvm-without-dataloss-557746/)

---

### Post by ClientAlive on 2012-04-22
> **darkod said:**
> This thread is rather old but post #5 seems to have what you need:
[http://www.linuxquestions.org/questions/linux-enterprise-47/shrink-lvm-without-dataloss-557746/](http://www.linuxquestions.org/questions/linux-enterprise-47/shrink-lvm-without-dataloss-557746/)


Thanks darkod,

At first I wasn't sure it was addressing my concern, then I saw the last couple lines in post #5 talk about shrinking the volume group. There's 2 things I'm a little confused about though. (1) Like the folks in a couple posts following, I don't quite understand the example command given for it. I mean, I see the pattern in the command syntax but I don't see anything in it where you specify the size you want the volume group to end up being. This leads me to what was my first impression...

(2) What I read about vgreduce in it's man page led me to believe it's for something entirely different. It's very  possible that I've misunderstood what's said there though, so I'd love to get the straight scoop on vgreduce.

What I got out of the man page was it's something comparable to failing and removing a drive from a raid array. (I mean that would be a good analogy). I thought it was saying that, for instance, if you had a volume group, who's physical volume included multiple physical partitions, you could use vgreduce to remove one of the partitions from the underlying physical extent upon which the volume group sat.

For example: Let's say you had a volume group and the physical volume it was on was sda1, sda2, sda3. vgreduce could then do something like remove sda3 from the underlying physical volume - thus ending up with a the same volume group on top of sda1 and sda2 only.

Am I mistaken about this? Can someone please explain? If vgreduce can reduce the volume group - without changing the underlying physical extent - what is the right way to use the command?
-----------------------------------------

Edit: I notice there's a command called vgsplit as well. It's just that the way they describe it in the man page is confusing. Perhaps their description is more technically correct to how lvm works, but it dosn't match the way I've been thinking about it.

---

### Post by ClientAlive on 2012-04-22
Well, I took the lazy man's way out   :p

I chose to just rename my volume group and logical volume to more sensible names rather than try to put the host system on it's own logical volume and have a second one for other things. For one, once I started to see what's involved in resizing a volume group it just struck me as absurdly complicated, even painful. For another, the more I thought about it the more I realized this is probably the wisest way to go. Keep the host system on the same volume group as everything else - that way I have the ability to resize it (along with any other logical volumes) in the future if I need to. I'm marking this one as solve. Thanks for your help though darkod.

Jake

---

