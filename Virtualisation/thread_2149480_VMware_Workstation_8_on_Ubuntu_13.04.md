---
title: "VMware Workstation 8 on Ubuntu 13.04"
date: 2013-05-28
forum: Virtualisation
---

### Post by JaySeeJC on 2013-05-28
I know it's not really all that supported, but is it possible to get workstation 8 to compile against the 3.8 kernel?
Using this patch ([http://weltall.heliohost.org/wordpress/2012/04/01/vmware-workstation-8-0-2player-4-0-2-and-7-1-x3-1-x-fix-for-linux-kernel-3-4-0/](http://weltall.heliohost.org/wordpress/2012/04/01/vmware-workstation-8-0-2player-4-0-2-and-7-1-x3-1-x-fix-for-linux-kernel-3-4-0/)) i'm able to get all but vmci compiled. I'm aware of open-vm-tools but but they have a weird bug where what looks like a kernel panic overwrites my X screen and the only way to fix it is to swap to console and back again.
Trying to use workstation 8 as I recall getting hardware acceleration for the graphics with it and a bug is preventing me from getting that in 9.

---

### Post by JaySeeJC on 2013-05-28
I seem to have found the answer to my own problem.
[http://communities.vmware.com/message/2234875#2234875](http://communities.vmware.com/message/2234875#2234875)

---

