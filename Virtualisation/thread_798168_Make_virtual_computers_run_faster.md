---
title: "Make virtual computers run faster"
date: 2008-05-17
forum: Virtualisation
---

### Post by Nampla on 2008-05-17
Any tips out there to make virtual pc's run faster?  We have vmware server 1.05 on Ubuntu and our virtual pc's are win 2000 and win xp.

---

### Post by bradmkjr on 2008-05-19
Any of the 100's of list of tips out there on speeding up XP will help:

[http://www.connectedinternet.co.uk/2005/12/03/10-simple-ways-to-speed-up-windows-xp/](http://www.connectedinternet.co.uk/2005/12/03/10-simple-ways-to-speed-up-windows-xp/)
[http://reviews.cnet.com/4520-10165_7-5554402-1.html](http://reviews.cnet.com/4520-10165_7-5554402-1.html)
[http://www.crn.com/white-box/59201471](http://www.crn.com/white-box/59201471)

But specifically for Virtual Machines, here are 3 tips:

1. Consider RAID, there are different styles of raid, but a true hardware Sata raid will allow for faster data access
2. Use full partitions instead of Virtual Disk Images, this should theoretically be a huge improvement in speed, since there is 1 less level of abstraction between the hardware and virtual machine. You could even share data partitions between virtual machines.
3. Increase the ram on the Virtual Server, there for increasing the ram on the virtual machines.

Hope this gives you some ideas,

Bradford Knowlton
[http://x86Virtualization.com/](http://x86Virtualization.com/)

---

