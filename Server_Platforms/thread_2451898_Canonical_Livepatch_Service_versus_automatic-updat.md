---
title: "Canonical Livepatch Service versus automatic-updates cron job"
date: 2020-10-12
forum: Server Platforms
---

### Post by avasudevan on 2020-10-12
We enrolled for Canonical Livepatch Service. Earlier we wrote shell scripts in automatic-updates and ran these scripts daily 6am. 
The scripts are **sudo apt update && sudo apt upgrade -y**. we also followed instruction as described in here -> _[https://libre-software.net/ubuntu-automatic-updates/](https://libre-software.net/ubuntu-automatic-updates/)_

What additional benefit do we get by enrolling for _Canonical Livepatch Service_ versus _cronjob - following the instructions_ as described in the link ?

Many thanks.

---

### Post by TheFu on 2020-10-12
I think automatic patching is a mistake for any production system. I've had patches break production syytems multiple times. Blindly accepting patches will eventually fail.  If you insist, please make snapshots with LVM or ZFS before patching and have a way to deleted those snapshots before all the storage runs out.

TANSTAFL.

---

### Post by ameinild on 2020-10-13
Livepatching and "unattended upgrades" are two different things.

[LIST=1]
[*]Unattended upgrades (or upgrade script) are just regular updates run at specific intervals. Kernel or microcode updates will still require a reboot to be applied 
[*]Canonical Livepatch is a special service that patches "high" and "critical" kernel vulnerabilities while the system is running, and thus reboot is not required. 
[/LIST]
Be aware that only a limited number of kernel vulnerabilities can and will be livepatched. For 20.04 I've only experienced 1 or 2 livepatches, while the remaining kernel updates have been regular updates that required a reboot. But livepatching makes sure that the most critical vulnerabilities are patched asap, and the other kernel updates can be applied when a reboot is possible.

---

### Post by 14kaitou on 2020-10-13
if using zfs or btrfs your safe to update the kernel etc, live update are essential, it is important to make sure ubuntu are livepatch and update be sure to update asap

Best regards

---

### Post by avasudevan on 2020-10-13
In production, we cannot afford to have a server restart. We understand Canonical Livepatch does the most critical kernel update patches but other kernel updates patches come into effect only when the server is restarted. What is most feasible option to avoid restart but still have a healthy kernel? Thanks.

---

### Post by TheFu on 2020-10-13
> **avasudevan said:**
> In production, we cannot afford to have a server restart. We understand Canonical Livepatch does the most critical kernel update patches but other kernel updates patches come into effect only when the server is restarted. What is most feasible option to avoid restart but still have a healthy kernel? Thanks.

Schedule weekly maintenance and reboot then. Setup multiple servers, perhaps with sticky affinity, so clients get directed to one begining 1.5x the average session time.  If you have a "follow the sun" service, you'll want 4+ of these setups.  

Attempting to get over 98% availability out of a single server setup is a fools errand.  There are availability questionnaires which make that pretty clear.  I think a "server" with redundant disks, redundant networking, redundant PSUs, and all addon cards placed internally onto different redundant buses can only guarantee 95% uptime.  That leaves something like 400+ hours a year of downtime.  
Sure, we all do better than that, but there's luck and reality.  I worked as a systems architect for services that can never be offline, ever, for over a decade.  We always had N+2 setups in each location.  If the service had 50 front end servers, we'd deploy 52.  If there are only 3 DB servers, we'd deploy 5 with the extra 2 in slave mode to keep up with transactions. Those 2 would replicate their data to different regions of the world, so if power or internet failed, we could still continue with just a minute or so of lost data.  These servers were placed into class-5 data centers with power fed from 3 different electric substations. The buildings were designed to take anything mother nature could throw.  There were battery banks, diesel electric power generators (like a multiple train engines) and gas turbine power generation on-sight should long term locally generated power be required.  All this testing begins with something as simple as yanking an ethernet cable out or pulling the power cable out. What happens, automatically?  If I did my job, the system barely notices and operations gets an alert, 4 pagers go off to the on-call numbers for  application support, DB support, the application manager/owner, and the local administrator.  Most importantly, I do not get any calls because the system worked as designed. That is key.  I had a job where I was 24/7/364 support. I wasn't allowed to leave the local town.  Once I went to the beach for a long lunch - about 45 min away - and my pager started going crazy by the application owner. It wasn't any emergency or my job he wanted help concerning. Never again.  6 months later, I moved to a different job in a different state.

These data centers were #1 on the govt list of critical locations to get refueled, just after regional trauma centers. We failed our servers over between different DCs every other week, then failed them back 2 weeks later.  If an entire DC was taken out for any reason, the IPs and all subnet for it could be switched to another DC that had servers to be taken over in a few hours.  Critical, national, infrastructure. We didn't mess around.
  All the storage was the most expensive, full-featured, redundant SAN equipment available.  These services could never go down, but each system had scheduled maintenance so we could do those things required to meed the 5-9s availability mandate.

Wishes are not a plan.  For truly 5-9s available services, a plan is required. It needs to be funded, implemented, tested and best if it is actually part of the normal systems testing every few weeks.  It's like backups, until we restore, we don't actually know whether our backups are any good. Same for availability. Any failover plans must be tested.

---

### Post by kevdog on 2020-10-14
Do you need a High Availability setup?  Clustering?

---

### Post by LHammonds on 2020-10-14
> **avasudevan said:**
> In production, we cannot afford to have a server restart. We understand Canonical Livepatch does the most critical kernel update patches but other kernel updates patches come into effect only when the server is restarted. What is most feasible option to avoid restart but still have a healthy kernel? Thanks.
If that truly is the case, then you should be running a high-availability farm...which means you can reboot whenever you need.

If you only have 1 server, then the system was not designed with the "cannot afford to have a server restart" goal.

**EDIT:** I do not know your setup but using redundant servers and load balancers can help you achieve the "always online" goal by letting you take servers offline at any level and the entire system still work.

Examples:
[Load balancer for a web server]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=260")
[Load balancer for a database cluster]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=264")
[MariaDB Galera cluster]("https://hammondslegacy.com/forum/viewtopic.php?f=40&t=262")

LHammonds

---

