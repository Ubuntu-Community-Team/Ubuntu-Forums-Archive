---
title: "server lvm mdadm usage question"
date: 2012-01-04
forum: Server Platforms
---

### Post by SeeThruHead on 2012-01-04
I'm planning a server and would like to clarify some things that will help me make a decision on the filesystem setup.

I think I'm going to be using Ubuntu server, with one HDD for the OS. There will also be 20 2tb HDD attached via linux compatible SAS controller card(s). I would like these twenty drives to show up as one volume. The reason for that is I am going to have multiple share folders on the volume that I cannot predict their storage needs. 

The idea was to have 4 groups of raid 6 with 5 drives each. setup with mdadm.
Then put those 4 volume groups into one large volume with LVM.
My main concern is what happens when a drive fails?
Best case scenario I remove the raid 6 array from the LV, replace the failed drive, rebuild the array with mdadm then add the volume back into the LV, with no data lost. Is this possible? or will I have to redeclare the LV and lose subsequently reformat it losing all the data? Any clarification or direction to where I can read about this kind of scenario would be helpful, google is failing me. Thanks much.

---

