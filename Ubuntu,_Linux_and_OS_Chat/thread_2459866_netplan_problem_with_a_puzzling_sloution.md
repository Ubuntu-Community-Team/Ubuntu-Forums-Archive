---
title: "netplan problem with a puzzling sloution"
date: 2021-03-28
forum: Ubuntu, Linux and OS Chat
---

### Post by tienhing on 2021-03-28
Hello everybody, this is not a plea for technical help but I would really love to understand how rebooting can consistently solve an intermittent problem. I'm losing sleep over this. I grappled for weeks with netplan connectivity, as a technical novice following various solutions offered by various experts. In the end, though the problem persists, so does the solution; all I have to do is reboot. My machine is an old Dell Optiplex, with Windows 10/Ubuntu 20.04 dual boot.

---

### Post by TheFu on 2021-03-28
Ideas:
[LIST]
[*]Failing hardware
[*]Bad drivers that don't reinitialize all the registered correctly
[/LIST]

What, exactly do you mean by "reboot"?  It that the same as powering off and on again, after waiting 30+ seconds?
I have 12+ yr old GPU that only works if a fully BRS (Big Red Switch) power-off is used.  A quick reboot doesn't empty the registers, so garbage is left and it won't initialize.  I assume the problem is bad drivers - bad because they don't initialize all memory to known values and wipe all free()'d memory when completed.  Can't say how often I see those poor programming practices assuming a compiler will set everything to zero ... when it doesn't.  How memory gets initialized is usually an "implementation detail" for each compiler/linker.

So in the end, if we have **anything** wrong in the HW or drivers, the results are often random.

I honestly doubt it has anything to do with netplan - especially since you didn't actually post any netplan.yaml file.

---

