---
title: "installation on the RAID-1"
date: 2009-02-11
forum: Server Platforms
---

### Post by snedi on 2009-02-11
There was a task to make a reinstall of the ubuntu server on the machine. I had been installed on raid-1 before. Using this [doc]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/") i followed all the steps but i didn't understand this:

> Once the partitions are configured, at the top of the &#8220;Partition Disks&#8221; main dialog select &#8220;Configure Software RAID&#8221;
When asked &#8220;Write the changes to the storage devices and configure RAID&#8221; select &#8220;Yes&#8221;.
For &#8220;Multidisk configuration actions&#8221; select &#8220;Create MD device&#8221;
For &#8220;Multidisk device type&#8221; select &#8220;RAID1&#8243;
For &#8220;Number of active devices for the RAID1 array&#8221; enter &#8220;2&#8243;
For Number of spare devices for the RAID1 array&#8221; enter &#8220;0&#8243; (zero)
When asked to select &#8220;Active devices for the RAID1 multidisk device&#8221; select both /dev/sda1 and /dev/sdb1
From the next dialog select &#8220;create MD device&#8221;
Repeat the above steps to create an MD device that contains /dev/sda2 and /dev/sdb2
Finally, from the dialog &#8220;Mulidisk configuration actions&#8221; select &#8220;Finish&#8221;

after Create MD device, and selecting type of RAID-1 it says that MD devices are alredy there and offered to delete them first. No questions about the number of active and spare devices was asked. I returned to the main partioning menu, there were all that i need, i setup mount points, format options and chose Write changes to disks. Installations continued fine and i see all my md devices ok, all works fine. But i didn't understood why i wasn't asked those steps... Could somebody explain this ?

---

### Post by snedi on 2009-02-11
btw, when i tried to delete md disks with Delete md device in the Software Raid menu - it said they'd been busy.

---

