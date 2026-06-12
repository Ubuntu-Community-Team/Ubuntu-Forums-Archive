---
title: "Do I need RAID?"
date: 2008-07-04
forum: Server Platforms
---

### Post by devonps on 2008-07-04
Hi,

I'm in the process of constructing a NAS box for home use. This box will be used store (and possibly stream) all of my media, e.g. documents, music, videos, CD's, etc.

The NAS box will be constructed using Ubuntu 8.04 (64bit server edition) and access will be via Samba for the windows clients.

The box will contain x4 Samsung 500gb SATA HDDs.

Down to my question, do I need to install a RAID option? Or should I go for a nightly(?) backup solution?:confused:

Thanks for any advice.

---

### Post by ixus_123 on 2008-07-04
You most certainly do not need RAID :)

Go ahead and buy the extra disk(s) to mirror what you have in the NAS but instead of using it for RAID, stick it in a USB caddy and use it for backups / weekly or when ever.


The important thing to know about RAID is that RAID is not a backup.

Sounds obvious but I am amazed daily by how many technical clients can't grasp this.

As far as I am concerned, you should only need RAID if you need the added performance from using the card cache or a higher throughput or if you need your server / nas to be HA (High Availability). This way one disk can fail and your solution will still be up.

If you are hosting media, music etc, your content wont be changing that much. I imagine you'll only be serving to the household so high availability isn't a concern.  RAID wont protect from a hardware failure or file system corruption.  That's why it's better to have the back up.

Some people argue that a RAID 5 is a cheap way to create one large virtual disk for file storage - it is and that's great.  However, bearing in mind the above, you still need to back that up. So unless you have a another R5 to back up to, I think it's much easier to just use one disk for one type of thing.

What you might find handy is smartmontools.  This wil monitor the health of your disk and can warn you of any predicted failures.

There is a tutorial at the link that shows you how to set it up to monitor and email you if any issues arise.
[http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu]("http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu")

Good luck, save your money on RAID cards and backplanes and invest in an external drive for backups. :)

---

### Post by windependence on 2008-07-04
Excellent post ixus_123! I gave you a thank you because so many n00bs think RAID is a substitute for backup.

-Tim

---

### Post by devonps on 2008-07-05
ixus,

Thanks for the reply - that's the kind of response I was hoping to get.

Steve.

---

### Post by cariboo on 2008-07-05
I agree with windependence, I think a lot of people want a raid array just because it is cool and don't really understand what raid is.

Jim

---

### Post by fjgaude on 2008-07-05
Well, for me, raid means reliability and high throughput (quickness). A failed drive (raid5) or two (raid6) doesn't take the system down... and under heavy load the speed of a multidrive array, software or hardware, gets the job done like no single-drive could.

---

### Post by windependence on 2008-07-05
I would agree wirth you in a situation where you really need all that bandwidth, but even on some of my production servers, I don't need that much throughput. If you are running a site with thousands of concurrent users and millions of page views, then OK yeah, you need it. Of course you would be running several load balanced servers then and would have the money to do all that. In the OP's situation though, he really won't see any difference.

-Tim

---

### Post by vpsville on 2008-07-06
For your needs you don't need RAID, and I'd guess you don't need 4 disks either.  But since you also want to do something interesting and have some fun, making a RAID-5 disk might be more satisfying even if it is overkill.

But as other posters have mentioned, be sure to backup your data to somewhere else.  Your RAID drives can fail, and if its a software RAID, it might be very problematic to rebuild the RAID if the motherboard it was based off of is no longer functioning.

A proper 3Ware RAID controller would give better reliability, but you still need a backup if any important must have data is on that RAID.

---

### Post by fjgaude on 2008-07-06
Software raid, **mdadm** style, doesn't require arrays to be re-built after a hardware failure, motherboard, etc. All that's required is replace the failed hardware item and reboot... the array comes up, even if OSs and MBs have been changed out. That's because the superblock on each drive is used to determine how the array was created and is used to auto assemble it.

It hasn't been easy to fully understand the full features of mdadm but it has been worth the time spent.

---

### Post by pdwerryhouse on 2008-07-07
> **devonps said:**
> The box will contain x4 Samsung 500gb SATA HDDs.

If you're not using RAID, are you going to be running each of these four drives independently (ie, a filesystem on each)? Or are you planning on using LVM or striping to make them one big filesystem?

Doing the latter will mean that you have four times the chance of losing all your data, just by losing a single drive. Sure, you'll have backups, but there's the time factor to reinstall it, inconvenience and you'll probably lose some data saved between the time of your last backup and the time of the crash.

Disk is cheap. Use 750Gb disks instead of 500Gb and run RAID5.

---

### Post by windependence on 2008-07-07
Not necessarily.

[http://www.novell.com/coolsolutions/appnote/19386.html](http://www.novell.com/coolsolutions/appnote/19386.html)

RAID is not the end all some people think it is. There is NO substitute for good verified backups. As the article above states, if you have a backup of the metadata, you should be fine. If LVM was so failure prone, it wouldn't be an integral part of enterprise systems such as RHEL, SLED, and Ubuntu server.

As an admin who has been through nightmares with RAID volumes, I can tell you that isn't all roses and cherries either.

-Tim

---

### Post by devonps on 2008-07-07
> **pdwerryhouse said:**
> If you're not using RAID, are you going to be running each of these four drives independently (ie, a filesystem on each)? Or are you planning on using LVM or striping to make them one big filesystem?

Doing the latter will mean that you have four times the chance of losing all your data, just by losing a single drive. Sure, you'll have backups, but there's the time factor to reinstall it, inconvenience and you'll probably lose some data saved between the time of your last backup and the time of the crash.

Disk is cheap. Use 750Gb disks instead of 500Gb and run RAID5.

I intend to run each drive seperately, but I haven't decided on the final configuration. For example, I might decide to run x2 of the drives in the NAS and keep 2 for backup purposes, or run x3 drives (again seperately) and keep 1 for backup.

One thing I do know is that I won't need to keep everything backed up as I own a large %age of the media I intend to make available to the household.

---

