---
title: "Ubuntu Server AMI, by default EXT4 - How to convert to XFS for consistent backup?"
date: 2011-05-11
forum: Ubuntu Cloud and Juju
---

### Post by Amivit on 2011-05-11
Hi everyone. I'm a fairly unexperienced Linux user so bear with me please :) I loaded an instance of ami-06ad526f (11.04 Ubuntu Server, 32-bit) and have set it up as a LAMP for my blog. 

By default the ami is formatted as EXT4 - how exactly would I go about transitioning to XFS instead? The reason I want to do this is because the backup utility I plan on using ([ec2-consistent-snapshot]("http://alestic.com/2009/09/ec2-consistent-snapshot")) supports XFS and also others (such as EXT4) by using fsfreeze, but for some weird reason - [fsfreeze is not included in the AMI and I can not find out where to get it]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/712689"). SO, it would be much easier for me to just convert to XFS so the backup utility can use xfs_freeze.

The question is how, I am guessing you can't convert on a live file-system so my best guess is to take a snapshot, create a volume from this snapshot, attach and mount it to my current instance and use some tool to convert to XFS? I am guessing that this will also empty the drive, if true, I will just create an additional EBS and format it as XFS, mount the volume and copy the files - if that's the way to go what tool should I use to copy the files to ensure everything is identical including rights, etc.?

Thank you so much!!! Amivit - Aspiring Linux Guru ^^

---

### Post by kim0 on 2011-05-13
Please do not double post
[http://groups.google.com/group/ec2ubuntu/browse_thread/thread/4dda297fa5b226f1](http://groups.google.com/group/ec2ubuntu/browse_thread/thread/4dda297fa5b226f1)

---

