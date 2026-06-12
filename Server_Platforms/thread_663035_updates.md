---
title: "updates"
date: 2008-01-09
forum: Server Platforms
---

### Post by boondocks on 2008-01-09
We have:
[INDENT]a Ubuntu 6.06 LTS server
a Ubuntu 6.06 LTS desktop
a Ubuntu 7.10 desktop
[/INDENT]
Both the desktops have frequent updates, so we download and apply them.

But on the 6.06 LTS server:
I did "sudo apt-get upgrade" shortly after the installation and there were some updates and we applied those.
So I did "sudo apt-get upgrade" at various times in the last 3 months and there are no updates at all.

All I see is:
[INDENT]Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
[/INDENT]
Is this to be expected?
What is the frequency of updates on the LTS server versions?

---

### Post by boondocks on 2008-01-09
Apparently, first I need to:
  sudo   aptitude   update

Then do:
 sudo   aptitude   upgrade

---

### Post by boondocks on 2008-01-09
The above worked.
A whole bunch of packages got upgraded.

Then I did " sudo   aptitude   upgrade" again:
[INDENT]Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  linux-image-server
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
[/INDENT]
So why was the "linux-image-server" package kept back?

---

### Post by k_grdn on 2008-01-10
Hi,

> So why was the "linux-image-server" package kept back?

Linux-image-server is a kernel update and you may necessarily not want to update your kernel for various reasons, packages relying on older kernel etc...

Try: sudo apt-get install linux-image-server (if you want to upgrade your kernel)

Most prob need a reboot to take effect.

Regards,

k_grdn

---

### Post by boondocks on 2008-01-10
Ahh, ok thanks.

---

