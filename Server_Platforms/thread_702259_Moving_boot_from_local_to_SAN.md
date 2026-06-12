---
title: "Moving /boot from local to SAN?"
date: 2008-02-20
forum: Server Platforms
---

### Post by justleen on 2008-02-20
So, i have a Blade somewhere in our datacentre.
The blade comes with two internal disks in a RAID1 configuration. The OS (a default image from our sofware engineers) is installed through altiris on the local disks. 

After everything is up and running, I get a SAN disk allocated by the storage guys. 

Now here is the thing: the SAN disk are backed up, the local disks are not (we dont want to backup over LAN, only over fibre).
Now its already pretty failsafe being a RAID1 config, but i'd like to have more security, by moving everything to the SAN disk, so its on a RAID5 AND is backed up.


how would i go about moving my /boot to the SAN disk? (the rest of the partition are  pretty straight forward, i think)

can i create a 100MB boot part on the san, copy /boot to it, and add an entry in the menu.lst?

---

