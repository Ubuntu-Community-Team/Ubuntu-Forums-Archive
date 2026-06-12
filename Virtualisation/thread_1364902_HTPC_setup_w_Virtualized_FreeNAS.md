---
title: "HTPC setup w/ Virtualized FreeNAS"
date: 2009-12-26
forum: Virtualisation
---

### Post by Lepy on 2009-12-26
I am in the process of upgrading a few components in old systems and building a completely new system. I want the new system to be in the bedroom and function as a mythtv and xbmc frontend as well as a FreeNAS w/ ZFS (RAIDZ) that will be accessed by (max) 2 users, so performance is not a huge issue.

The system will run on a new ASRock K10N78 mobo which has 6 sata ports and use an old AMD X2 3800+ which has been a treat in my main mythtv appliance system. I plan on keeping the FreeNAS server on this hardware for atleast a year or two, until I have more space for a proper, larger capacity rackmount server. 

I've never run FreeNAS before, but from my research, running a ubuntu or mythubuntu system with FreeNAS running under Virtualbox should be an acceptable solution, correct? (Will I need a second NIC card, x1 for myth x1 for FreeNAS)?

If so, my main question is about HDD setup. At the moment, I have 3 1TB drives which have no form of redundancy/backup and will eventually approach capacity that I want to transfer to the FreeNAS. I'm planning on buying 3 more 1TB drives (since RAIDZ requires 3 drives), but I was hoping I could only get 2 drives, make a degraded array, copy over one of the old drives data, then place it in the array, and repeat for the remaining drives. Is this possible or should I save myself trouble and go ahead and get the 3rd drive.

Also, If I want to ensure expandability (past the 6 sata drives on the mobo), I should use FreeNAS software raid instead of the mobo's fakeRAID? Will this work with a virtualized FreeNAS?

I hope my HTPC/FreeNAS system is feasible, but if there is a better approach to this dual system which can host all my files + expand using RAIDZ, let me know!

Thanks

---

### Post by kymnyth on 2010-01-20
This is very similar to what I am attempting. I would be very interested in any feedback people can provide.

---

### Post by Lepy on 2010-02-09
To answer my own questions, at the moment it is impossible to expand a zfs RAIDZ without adding another vdev of the same size (to expand a RAIDZ of 3 1TB drives, you would need to create a new vdev out of more 3 1TB = total of 6 1TB drives.

I ended up setting up the FreeNAS by itself and avoiding virtualization all together. From what I've read though, it seems like if you must virtualize, Virtualbox would not be a good option for this setup. It seems using VMware ESX or ESXi to virtualize both FreeNAS and Mythbuntu could work.

I'm very happy with FreeNAS in its own box and using a laptop as a frontend, but I'd be interested to know if anyone has tried a setup using ESXi.

---

### Post by pirateghost on 2010-02-09
i have a virtualized FreeNAS running on ESXi 4.0

with ESXi you do not have direct access to the disks meaning that if you were to have ESXi installed and you want to allocate 3-1tb drives to FreeNAS alone, you must create a VMFS on them and use them as virtual disks.  there is no way around this.

virtualizing storage is complicated and shouldnt be attempted unless you have experience in ESXi/ESX/XEN and have some spare harddrives to test extensively with.  it is way too easy to wipe a drive on accident.

i actually prefer to have my ubuntu server acting as an iscsi target and i allocate all needed drivespace directly to my VM via the ESXi host.  doing it this way allows me to play around with different NAS appliances at will.

---

