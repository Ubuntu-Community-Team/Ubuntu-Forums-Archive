---
title: "Change VB Partitions"
date: 2016-03-13
forum: Virtualisation
---

### Post by Quarkrad on 2016-03-13
Running 14.04 host and 14.04 guest.  I have three partitions in my guest and would like to make some changes - on my host machine I would do this by booting to a live CD.   However, my partitions are now those on the virtual machine.  Is it possible to effectively boot a Virtualbox (5) guest to a live CD?

---

### Post by MAFoElffen on 2016-03-15
If you are making changes to a VM, mount the LiveCD to that VM. If making chages to a host, then boot from the host CD... You cannot make changes from a guest to a host... the host root disk has to be un-mounted to make changes to it. You cannot run a virt with the root un-mounted.

---

### Post by Quarkrad on 2016-03-15
Thanks - all I want to do is make changes to the guest so I have to mount the CD.  Can you help me how to do that please?   Assuming I have launched the guest and am now at the Desktop - do I fire up the terminal and put in some commands to launch the live CD so I can access GParted to act on the guest partitions?

---

### Post by MAFoElffen on 2016-03-17
When you have the VM Pane open, look at the menu in the VM frame. 

Refer to the screen shot I posted.

Select: Devices > Optical Drive > Choose Disk Image... That will open a menu so that you can manuever and select the ISO image of the LiveCD.

---

### Post by Quarkrad on 2016-03-17
Thank you very much

---

