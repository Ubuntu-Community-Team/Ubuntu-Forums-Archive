---
title: "VMware using existing partition on a seperate drive?"
date: 2008-03-04
forum: Virtualisation
---

### Post by Dritzaike on 2008-03-04
I'm trying to get VMware to run a virtual machine of an existing Windows partition, but it seems to only allow a single drive when selecting partitions. I have my Windows partition on sda1, and my Gutsy and swap partitions on sdb1, but I can only select partitions from one drive at a time... Is it possible to get this setup running?

---

### Post by dcstar on 2008-03-05
> **Dritzaike said:**
> I'm trying to get VMware to run a virtual machine of an existing Windows partition, but it seems to only allow a single drive when selecting partitions. I have my Windows partition on sda1, and my Gutsy and swap partitions on sdb1, but I can only select partitions from one drive at a time... Is it possible to get this setup running?

There are numerous HOWTOs on how to use a physical Windows partition - but I don't like it myself (too easy to stuff things up).

I used the free VMware (Windows) utility to make a VM copy of my Windows partition and that runs fine - I don't even bother to boot into Windows any more and I don't risk any of the horror stories from those who try to use their physical Windows partitions.

---

### Post by Dritzaike on 2008-03-05
I think you misunderstood me; I've already been going through a [HOWTO (link)]("http://news.u32.net/articles/2006/07/18/running-vmware-on-a-physical-partition") on running a physical partition, but I've gotten stuck on step 12 of creating the virtual machine due to the fact that I have two HDs; Windows is on one, Ubuntu and my boot partition are on the other-- but in VMware, I can only select partitions to use off of one drive for each VM setup.

If I only select Windows, booting gets me a GRUB error 21, so I need at least one more partition in there (I'm not sure if the second needed partition will be the Linux install or swap, but I can figure that out once I manage to select partitions from both drives....). Because the Windows partition is on a drive by itself, I can't select the partitions on my other drive if I want to use it.

However, that VM copy idea sounds interesting, but I can't seem to find anything about it. Could you get me some more information on that?

---

### Post by Xkutzy on 2008-03-05
I think dcstar is referring to VMware Converter. Have a look on the VMware web sit on their Product Index under Management and Automation Products. Or just google VMware Converter.

---

### Post by obovgn on 2008-03-05
...try opening VMWare as super user with the command: sudo vmware from terminal.
This should give you the privilege to manage sda partitions and select them in your VM creation...

---

