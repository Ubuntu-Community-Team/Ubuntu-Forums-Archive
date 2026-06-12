---
title: "Curious - If VR is Setup, but not Powered On, Does it still take up Resources?"
date: 2014-12-08
forum: Virtualisation
---

### Post by Rick St. George on 2014-12-08
Downloaded and installed VirtualBox and setup space, but haven't installed anything to it yet. It shows "Powered Off". But has it already allocated the Memory etc to it, or not until I "Power it On"?

Just curious because my newly installed Opera browser seems to lock up my HD, so wondering what happened to my computing power.

Have 1GB Ram, 250 GB HD (about 100 free), 1.8 Ghz dual CPU in Dell Precision 390 workstation. 

Thanks,
Rick

---

### Post by TheFu on 2014-12-08
virtualbox has kernel drivers  and bridge slots that are loaded after install which take some memory and CPU, but each VM doesn't/shouldn't get any resources until run.

1G of RAM is not really enough to do any HVM visualization.  It isn't just the RAM that you allocate to the VM, but the video RAM and 50M-100M for Virtualbox to manage the VM when running.  It is important to leave CPU and RAM for the hostOS too.

Take a look at LXC, which has much lower resource requirements, but it is limited to Linux-only containers.

---

