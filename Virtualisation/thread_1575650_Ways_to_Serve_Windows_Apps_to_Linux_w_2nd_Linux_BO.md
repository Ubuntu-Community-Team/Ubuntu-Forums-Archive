---
title: "Ways to Serve Windows Apps to Linux w/ 2nd Linux BOX"
date: 2010-09-16
forum: Virtualisation
---

### Post by Majgeek on 2010-09-16
Okay I know it is possible using something like VMWare Server running as a service to serve Windows apps to the Linux host.    (I believe this is possible with Virtual Box as well)

What I am looking for is a way to use a second computer running Linux as host and a virtual machine to serve windows apps to my primary Linux box over the network. (e.g. Like Citrix does) Perhaps this is covered here somewhere already, but I did not know the terminology to use.  I remember reading something about doing this before I think. 

I have run both Virtual box and VMware.  Currently I am using VMware Player with Win XP pro, & Win 7 to run apps i need and do software testing.  With VMware I have been experiencing a lot of times when my host "freezes" momentarily (i.e. the turns gray) even though the VM is running very light and experienced no slow down at all.

What I am looking for is a speed increase, as well as a better seamless integration if possible.  

Thanks

System Specs
Ubuntu 10.04 
4GB RAM
AMD Phenom (9850) Quad Core

---

### Post by TheFu on 2010-09-17
For XP-Pro, why not just enable "Remote Desktop" connections inside the VM OS, then you can RDP into the WinXP machine with rdesktop from any Linux machine.  With Win7, you didn't say whether it was pro, home or something else - if you have Win7 Pro or above, enable "Remote Desktop", but you need to allow the older version of RDP - Windows will say this is a security risk, but inside a LAN, I wouldn't worry.  This stuff has nothing to do with virtualization, BTW.

---

