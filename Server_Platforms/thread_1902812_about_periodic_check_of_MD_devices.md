---
title: "about periodic check of MD devices"
date: 2011-12-31
forum: Server Platforms
---

### Post by yavuz.maslak on 2011-12-31
I use ubuntu11.10 64 bit. it works as raid1 softraid.
it works well. But I am aware of a thing that there is a crontab related to mdadm. That runs a schdule which checks periodic redundancy checks of MD devices at first sunday of a month.

my server runs under heavy load
if I close that cron could that be any problem ? 

How can I close that cron?

Thanks

---

### Post by Xianath on 2012-01-01
If I were you, I wouldn't remove it. The default setting for sync_speed_min is 1000, meaning that when there's other load, it will only add up 1MB/sec of I/O (granted, with some more random seeks thrown in, but nothing proper readahead tuning can't take care of). On the other hand, this job is quite useful in reporting data inconsistencies. Those can occur during power failure, system crashes, hardware errors (controller, bus or cable problems) or -- and that's pretty much guaranteed -- just normal drive use. See [this article]("http://lefthandnetworks.typepad.com/virtual_view/2008/02/what-does-data.html") for a more in-depth explanation of bit error rate.

In short, that cron job is useful (provided you monitor the results) and shouldn't affect server performance.

---

