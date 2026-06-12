---
title: "Help installing Ubuntu on virtual box"
date: 2017-12-22
forum: Virtualisation
---

### Post by bjerget on 2017-12-22
I get the following error when I try to install Ubuntu on my virtual box on my Win 8 pc.

[img]https://preview.ibb.co/cF6c0R/ubuntu.png[/img]

---

### Post by deadflowr on 2017-12-22
*Thread moved to **Virtualization***

Is the host (Windows 8) a 32-bit version or a 64-bit version?
Ubuntu iso seems to be a 64-bit version (x86_64 means 64-bit) and the host seems to be 32-bit (i686 means 32-bit)

It might also be that the machine is not properly set with vt-x enabled.

Post back basics specs about the system and machine.

---

### Post by bjerget on 2017-12-22
Thank you for your reply. Here are my system specs.

[img]https://image.ibb.co/mWhjfR/specs.png[/img]

---

### Post by TheFu on 2017-12-23
It appears that the virtual hardware created for the installation picked 32-bit CPU.  Just change that to a 64-bit CPU and all should be good for an install, assuming VT-x (or whatever AMD calls it) is enabled in the BIOS.  I think 64-bit installations require hardware support for virtualization - VT-x or "virtualization extensions" is how I've seen this in the physical BIOS on most machines.  

Some low-end laptops do not have this setting, so running a 64-bit guest isn't possible.

---

### Post by bjerget on 2017-12-27
Hi again and happy holidays!

I was able to enable SVM on my laptop's bios, but I got the same error. I'm using a lenovo g505 running windows 8.

---

### Post by bjerget on 2017-12-27
Got it sorted. Was accidentally choosing to run the 32 bit version instead of the 64 bit version in virtualbox settings. Thanks for your help.

---

### Post by TheFu on 2017-12-28
We all make this sort of mistake from time to time.

If this is solved, please mark the thread as [solved] using the thread tools to help others in the community.

---

### Post by bjerget on 2018-01-01
Marked as solved. Thanks very much. I'm really loving my Ubuntu, but I wish I had given the partition more than 10gb of space! I blew through that in no time at all :D

---

### Post by TheFu on 2018-01-01
vboxmanage has an option to copy a vdi into a new one.  The new one can be larger.
or ... [https://www.howtogeek.com/124622/how-to-enlarge-a-virtual-machines-disk-in-virtualbox-or-vmware/](https://www.howtogeek.com/124622/how-to-enlarge-a-virtual-machines-disk-in-virtualbox-or-vmware/) is probably still valid.

---

