---
title: "[IDEA]- Stop constant hard drive parking which will kill drives"
date: 2007-10-20
forum: Ubuntu Brainstorm
---

### Post by martinw89 on 2007-10-20
Since Edgy, I've been using Ubuntu and this has always been an incredibly huge yet under the radar issue.  For some reason, there is a kernel bug that makes the hard drive park every 5 seconds.  This excessive parking will kill a drive as they are not spec'd to do this.  The official bug report is here [https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/92288](https://bugs.launchpad.net/ubuntu/+source/hdparm/+bug/92288).  As Hardy is intended to be a LTS release, I really believe this is important.

---

### Post by durand on 2007-10-20
What is hardware parking? I've been using ubuntu for about 3 years now since hoary 5.04 and I don't think I've noticed any drive problems..

---

### Post by martinw89 on 2007-10-21
When a hard drive is not in use, it is designed to physically "park" the head off the disk.  This is to prevent data loss if it is dropped etc.  However, for some reason, Ubuntu and other Linux distributions do this much more often then needed. I have heard this issue may not affect everyone, you may be lucky.  Check to see if when your computer is idle if the hard drive light flashes around every 5 seconds.  Again, this doesn't affect everyone but it is still important.

Edit:  On fact checking myself it seems that there are tons of opinions about this and I haven't actually found any "expert" opinions.  However, at the same time I can definitely say that on both my previous HP dv6000t laptop and my current Dell XPS m1330, there is an audible "click" that happens at a constant interval.  This does not happen on Windows so I think it's OS dependent.

Here is another bug report: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

---

### Post by FuturePilot on 2007-10-21
I have an HP dv6500t and I know exactly what click you are talking about. However it happens in Vista too! And I haven't noticed any sort of pattern to it. i.e. a regular interval.
If there was a problem I think Gutsy may have fixed it, because I haven't heard that sound in a while since installing Gutsy on it.

---

### Post by Megatog615 on 2007-10-21
Does this cause the drive to spin up when it's stopped(with the hdparm -S flag)? I haven't been able to keep my drives sitting still for over 10 seconds and on older versions of Ubuntu(dapper and below) I could keep them still for up to an hour.

---

### Post by martinw89 on 2007-10-23
Regarding the comment about Vista:  Yes, I have definitely heard of people having similar problems on other OS's (mostly Windows because of the number of people that use it).  However, for me, it is an Ubuntu only thing.  Adding "hdparm -B254 /dev/sda" to my rc.local was a workaround that worked for me in Ubuntu.

And to Megatog, I'm getting less sure what actually happens lol.  It seems that there are a lot of opinions because of how difficult it is to relate one noise that many people experience to an actual source for the problem.  Some people definitely report activity, while others report what they say is head parking.  People have objectively measured insane number of load cycles. ([http://web.glandium.org/blog/?p=54](http://web.glandium.org/blog/?p=54) retrieved from [http://ubuntuforums.org/showpost.php?p=1733578&postcount=61](http://ubuntuforums.org/showpost.php?p=1733578&postcount=61))

Yet, the more I read the more confused I get about this whole thing ](*,)  It makes sense for laptop disks to be parked quickly so that if they are dropped etc. there isn't a major disk failure, but it seems that Ubuntu (and sometimes other Linuxes and other OSs) are doing a quick "park, unpark" every few seconds.  Can anyone clear this up more?

---

### Post by zsouthboy on 2007-10-23
More than likely, your ATA/SATA controller is just blinking the hard drive light every x seconds, when a driver asks it for information.

"Parking" the read/write head of a HDD does nothing. It doesn't hurt anything - it could make seeks a little slower.

---

### Post by martinw89 on 2007-10-25
At this point this problem is picking up momentum. The bug report for this has been written about and [digged]("http://digg.com/linux_unix/Explanation_of_Ubuntu_Hard_Drive_Wear_and_Tear")  and all the similar bugs have been marked duplicates of [Bug #59695]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695").  The bug report page has a lot of interesting discussion.  One person mentioned this might not be power management, but that Ubuntu is accessing the drive every X seconds for some reason, possibly a logger etc.

zsouthboy, yeah I know, it doesn't seem like moving the head on and off the disk would do anything.  But drives are actually rated for a maximum number of load cycles.  For example, check out the [Fujitsu MHV2120AH at Directron]("http://www.directron.com/mhv2120ah.html").  The page doesn't have a clear layout but there is a rating for load/unload cycles.  In that drive's case it is 600,000.

---

