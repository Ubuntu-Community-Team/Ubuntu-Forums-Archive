---
title: "Fuzzy GUI VM (ubuntu 12.04) on Nutanix (hypervisor) after new installation"
date: 2016-05-19
forum: Virtualisation
---

### Post by poshanchang on 2016-05-19
Fuzzy GUI VM (ubuntu 12.04) on Nutanix (hypervisor) after new installation. What can be wrong? How to fix? Thanks a lot.
[ATTACH=CONFIG]269166[/ATTACH][ATTACH=CONFIG]269167[/ATTACH]

---

### Post by howefield on 2016-05-19
Thread moved to the "*Virtualisation*" forum.

---

### Post by user1397 on 2016-05-20
Question, why are you trying 12.04?  Why not 16.04 or 14.04? 12.04 is quite dated (yes I know the EOL is next year for it but still, if you're just trying it out in a VM I don't get why you're using that version.)

---

### Post by KillerKelvUK on 2016-05-20
+1 on user1397's response.

Also as Nutanix offers different hypervisor options please can you confirm the hypervisor used and the versions as well as your guest vm configurations?

---

### Post by MAFoElffen on 2016-05-22
> **KillerKelvUK said:**
> +1 on user1397's response.

Also as Nutanix offers different hypervisor options please can you confirm the hypervisor used and the versions as well as your guest vm configurations?
I haven't used Nutanix (specifically), but understand that it uses nodes in a distributed computing cluster. (Multiple servers running hypervisors and a shared filesystem.) I also know it is a "new" startup.

So:
- How many servers in the computing cluster?
- What was the load on the servers while trying to run this Guest?
- Was the hypervisor remote to the machine displaying the VM Guest? Or was this on the same machine?
- In defining your VM Guest:
 -- How much memory did you allocate to the VM?
 -- What was the video setting for the VM Guest?
 -- Are you displaying the VM guest via VNC or SPICE?

Why did I ask those two questions? Because if this were "on metal" displaying as you posted, it looks to me that it was running out of resources (low memory, too much of a load)... Having no idea of the environment you have this on... Maybe you could paint us a picture of the details and particulars(?)

---

