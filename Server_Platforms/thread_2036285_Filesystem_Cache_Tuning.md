---
title: "Filesystem Cache Tuning"
date: 2012-08-01
forum: Server Platforms
---

### Post by kfzig on 2012-08-01
Hello,

Full disclosure, my linux proficiency is in that wonderfully uncomfortable "knows enough to be dangerous" phase.

I've migrated from Openfiler to Ubuntu Server as an iSCSI/NFS box since Openfiler is about as stagnate as a distribution can get and, further, the limitations to the GUI interface were frustrating at best.  My hardware is a poor-man's white-box with lots of physical disks attached to regular SATA/SAS HBAs, leveraging MD for software raid.  The box's primary function is that of an iSCSI target for my home/home-office vSphere 5 Essentials setup.  As such, I'm using Ubuntu 11.10 (the best-available back when I rebuilt the box with Ubuntu) and a slightly modified build of IETD from what was automatically installed via APT several months ago; I followed instructions to build a subversion of the iscsitarget package which contained a fix for a bug which was causing the IET daemon to crash.  IETD has operated relatively flawlessly since.

Regardless of what one may say about this in a 'production' environment, I've been using write-back caching on all of my iSCSI VMFS and NTFS LUNs for the drastic performance increase; I've got more than sufficient battery backup to cover for any foreseeable power issues and has been working admirably without a hitch.  I understand the risks and have chosen to accept them rather than spend a couple of grand on proper hardware raid controllers.

Back when I was using Openfiler, the disc cache usually consumed most of the system's 32GB of memory.  However, under Ubuntu, memory utilization never rises over about 50%.  This is what I'm asking for help with; I apparently don't at all understand enough about how linux works under-the-hood to be able to put together a good enough google query to get the answer to this; the only reason for this that I can figure is that somewhere under the hood the disk caching daemon or driver is configured with a hard-limit of maximum memory utilization, in which case what I want to know is where and how do I change it?  Otherwise, I'd really appreciate someone explaining what's going on and how I might remedy my performance issue or at least pointing me to documentation that I can read on my own that speaks to what I need to know.

Thanks for reading all of this, and thanks ahead of time for any assistance.

Regards,
kfzig

---

