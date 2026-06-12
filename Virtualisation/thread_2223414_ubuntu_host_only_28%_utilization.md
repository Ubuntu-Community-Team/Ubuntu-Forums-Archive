---
title: "ubuntu host only 28% utilization"
date: 2014-05-10
forum: Virtualisation
---

### Post by PhilTroy on 2014-05-10
I am running lubutu 14,04 as host and windows 7 as client on an 7 mobile procssor dual core with hyperthreading.  Windows task manager shows 100% but lubuntu orly shows 28% processor utilization when running a multithreaded application on windows (simul 8) with all processors and memory allocated to guest.  I would like the guest to have all resources possible so that simul 8 runs faster.

I have two questions

- Are There any settings i can use to get my windows app to run faste?

- would xen be better e than kvm?

Thanks

Phil

---

### Post by TheFu on 2014-05-12
Exactly what hardware does the host have?  CPU model, RAM, disk subsystem?
Which settings were selected for the VM?  RAM, number of cores, video, disk controller type and amount of storage allocated?  How did you allocated the vHDD for the VM? THIS matters tremendously. Don't use sparse allocations. Fully pre-allocated all storage as raw, unless you are allocating an entire partition using LVM as passthru to the guest. QCOW is slow, except on SSDs.

It seems like the settings are poorly selected, lacking any other data.

It is bad to give a guestOS too many resources, but it is equally bad to limit resources too much. Plus, if enough resources are not reserved for the hostOS, well, that matters too.

---

### Post by Doug S on 2014-05-12
I gave a VM 4 CPU's, and fully loaded them down. It is a dekstop VM and so also has a lot more overhead than a server:```
doug@doug-desktop:~$ uptime
 07:52:22 up 23 min,  5 users,  load average: [COLOR=#ff0000]4.68[/COLOR], 4.87, 3.67
```And on the host 14.04 server I get:```
doug@s15:~/temp$ uptime
 07:53:40 up 28 min,  2 users,  load average: [COLOR=#ff0000]4.33[/COLOR], 4.21, 3.40
```In otherwords, I get exactly what I expect.

---

### Post by TheFu on 2014-05-12
I don't give desktops more than 1 vCPU or 2G of RAM.  Windows will expand to use all resources available.

Also - leaving the hostOS with 1 unused core and 1G of RAM is important. It needs those resources to manage clientOS stuff.  These are rough estimates - different hosts and different clientOSes can be tweaked to use less resources.

---

