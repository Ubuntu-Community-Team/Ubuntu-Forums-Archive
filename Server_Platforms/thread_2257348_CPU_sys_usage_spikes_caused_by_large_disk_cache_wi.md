---
title: "CPU sys usage spikes caused by large disk cache with large memory"
date: 2014-12-19
forum: Server Platforms
---

### Post by RuralHunter on 2014-12-19
I have a dedicated database(PostgreSQL 9.2) server Ubuntu 12.04.4 LTS(3.5.0-22-generic #34~precise1-Ubuntu SMP Wed Jan 9 21:45:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux). The server has 384G memory and PostgreSQL is configured with 16G shared buffer(memory usage). So the most part of the memory is used as OS disk cache. Recently we saw intermittent cpu spikes when the free memroy is lower than 2G. When the problem happens all the cpu is used by sys part and the OS is frozen. The vmstat output is like this:
```
$ vmstat 3
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 4  5 680472 2074224 295012 380294752    0    0   199   512    0    0 12  4 75  9
 7  5 680472 1924056 295032 380449056    0    0 39305 33933 33483 34959 18  4 67 11
10  6 680472 1855644 295044 380503616    0    0  7228 13869 21690 35089 19  6 67  7
 4  4 680472 1803304 295092 380556672    0    0  6477 15863 23531 42315 18  6 68  8
 4  9 680472 1752896 295112 380604992    0    0  5103 12924 16811 21739 14  3 75  8
 4  4 680472 1746984 295124 380597120    0    0  3189 20839 22414 27391 14  4 71 11
 4  7 680472 1685020 295152 380638944    0    0  7087 36879 17662 14530 12  2 71 15
 9  7 680472 1574856 295184 380743168    0    0 25392 29203 22883 18270 10  2 72 16
=====================Problem starts============================
178  9 680472 1470920 295132 380814528    0    0 56065  8611 30298 14814  4 73 19  4
71 20 680480 1582584 294928 380700000    0    3 17880 23216 24921 10169  8 91  1  1
144 13 680480 1489360 294896 380758400    0    0 31561 24060 28925 15912  7 87  2  3
161  7 680480 1458964 294876 380770400    0    0 23831 17684 24333 11135  8 87  2  3
51  5 680492 1499344 294808 380769472    0    4 20449 19509 22953 11342  8 86  2  3
124  9 680500 1576180 294792 380694848    0    3  7225 22391 25009 8749  7 89  2  1
130  7 680500 1684820 294736 380576192    0    0   703  4209 12469 1874  2 98  0  0
137 21 680520 1668448 294600 380503328    0    7  5003 26919 26833 20787 10 80  6  4
136 12 680520 1648328 294608 380507168    0    0   143   363 10696 1613  3 97  0  0
60  8 680520 1577896 294532 380601312    0    0 47453 15459 26177 16708  7 82  7  3
10 13 680532 1581176 294348 380631776    0    4 40689 14884 30857 42377 11 69 16  5
16  7 680532 1281988 294380 380955520    0    0 94193 31415 42036 67945 24 10 51 15
159  8 680532 1255836 294344 380988576    0    0 45329  8556 30689 16089  5 85  8  3
175  5 680536 1239100 294284 380938688    0    1  6957  9767 20449 7958  7 92  0  0
60  2 680568 1292944 294260 380867200    0   11   907 13671 12820 5324  3 89  6  2
106  5 680628 1258592 294244 380862848   11   21 13797  1133 20167 9454 15 84  1  0
137  3 680636 1300352 294236 380814464    0    3 19256  6125 28278 19983 13 86  1  1
183 15 680644 1313472 294244 380783072    0    3   424   135 12316 3199  7 93  0  0
155  1 680644 1334764 294248 380740096    0    0  8737  1136 19467 5785  5 95  0  0
98  3 680644 1299516 294244 380766080    0    0  6292  2631 16652 5855  8 91  1  0
192 17 680644 1342412 294144 380744448    0    0  3189   580 20156 8071  8 91  1  0
191  8 680644 1370752 294156 380780160    0    0 26052  2741 26198 19001 11 85  3  0
118  2 680644 1316504 294164 380819072    0    0 18467  3349 18454 6443  7 92  0  0
176  6 680696 1439148 293952 380682304    0   17  4733  2119 16110 3079  2 98  0  0
117  3 680696 1433872 293888 380667616    0    0   421  1597 14758 5292  4 95  1  0
118  9 680700 1417508 293900 380668960    0    1  1313  1089 14601 4458  4 96  0  0
176  5 680700 1434004 293884 380645792    0    0  1459  1623 10459 1036  3 97  0  0
116  3 680740 1443220 293808 380621408    0   13 12251  1557 20832 8149  6 93  1  0
98 10 680740 1417768 293848 380654336    0    0  4688   345 12879 4453  5 94  1  0
164 10 680740 1407976 293804 380642304    0    0  3383   757 17480 4234  8 92  0  0
```

I also noticed there are some memory allocation errors in syslog from different processes:
Dec 17 12:18:52 dbserver kernel: [5783823.189821] postgres: page allocation failure: order:5, mode:0x4020
Dec 17 12:18:52 dbserver kernel: [5783823.189827] Pid: 14141, comm: postgres Tainted: G W O 3.5.0-22-generic #34~precise1-Ubuntu
Dec 17 12:18:52 dbserver kernel: [5783823.189828] Call Trace:
Dec 17 12:18:52 dbserver kernel: [5783823.189830] <IRQ> [<ffffffff8112d206>] warn_alloc_failed+0xf6/0x150
Dec 17 12:18:52 dbserver kernel: [5783823.189847] [<ffffffff8108a2ee>] ? try_to_wake_up+0x18e/0x200
Dec 17 12:18:52 dbserver kernel: [5783823.189850] [<ffffffff8113104b>] __alloc_pages_nodemask+0x6db/0x930
Dec 17 12:18:52 dbserver kernel: [5783823.189854] [<ffffffff816897b2>] kmalloc_large_node+0x57/0x85
Dec 17 12:18:52 dbserver kernel: [5783823.189858] [<ffffffff81176745>] __kmalloc_node_track_caller+0x1a5/0x1f0
Dec 17 12:18:52 dbserver kernel: [5783823.189863] [<ffffffff814144f1>] ? add_interrupt_randomness+0x41/0x190
Dec 17 12:18:52 dbserver kernel: [5783823.189867] [<ffffffff81574d5b>] ? __alloc_skb+0x4b/0x230
Dec 17 12:18:52 dbserver kernel: [5783823.189869] [<ffffffff815750b5>] ? skb_copy+0x45/0xb0
Dec 17 12:18:52 dbserver kernel: [5783823.189871] [<ffffffff81574d88>] __alloc_skb+0x78/0x230
Dec 17 12:18:52 dbserver kernel: [5783823.189874] [<ffffffff815750b5>] skb_copy+0x45/0xb0

 I increased vm.min_free_kbytes and seems it fixed the memory allocation problem. But the cpu spike still happens. I read an article([http://www.pythian.com/blog/performance](http://www.pythian.com/blog/performance)-tuning-hugepages-in-linux/) and it claims large memory page table could cause the similar problem. So I suspected the problem is caused by this when OS is busying scaning page table for free memory when almost all the memory is used by disk cache. So I cleared the disk cache to free up the memory and found it did the trick.

 So is this a bug with Ubuntu memory management? It should free some memory from disk cache when the memory is short or it takes too long to find free memory. I noticed there is a vm parameter(vm.pagecache) to control the memory usage of disk cache on redhat(https://[access.redhat.com/documentation/en]("http://access.redhat.com/documentation/en")-US/Red_Hat_Enterprise_Linux/5/html/Tuning_and_Optimizing_Red_Hat_Enterprise_Linux_for_Oracle_9i_and_10g_Databases/sect-Oracle_9i_and_10g_Tuning_Guide-Memory_Usage_and_Page_Cache-Tuning_the_Page_Cache.html). But I can not find this with Ubuntu. So for now I created a workaround script to clear disk cache when free memory is below 10G. Is there any permanent solution for this problem?

---

### Post by RuralHunter on 2014-12-23
anybody?

---

