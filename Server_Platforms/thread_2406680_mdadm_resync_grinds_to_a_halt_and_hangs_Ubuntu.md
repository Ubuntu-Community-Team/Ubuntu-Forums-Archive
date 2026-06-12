---
title: "mdadm resync grinds to a halt and hangs Ubuntu"
date: 2018-11-24
forum: Server Platforms
---

### Post by garfield-arbuckle on 2018-11-24
Hey Everyone,
I have 5 times 4TB drives in a RAID5 array on Ubuntu 16.04 using mdadm. Everything has been working fine for several years however since a couple of weeks now my mdadm array has been resyncing. At first the resync goes at a proper speed with a predicted completion time of about 12 to 14 hours.
However when coming to around 80% everything starts slowing down to about 400K/sec. After waiting a couple hours more the system finally hangs (no ssh connectivity anymore) and a reboot is necessary. The resync starts all over again and hangs again around the 80% marker.
Any ideas on how to troubleshoot this?
I've tried cancelling the resync but both:

[COLOR=#242729][FONT=Consolas]/usr/share/mdadm/checkarray -x --all
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]and
[/FONT][/COLOR][COLOR=#242729][FONT=Consolas]echo idle > /sys/block/md0/md/sync_action[/FONT][/COLOR]

don't work. I've now set the max and min speed limit to 0 and that has halted the resync however this is hardly a solution.
Any help would be much appreciated.
Thanks

---

