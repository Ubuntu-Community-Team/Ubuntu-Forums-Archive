---
title: "What do we do when there's a new release of Ubuntu CE?"
date: 2009-10-20
forum: Ubuntu Christian Edition
---

### Post by atyar on 2009-10-20
Just curious - when we're running the latest release (not the LT release), what do we have to do when the new release comes out?  

Is it something simple, like a 'sudo apt-get dist-upgrade', or do we have to download the new installation image, re-image our pc, etc.(which I doubt is the case)?

Thanks!

---

### Post by david_kt on 2009-10-20
> **atyar said:**
> Just curious - when we're running the latest release (not the LT release), what do we have to do when the new release comes out?  

Is it something simple, like a 'sudo apt-get dist-upgrade', or do we have to download the new installation image, re-image our pc, etc.(which I doubt is the case)?

Thanks!

From beta release to production release should be as simple sudo apt-get dist-upgrade. But for Jaunty, beta release repository and production release repository is different, so, you should follow the conversion method.

As for new release, we should be able to upgrade following ubuntu procedure, plus changing ubuntu ce repository.

But as recommended by ubuntu, clean install is normally more desirable, but you should have separate home partition or and/or backup home directory before installing new version.

DK

---

### Post by atyar on 2009-10-20
> **david_kt said:**
> From beta release to production release should be as simple sudo apt-get dist-upgrade. But for Jaunty, beta release repository and production release repository is different, so, you should follow the conversion method.

As for new release, we should be able to upgrade following ubuntu procedure, plus changing ubuntu ce repository.

But as recommended by ubuntu, clean install is normally more desirable, but you should have separate home partition or and/or backup home directory before installing new version.

DK

Well, on that subject, I'm not sure I really have a good partitioning scheme setup.  I'm working with about a 55GB hard drive.  I recently ran into space issues, after installing some apps, so I had to re-image and try a different partitioning scheme.  Thinking I'd just try to be safe, I created a 25Gig-ish primary partition first, using a mount point of '/boot'.  Then, I created a 2GB swap primary partition (I have 1GB of ram).  I used the rest of the space for a 26Gig-ish logical partition with simple '/' for the mount point.  I've read some more since then, and I think I should install again, with a different scheme.  How can I partition this best so that the O/S is on it's own partition, and then any user files, etc., are on another partition (so, just 3 total, including the swap file - btw, should the swap partition be 'primary' or 'logical', or does it matter?)?

Thanks again! :popcorn:

---

### Post by david_kt on 2009-10-20
> **atyar said:**
> I'm working with about a 55GB hard drive.  I recently ran into space issues, after installing some apps, so I had to re-image and try a different partitioning scheme.  Thinking I'd just try to be safe, I created a 25Gig-ish primary partition first, using a mount point of '/boot'.  Then, I created a 2GB swap primary partition (I have 1GB of ram).  I used the rest of the space for a 26Gig-ish logical partition with simple '/' for the mount point.  I've read some more since then, and I think I should install again, with a different scheme.  How can I partition this best so that the O/S is on it's own partition, and then any user files, etc., are on another partition (so, just 3 total, including the swap file - btw, should the swap partition be 'primary' or 'logical', or does it matter?)?

Thanks again! :popcorn:

You /boot partition is way to big. For example, my /boot folder is only 13.2 MB. For hard disk with single OS, I don't think /boot partition is necessary, so, may be you just combine /boot and / (no /boot partition).

The most important is to separate /home partition. So, I suggest 3 partition:

1. /      ====> 10 GB - 20 GB
2. swap   ====>  2 GB
3. /home  ====>  The rest ( 33 GB 43 GB).

For / partition is depend on how many software you would like to install. So, 10 - 20 GB is just a rough guidelines.

DK

---

### Post by atyar on 2009-10-20
> **david_kt said:**
> You /boot partition is way to big. For example, my /boot folder is only 13.2 MB. For hard disk with single OS, I don't think /boot partition is necessary, so, may be you just combine /boot and / (no /boot partition).

The most important is to separate /home partition. So, I suggest 3 partition:

1. /      ====> 10 GB - 20 GB
2. swap   ====>  2 GB
3. /home  ====>  The rest ( 33 GB 43 GB).

For / partition is depend on how many software you would like to install. So, 10 - 20 GB is just a rough guidelines.

DK

Thanks much - I'll install it again, a little wiser this time :popcorn:

---

### Post by atyar on 2009-10-20
oh, again I'm wondering - does it matter if the swap partition is primary or not(vs. logical)? And the swap partition should come second, correct?

---

### Post by david_kt on 2009-10-20
> **atyar said:**
> oh, again I'm wondering - does it matter if the swap partition is primary or not(vs. logical)? And the swap partition should come second, correct?

I think it does not matter. For me, I just put all primary partition. You could have maximum 4 primary partitions. But if you have very big harddisk (1.5 TB for example) and you want many OS there, then only you will need logical partition (partition within primary partition):

[http://www.faqs.org/docs/Linux-mini/Partition.html#PARTITION-3](http://www.faqs.org/docs/Linux-mini/Partition.html#PARTITION-3)

DK

---

### Post by atyar on 2009-10-20
Ahh - great link - thanks!
I've  been looking for such a discussion for quite some time :guitar:

---

### Post by shane2peru on 2009-10-20
I would second David's partition scheme.  And even go as far to recommend only about 10-15 on the first partition of /  I usually do 8-10 and have had two desktops installed kde and gnome and have never run into a problem.  12GB should give you more than plenty space, and 15 would be on a really safe side, 20GB you could install every application in the repo. :)  Ok, I just made that last part up.  I currently have:

Partition 1   /    9GB
Partition 2   swap  3GB
Partition 3   /home  rest of disk (215GB)

Shane

---

### Post by atyar on 2009-10-20
> **shane2peru said:**
> I would second David's partition scheme.  And even go as far to recommend only about 10-15 on the first partition of /  I usually do 8-10 and have had two desktops installed kde and gnome and have never run into a problem.  12GB should give you more than plenty space, and 15 would be on a really safe side, 20GB you could install every application in the repo. :)  Ok, I just made that last part up.  I currently have:

Partition 1   /    9GB
Partition 2   swap  3GB
Partition 3   /home  rest of disk (215GB)

Shane

Thanks for the info.  I'm wondering, though - I am using this laptop primarily for OpenOffice (docs are stored on my main pc in another part of the house, I'm just accessing them via the lan), Email (I don't keep many messages - usually read and delete most of them), and internet browsing.  I like to install and check out games and other applications from the repository as time permits, more so than creating and storing documents locally.  With that in mind, how would you skew my partitions to be safe?  Thanks!

---

### Post by shane2peru on 2009-10-20
> **atyar said:**
> Thanks for the info.  I'm wondering, though - I am using this laptop primarily for OpenOffice (docs are stored on my main pc in another part of the house, I'm just accessing them via the lan), Email (I don't keep many messages - usually read and delete most of them), and internet browsing.  I like to install and check out games and other applications from the repository as time permits, more so than creating and storing documents locally.  With that in mind, how would you skew my partitions to be safe?  Thanks!

Even so, with the time I have used Ubuntu I have never seen it go over 15GB for the / partition.  However since you don't have much need for home space, you could bump it up to 20GB if you install a ton of games.  I checked on IRC and no one had went over 15GB, so 20GB would be super extra safe. :)

Shane

---

### Post by atyar on 2009-10-21
> **shane2peru said:**
> Even so, with the time I have used Ubuntu I have never seen it go over 15GB for the / partition.  However since you don't have much need for home space, you could bump it up to 20GB if you install a ton of games.  I checked on IRC and no one had went over 15GB, so 20GB would be super extra safe. :)

Shane

Thanks!  That's basically what I wound up doing last night, before I read this post.  I think I put it a little higher, actually, but the same idea :)

---

### Post by livram79 on 2009-10-22
When will be available Ubuntu CE 9.10? I am coming from PClinuxos.

---

### Post by david_kt on 2009-10-22
> **livram79 said:**
> When will be available Ubuntu CE 9.10? I am coming from PClinuxos.

I do not have any target date yet, but I hope I could have beta release by end of November.

DK

---

