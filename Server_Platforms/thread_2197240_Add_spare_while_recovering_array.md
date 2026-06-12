---
title: "Add spare while recovering array?"
date: 2014-01-02
forum: Server Platforms
---

### Post by larzeb on 2014-01-02
I am using Ubuntu 12.04.03. I have a 6-2TB RAID-5 array with a single spare. Recently I noticed that one of the disks was developing bad sectors.

I failed and removed that disk using mdadm. Immediately it used the spare to begin rebuilding the array. I wanted to physically remove the bad drive so I shutdown, removed the drive and put a new one in. When I tried to re-boot, the OS hung at the colored background but did not ask for a log-in.

The disks in the original array are mostly WD Green drives. The new one is also 2TB but a Red. 

Am I supposed to wait for the array to fully rebuild before putting in a new disk?

Thanks

---

### Post by larzeb on 2014-01-03
After the array was rebuilt successfully, I restarted the machine with the new disk and the OS came up normally. 

Maybe you can't add a spare while the array is rebuilding?

---

