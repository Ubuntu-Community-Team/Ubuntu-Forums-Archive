---
title: "sysctl tuning: how to limit vm caching?"
date: 2011-09-16
forum: Server Platforms
---

### Post by mike.emery on 2011-09-16
Bit of a newbie here and could use a hand: how do I limit the ram available for pagecache, dentries and inodes? I think I want vm.bdflush and/or vm.kswapd in sysctl, but the explanations I'm finding online are a bit confusing. What I'm looking to do is prevent these caches from taking more than 4g or so (out of 24g total available).

---

### Post by mike.emery on 2011-09-19
Editing with updates.

So far I've limited vm.dirty_background_ratio and vm.dirty_ratio to 5 and 10% and this helps somewhat, but these setting have no effect on the amount of memory allocated for clean caches.

---

### Post by jchung on 2011-09-19
> **mike.emery said:**
> Editing with updates.

So far I've limited vm.dirty_background_ratio and vm.dirty_ratio to 5 and 10% and this helps somewhat, but these setting have no effect on the amount of memory allocated for clean caches.

Try this article

[http://www.enterprisenetworkingplanet.com/netsysm/article.php/3741281/Understand-Linux-Virtual-Memory-Management.htm](http://www.enterprisenetworkingplanet.com/netsysm/article.php/3741281/Understand-Linux-Virtual-Memory-Management.htm)

---

### Post by mike.emery on 2011-09-19
> **jchung said:**
> Try this article

[http://www.enterprisenetworkingplanet.com/netsysm/article.php/3741281/Understand-Linux-Virtual-Memory-Management.htm](http://www.enterprisenetworkingplanet.com/netsysm/article.php/3741281/Understand-Linux-Virtual-Memory-Management.htm)

Thanks! This describes exactly what I want, but I do not see any of the settings mentioned when I do sysctl -A. Specifically: vm.pagecache and vm.bdflush. I also do not see these in /proc/sys/vm.

For reference I'm running 10.04.3 LTS

---

### Post by ZorkMaster on 2011-09-22
> **mike.emery said:**
> Thanks! This describes exactly what I want, but I do not see any of the settings mentioned when I do sysctl -A. Specifically: vm.pagecache and vm.bdflush. I also do not see these in /proc/sys/vm.

For reference I'm running 10.04.3 LTS

For Linux kernel version 2.6.38, [http://www.mjmwired.net/kernel/Documentation/sysctl/vm.txt](http://www.mjmwired.net/kernel/Documentation/sysctl/vm.txt) doesn't list *vm.pagecache* or *vm.bdflush* as valid parameters.  Don't know what happened to them or why they were removed.

Try reading the descriptions on the other params; maybe *vm.min_free_kbytes* or *vm.vfs_cache_pressure* can help you out?

---

