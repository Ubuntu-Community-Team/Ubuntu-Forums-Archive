---
title: "New Server: MDADM + SSD + TRIM = Working?"
date: 2015-01-20
forum: Server Platforms
---

### Post by LewsTherin2005 on 2015-01-20
Sorry if this has been asked 100 times, but I've been researching this for days and all the info I find is either outdated, incorrect, or contradictory.

To make a long story short, we are gearing up to replace an aging MySQL server (Debian).
This time we are going all out, utilizing SSDs (Enterprise class drives) and switching to Ubuntu Server.
In theory, these drives should have sufficient GC routines and over-provisioning to limit the need for trim...but I'd feel a lot better if trim was working.

The plan is to run Ubuntu server w/ 6x SSDs in RAID10.
I've loaded Ubuntu Server 14.04.1 and I am starting simple just to make sure things are working as expected.

So far I have created a single RAID1 device using MDADM and 2 drives. It has been formatted EXT4 and **/** mounted.
Running "fstrim -v /" seems to work, I get xxxxx bytes trimmed in response. A subsequent run returns 0.


However, I'm not 100% sure I trust this, so I've been looking for another way to validate if trim is in fact working.
In doing so, I found the following guide: [http://lightrush.ndoytchev.com/random-1/checkiftrimonext4isenabledandworking](http://lightrush.ndoytchev.com/random-1/checkiftrimonext4isenabledandworking)
When I do the above test on a SINGLE, NON RAID drive, it works perfectly.

However, when I attempt to run the same test on the RAID1 array, "hdparm --read-sector xxxxxxx /dev/sda" does not appear to reference the file in question when I convert the hex to text.
It appears that "hdparm --fibmap tempfile" is returning the wrong LBA information, so I can't prove that trim is still working under raid.

So my questions are this...
1) Am I going overboard trying to prove TRIM is working...is the fact that fstrim issues a response proof that it is working?
2) If not, is there a way to get the above test to work with raid, or another means of testing trim that would work?

Thank you for your time

---

### Post by MAFoElffen on 2015-01-21
The rhel 6.5 Release notes announced:
> 
TRIM Support in mdadm:
The mdadm tool now supports the TRIM commands for RAID0, RAID1, RAID10 and RAID5

(rhel and Centos is now at v7.x). The rpm package of mdadm that came with rhel 6.5 was mdadm-3.2.6-7.el6_5.2.src.rpm. (version 3.2.6-7). But note how that compares below. (I may be wrong, but this is how I read it...)

(Ubuntu) The current version of mdadm in trusty is 3.2.5-5... utopic and vivd is 3.3-2... So it looks like to get that support, you would either have to go at least utopic... I'm thinking not just mdadm, but with the matching kernel support that went with that.

---

### Post by LewsTherin2005 on 2015-01-21
> **MAFoElffen said:**
> The rhel 6.5 Release notes announced:

(rhel and Centos is now at v7.x). The rpm package of mdadm that came with rhel 6.5 was mdadm-3.2.6-7.el6_5.2.src.rpm. (version 3.2.6-7). But note how that compares below. (I may be wrong, but this is how I read it...)

(Ubuntu) The current version of mdadm in trusty is 3.2.5-5... utopic and vivd is 3.3-2... So it looks like to get that support, you would either have to go at least utopic... I'm thinking not just mdadm, but with the matching kernel support that went with that.

Appreciate the feedback.
I think I read an article or post discussing the same information.

I guess what has me confused is I see many posts/articles saying that if the "fstrim" command is working...then your fine...but just a few that say otherwise to make me wonder.

Fstrim is in fact working for us in raid 1 (haven't tried raid 10 yet)...so I'm inclined to think it's working just fine.
I just wish the hdparm commands would work to know for sure.

14.10 may be an option, but given it's shorter support timeline...it could be tough sell.
On the other hand, the SSD manf is telling me that their GC and OP should be sufficient, so I'm beginning to think we should just go for it and if trim isn't working...so be it.

---

### Post by MAFoElffen on 2015-01-21
I'm wondering if a request for a backport to 14.04LTS would go anywhere on that(?) I know of people who have installed newer mdadm on older Ubuntu versions, but I haven't been that brave on my own(, without others trying it first).

I keep hearing trim is not working for LVM RAID1 (LVM mirrors, not under mdadm) but, honestly, I lost track of the status of that.

---

