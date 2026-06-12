---
title: "Softwarei RAID1 with mdadm---possibility of data corruption?"
date: 2010-06-13
forum: Server Platforms
---

### Post by isaacjgs on 2010-06-13
Hi guys.

I have a question about software RAID using mdadm. I looked here

[https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)

It says that mdadm "works very well." This page here

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

says that "Note: Be aware of the fragile state of RAID support in Ubuntu and what  it takes to get a reliable raid setup ([https://wiki.ubuntu.com/ReliableRaid](https://wiki.ubuntu.com/ReliableRaid)),  but most of them has fixed since Ubuntu 8.10." Yet a little further down and it also says "The RAID software included with current versions of Linux (and Ubuntu)  is based on the 'mdadm' driver and works very well."

But then I jumped to [https://wiki.ubuntu.com/ReliableRaid](https://wiki.ubuntu.com/ReliableRaid)

and it says this, right under the heading "Rationale"

"Unfortunately Ubuntu's md (software) raid  configuration seems to suffer from a little incompleteness. The assembling of arrays with "mdadm" has been  transitioned from the Debian startup scripts to the hotplug system (udev  rules), however some bugs defy the hotplug mechanism and other things  that are generally expected (as in just works in other distros) are  missing functionality in Ubuntu:"

and a further down, I read this:

"Blocked and flawed hotplugging mechanisims. Mdadm is setting up arrays according to  unreliable superblock information. (Device "minor" numbers, labels and  hostnames in superblocks are not sure to be unique and can be outdated.)  This is combined with the idea of fixing the unreliability by limiting  array assembly with information from mdadm.conf. (Defining PARTITIONS,  ARRAY, HOMEHOST lines.) Consequently this forces setup tools, admins and  installers to create mdadm.conf files and subjects them to the exact  same reliability problems. The only thing mdadm can (and  should) rely on when assembling is the high probability of uniqueness of  UUIDs. (i.e. don't rely on admins, tools or install scripts to set up a  mdadm.conf, use only UUIDs as references for device nodes/userspace."

So it sets up arrays according to unreliable superblock information?

Does this mean that there is a higher risk of data corruption using mdadm's software RAID1 than when compared to just using a single hard drive? I mount /home to a RAID1 SATA pair of 500 GB hard disks, formatted with ext3, with my Ubuntu Operating System on a IDE 40 GB hard drive. I want to know if my ext3 RAID1 SATA pair is just as reliable as a single ext3 500 GB hard drive or not.

It's just that it seems like I'm getting mixed messages.

---

