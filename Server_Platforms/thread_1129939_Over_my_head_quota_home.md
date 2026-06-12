---
title: "Over my head: quota /home"
date: 2009-04-19
forum: Server Platforms
---

### Post by volkswagner on 2009-04-19
Hi,

I am trying to setup quota's for the first time.  I have quota installed a part of the "Perfect Server" setup on SourceForge.

I am interested in setting a quota for user that is using ftp and jailed to /home/user.

My /home is on a dedicated partition /dev/hda2.  I tried adding the quota string to /etc/fstab and running the commands as described [here]("http://tomclegg.net/debian-quota").  This created quota arguments for / and /home partitions.

I received an error at the step:

```
 sudo quotaon -a
```

```
Cannot find quota file on /home [/dev/sda2] to turn quotas on/off
```

My questions:
Is the error normal, until I setup user/group quotas on this partition?
Can I have quota on two partitions?
Or, does having quota on / run on the entire file system regardless of partitioning?
I think this may be false as I tried to view usage for the user in question and it showed up as zero.  Either I am checking with incorrect syntax or the usage in /home is not showing up.  Perhaps it shows as zero because quota is not setup for the user...duh?
Are there any detailed How_to's for setting quota up for the first time?

---

