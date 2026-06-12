---
title: "Ubuntu Sever 10.04 getting attacked?? Help please."
date: 2011-10-08
forum: Server Platforms
---

### Post by ioasw on 2011-10-08
I'm on Ubuntu Server 10.04 with all the latest updates installed.  I have Google Analytics running on the site, and I believe it's being attacked somehow because it keeps running out of memory.  I'm getting the error:  out of memory: Kill process 2789.

The site I'm running is definitely memory intensive, but I have 2GB installed on the virtual machine I'm running on, and google analytics only reports 80 visits!  So I know it's not the site I'm running, it has to be an attack.  I've viewed the systems logs and found a couple ips that looked like they where doing the attacking so I blocked them using 

```
iptables -A INPUT -s i.p.a.d -j DROP
```

I replaced i.p.a.d with the actual ips of course.  I'm running ehcp, and I have webmin installed.  What can I look for?  There is something taking all my memory away, and I have tons of it, I've only ever seen it get to maybe 800mb of used memory, so it can't be my site.  

Any help would be greatly appreciated.  I just need to know what to look for.

Here is a piece of my syslog, it just repeats itself over and over again like this:

```
Oct  8 03:04:19 localhost kernel: [65942.534067] Total swap = 1340408kB
Oct  8 03:04:19 localhost kernel: [65942.540015] 524288 pages RAM
Oct  8 03:04:19 localhost kernel: [65942.540015] 11923 pages reserved
Oct  8 03:04:19 localhost kernel: [65942.540015] 75370 pages shared
Oct  8 03:04:19 localhost kernel: [65942.540015] 505792 pages non-shared
Oct  8 03:04:19 localhost kernel: [65942.540015] Out of memory: kill process 4944 (apache2) score 261991 or a child
Oct  8 03:04:19 localhost kernel: [65942.540015] Killed process 22575 (apache2)
Oct  8 03:04:52 localhost kernel: [65976.362232] mysqld invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
Oct  8 03:04:52 localhost kernel: [65976.362241] mysqld cpuset=/ mems_allowed=0
Oct  8 03:04:52 localhost kernel: [65976.362246] Pid: 22665, comm: mysqld Not tainted 2.6.32-34-server #77-Ubuntu
Oct  8 03:04:52 localhost kernel: [65976.362250] Call Trace:
Oct  8 03:04:52 localhost kernel: [65976.362263]  [<ffffffff810b4b2d>] ? cpuset_print_task_mems_allowed+0x9d/0xb0
Oct  8 03:04:52 localhost kernel: [65976.362271]  [<ffffffff810f8fe4>] oom_kill_process+0xd4/0x2f0
Oct  8 03:04:52 localhost kernel: [65976.362277]  [<ffffffff810f95a0>] ? select_bad_process+0xd0/0x110
Oct  8 03:04:52 localhost kernel: [65976.362282]  [<ffffffff810f9638>] __out_of_memory+0x58/0xc0
Oct  8 03:04:52 localhost kernel: [65976.362287]  [<ffffffff810f97ce>] out_of_memory+0x12e/0x1a0
Oct  8 03:04:52 localhost kernel: [65976.362294]  [<ffffffff8155b0ce>] ? _spin_lock+0xe/0x20
Oct  8 03:04:52 localhost kernel: [65976.362300]  [<ffffffff810fc931>] __alloc_pages_slowpath+0x571/0x590
Oct  8 03:04:52 localhost kernel: [65976.362305]  [<ffffffff810fcac9>] __alloc_pages_nodemask+0x179/0x180
Oct  8 03:04:52 localhost kernel: [65976.362312]  [<ffffffff8112fbb7>] alloc_pages_current+0x87/0xd0
Oct  8 03:04:52 localhost kernel: [65976.362318]  [<ffffffff810f67a7>] __page_cache_alloc+0x67/0x70
Oct  8 03:04:52 localhost kernel: [65976.362323]  [<ffffffff810f7e33>] filemap_fault+0x1b3/0x450
Oct  8 03:04:52 localhost kernel: [65976.362329]  [<ffffffff81114964>] __do_fault+0x54/0x500
Oct  8 03:04:52 localhost kernel: [65976.362335]  [<ffffffff81117f18>] handle_mm_fault+0x1a8/0x3c0
Oct  8 03:04:52 localhost kernel: [65976.362342]  [<ffffffff8100f382>] ? check_events+0x12/0x20
Oct  8 03:04:52 localhost kernel: [65976.362347]  [<ffffffff8155dc45>] do_page_fault+0x125/0x3b0
Oct  8 03:04:52 localhost kernel: [65976.362352]  [<ffffffff8155b595>] page_fault+0x25/0x30
Oct  8 03:04:52 localhost kernel: [65976.362356] Mem-Info:
Oct  8 03:04:52 localhost kernel: [65976.362359] Node 0 DMA per-cpu:
Oct  8 03:04:52 localhost kernel: [65976.362364] CPU    0: hi:    0, btch:   1 usd:   0
Oct  8 03:04:52 localhost kernel: [65976.362366] Node 0 DMA32 per-cpu:
Oct  8 03:04:52 localhost kernel: [65976.362371] CPU    0: hi:  186, btch:  31 usd:  28
Oct  8 03:04:52 localhost kernel: [65976.362378] active_anon:342624 inactive_anon:114504 isolated_anon:0
Oct  8 03:04:52 localhost kernel: [65976.362379]  active_file:294 inactive_file:549 isolated_file:0
Oct  8 03:04:52 localhost kernel: [65976.362380]  unevictable:0 dirty:1 writeback:2 unstable:0
Oct  8 03:04:52 localhost kernel: [65976.362381]  free:3488 slab_reclaimable:1527 slab_unreclaimable:6436
Oct  8 03:04:52 localhost kernel: [65976.362383]  mapped:299 shmem:13 pagetables:29176 bounce:0
Oct  8 03:04:52 localhost kernel: [65976.362386] Node 0 DMA free:8056kB min:32kB low:40kB high:48kB active_anon:1240kB inactive_anon:1528kB active_file:24kB inactive_file:80kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:11772kB mlocked:0kB dirty:0kB writeback:0kB mapped:32kB shmem:0kB slab_reclaimable:16kB slab_unreclaimable:160kB kernel_stack:240kB pagetables:556kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:174 all_unreclaimable? no
Oct  8 03:04:52 localhost kernel: [65976.362399] lowmem_reserve[]: 0 2004 2004 2004
Oct  8 03:04:52 localhost kernel: [65976.362408] Node 0 DMA32 free:5896kB min:5708kB low:7132kB high:8560kB active_anon:1369256kB inactive_anon:456488kB active_file:1152kB inactive_file:2116kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:2052320kB mlocked:0kB dirty:4kB writeback:8kB mapped:1164kB shmem:52kB slab_reclaimable:6092kB slab_unreclaimable:25584kB kernel_stack:3848kB pagetables:116148kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:6528 all_unreclaimable? no
Oct  8 03:04:52 localhost kernel: [65976.362421] lowmem_reserve[]: 0 0 0 0
Oct  8 03:04:52 localhost kernel: [65976.362429] Node 0 DMA: 5*4kB 1*8kB 20*16kB 17*32kB 2*64kB 5*128kB 3*256kB 3*512kB 2*1024kB 1*2048kB 0*4096kB = 8060kB
Oct  8 03:04:52 localhost kernel: [65976.362451] Node 0 DMA32: 996*4kB 13*8kB 3*16kB 3*32kB 2*64kB 0*128kB 0*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 5896kB
Oct  8 03:04:52 localhost kernel: [65976.362472] 21272 total pagecache pages
Oct  8 03:04:52 localhost kernel: [65976.362475] 20418 pages in swap cache
Oct  8 03:04:52 localhost kernel: [65976.362479] Swap cache stats: add 3967222, delete 3946804, find 435039/832010
Oct  8 03:04:52 localhost kernel: [65976.362482] Free swap  = 0kB
Oct  8 03:04:52 localhost kernel: [65976.362484] Total swap = 1340408kB
Oct  8 03:04:52 localhost kernel: [65976.370017] 524288 pages RAM
Oct  8 03:04:52 localhost kernel: [65976.370017] 11923 pages reserved
Oct  8 03:04:52 localhost kernel: [65976.370017] 63947 pages shared
Oct  8 03:04:52 localhost kernel: [65976.370017] 505284 pages non-shared
Oct  8 03:04:52 localhost kernel: [65976.370017] Out of memory: kill process 4944 (apache2) score 261929 or a child
Oct  8 03:04:52 localhost kernel: [65976.370017] Killed process 22576 (apache2)
Oct  8 03:06:24 localhost kernel: [66067.713161] apache2 invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0
Oct  8 03:06:25 localhost kernel: [66067.713170] apache2 cpuset=/ mems_allowed=0
Oct  8 03:06:25 localhost kernel: [66067.713175] Pid: 22627, comm: apache2 Not tainted 2.6.32-34-server #77-Ubuntu
Oct  8 03:06:25 localhost kernel: [66067.713179] Call Trace:
Oct  8 03:06:25 localhost kernel: [66067.713192]  [<ffffffff810b4b2d>] ? cpuset_print_task_mems_allowed+0x9d/0xb0
Oct  8 03:06:25 localhost kernel: [66067.713201]  [<ffffffff810f8fe4>] oom_kill_process+0xd4/0x2f0
Oct  8 03:06:25 localhost kernel: [66067.713206]  [<ffffffff810f95a0>] ? select_bad_process+0xd0/0x110
Oct  8 03:06:25 localhost kernel: [66067.713211]  [<ffffffff810f9638>] __out_of_memory+0x58/0xc0
Oct  8 03:06:25 localhost kernel: [66067.713216]  [<ffffffff810f97ce>] out_of_memory+0x12e/0x1a0
Oct  8 03:06:25 localhost kernel: [66067.713223]  [<ffffffff8155b0ce>] ? _spin_lock+0xe/0x20
Oct  8 03:06:25 localhost kernel: [66067.713229]  [<ffffffff810fc931>] __alloc_pages_slowpath+0x571/0x590
Oct  8 03:06:25 localhost kernel: [66067.713236]  [<ffffffff8100f382>] ? check_events+0x12/0x20
Oct  8 03:06:25 localhost kernel: [66067.713241]  [<ffffffff810fcac9>] __alloc_pages_nodemask+0x179/0x180
Oct  8 03:06:25 localhost kernel: [66067.713246]  [<ffffffff8100f36f>] ? xen_restore_fl_direct_end+0x0/0x1
Oct  8 03:06:25 localhost kernel: [66067.713253]  [<ffffffff8112fbb7>] alloc_pages_current+0x87/0xd0
Oct  8 03:06:25 localhost kernel: [66067.713259]  [<ffffffff810f67a7>] __page_cache_alloc+0x67/0x70
Oct  8 03:06:25 localhost kernel: [66067.713264]  [<ffffffff81100359>] __do_page_cache_readahead+0xc9/0x210
Oct  8 03:06:25 localhost kernel: [66067.713269]  [<ffffffff811004c1>] ra_submit+0x21/0x30
Oct  8 03:06:25 localhost kernel: [66067.713274]  [<ffffffff810f807e>] filemap_fault+0x3fe/0x450
Oct  8 03:06:25 localhost kernel: [66067.713280]  [<ffffffff81114964>] __do_fault+0x54/0x500
Oct  8 03:06:25 localhost kernel: [66067.713286]  [<ffffffff81117f18>] handle_mm_fault+0x1a8/0x3c0
Oct  8 03:06:25 localhost kernel: [66067.713293]  [<ffffffff8155dc45>] do_page_fault+0x125/0x3b0
Oct  8 03:06:25 localhost kernel: [66067.713297]  [<ffffffff8155b595>] page_fault+0x25/0x30
Oct  8 03:06:25 localhost kernel: [66067.713301] Mem-Info:
Oct  8 03:06:25 localhost kernel: [66067.713304] Node 0 DMA per-cpu:
Oct  8 03:06:25 localhost kernel: [66067.713309] CPU    0: hi:    0, btch:   1 usd:   0
Oct  8 03:06:25 localhost kernel: [66067.713312] Node 0 DMA32 per-cpu:
Oct  8 03:06:25 localhost kernel: [66067.713316] CPU    0: hi:  186, btch:  31 usd:  30
```

I did a little research and installed libapache2-mod-antiloris on my vps, so lets see if that'll do it.  Still any suggestions would be great.

---

### Post by CharlesA on 2011-10-08
Is apache that one that is eating all the memory?

Do you have some kind of remote access set up such as SSH?

---

### Post by stlsaint on 2011-10-08
For a quick check use netcat (nc) or nmap to do a port scan on your server to view open ports. Open ports that you did not do yourself will be a better indicator if something is happening. Also logs will reveal attacks.

---

### Post by CharlesA on 2011-10-08
> **stlsaint said:**
> For a quick check use netcat (nc) or nmap to do a port scan on your server to view open ports. Open ports that you did not do yourself will be a better indicator if something is happening. Also logs will reveal attacks.
+1 to logs - particularly auth.log.

---

### Post by Dangertux on 2011-10-08
I'm going to go out on a limb here and say this looks a lot like Apache killer, however -- syslog when it comes to apache logging without extra options can be less than intuitive.

I would suggest you check /var/log/apache2/access.log for the following

```

sudo cat /var/log/apache2/access.log | grep "&#8220;HEAD / HTTP/1.1&#8243; 206 353 &#8220;-&#8221; &#8220;-&#8221;"

```

and just to double check our 206 responses :

```

sudo tail -n 500 /var/log/apache2/access.log | awk &#8216;($9 ~ /206/ )&#8217;

```

If you see that it's time to hook up a packet sniffer like wireshark and start filtering by HTTP 1.1 headers filtering for the following

```

Range:bytes=0-,5-0,5-1,5-2,5-3,5-4,5-5,5-6,5-7,5-8,5-9,5-10,5-11

```If you see both of these it's safe to assume you're being attacked by the Apache Killer ranged header request fork issue (CVE-2011-3192)

If that is the case there are a few workarounds already posted on this forum using mod_qos and mod_headers, however the best solution is to upgrade to Apache 2.2.19+ If this is your VPS you can do that under Ubuntu 10.04 by following the procedure [here ]("http://dangertux.wordpress.com/2011/10/05/updating-to-apache-2-2-20-ubuntu-10-04-lts/")

Hope this has been helpful.

---

### Post by ioasw on 2011-10-09
Thanks for all the replies and help everyone I really appreciate it.  I installed libapache2-mod-antiloris almost 24 hours ago, and haven't had a problem since, but I'll check back in another 24 hours with an update.  I'm still weary that something might go wrong.  What exactly is an apache killer, is it an attack?

---

### Post by Dangertux on 2011-10-09
> **ioasw said:**
> Thanks for all the replies and help everyone I really appreciate it.  I installed libapache2-mod-antiloris almost 24 hours ago, and haven't had a problem since, but I'll check back in another 24 hours with an update.  I'm still weary that something might go wrong.  What exactly is an apache killer, is it an attack?


Apache killer is a slowloris style Denial of Service attack. It works by making multiple ranged header requests (50 at a time). Which due to poor coding causes the apache process to fork uncontrollably, thus ending in a resource exhaustion situation.

---

