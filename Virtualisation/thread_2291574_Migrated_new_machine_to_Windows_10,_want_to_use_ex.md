---
title: "Migrated new machine to Windows 10, want to use existing raidz2 in ubunutu vm"
date: 2015-08-21
forum: Virtualisation
---

### Post by cliff-peeples on 2015-08-21
Hello all. I've been running Ubuntu for several months without a single hiccup. The server I was utilizing was getting old and tired, so I built a new machine that was just as capable, and quieter than the rackmount was. 

In the new configuration, I decided to go ahead and purchase Windows 10 so I can play some decent games, all while running Ubuntu in a VMWare 11 environment to act as my mediaserver. The installation was obviously as easy as pie, however I'm now stuck in thinking how I can take my existing raidz2 6 physical disk configuration and use it in the Ubuntu VM.

If I go into the Virtual Machine's settings and add a SCSI or SATA hard disk, select "Use a physical disk", then select the physical device I want to add to the VM, the following prompt makes me assume that the disks are going to be erased so that the disk files can be created on the physical drives. 

Before I hit "finish" and blow away my data on my raid array, am I off base here with the impression I'm getting from VMWare? Or is the disk file more or less a reference that points the virtual machine guest to a physical drive?

I have around 6TB of data currently and would rather not blow it away. 

Thanks in advance.

---

### Post by cliff-peeples on 2015-08-21
Solved. I took the plunge and went ahead and finished as specified above. First had the VM powered off, and added all drives from the array. When I powered the VM back on, I imported the array with no issues. The "vmdk" is as I suspected; a simple placeholder.

---

