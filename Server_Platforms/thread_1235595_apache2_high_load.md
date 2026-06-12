---
title: "apache2 high load"
date: 2009-08-09
forum: Server Platforms
---

### Post by 2smooth on 2009-08-09
Hi,

My server had been running without any problems for several month. Suddenly since about two months the server gets overloaded and than nobody can connect. It can run for several hours without any problem and than suddenly it starts to overload. Sometimes when i restart apache it runs fine again for a while, but sometimes like today i have to baby sit and restart apache almost every 20 minutes. 

Normally, my server is capable of server a pretty high number of users.

I notice that before the high load starts, it getting very busy with only reading, which is abnormal:

Like this:
```

DSK |         sda | busy     71% | read    1259 | write      8 | avio    5 ms |
DSK |         sdb | busy     70% | read    1233 | write     15 | avio    5 ms |
```




This is the normal situation
```

PRC | sys   0.02s | user   0.24s | #proc    286 | #zombie    0 | #exit      0 |
CPU | sys      1% | user     17% | irq       1% | idle    781% | wait      2% |
cpu | sys      0% | user      3% | irq       0% | idle     97% | cpu002 w  0% |
cpu | sys      0% | user      2% | irq       0% | idle     98% | cpu000 w  1% |
cpu | sys      0% | user      3% | irq       1% | idle     96% | cpu001 w  0% |
cpu | sys      0% | user      3% | irq       0% | idle     97% | cpu004 w  0% |
cpu | sys      0% | user      5% | irq       0% | idle     95% | cpu006 w  1% |
cpu | sys      0% | user      1% | irq       0% | idle     99% | cpu003 w  0% |
cpu | sys      1% | user      1% | irq       0% | idle     98% | cpu007 w  0% |
CPL | avg1   2.96 | avg5    4.47 | avg15   5.18 | csw      663 | intr     215 |
MEM | tot    3.9G | free  346.8M | cache   2.0G | buff    3.9M | slab   40.8M |
SWP | tot    2.1G | free    1.0G |              | vmcom   3.1G | vmlim   4.0G |
PAG | scan      0 | stall      0 |              | swin       4 | swout      0 |
DSK |         sda | busy      2% | read       5 | write      6 | avio    2 ms |
DSK |         sdb | busy      1% | read       3 | write     15 | avio    1 ms |
NET | transport   | tcpi     126 | tcpo     140 | udpi       0 | udpo       0 |
NET | network     | ipi      127 | ipo      143 | ipfrw      0 | deliv    126 |
NET | eth0     0% | pcki     193 | pcko     228 | si  138 Kbps | so  992 Kbps |

  PID  SYSCPU  USRCPU  VGROW  RGROW  RDDSK  WRDSK  ST EXC S  CPU CMD     1/3
 7217   0.00s   0.06s     0K   432K     0K     0K  --   - R   4% apache2
 7191   0.00s   0.05s    88K  3096K     0K     4K  --   - S   3% apache2
 5763   0.00s   0.04s     0K    44K     0K     0K  --   - S   2% mysqld
 7261   0.00s   0.04s   344K  3280K     0K     0K  --   - S   2% apache2
 7375   0.00s   0.02s  1188K  3800K     0K     0K  --   - S   1% apache2
 7407   0.01s   0.01s   132K   132K     0K     0K  --   - R   1% atop
 7320   0.00s   0.01s  -512K   -28K     4K     0K  --   - S   1% apache2
 7270   0.00s   0.01s     0K    88K     0K     0K  --   - S   1% apache2
 7186   0.01s   0.00s     0K     0K     0K     0K  --   - S   1% apache2
 7215   0.00s   0.00s     0K     0K     0K     0K  --   - S   0% apache2
 7250   0.00s   0.00s     0K     4K     0K     0K  --   - S   0% apache2
 7238   0.00s   0.00s     0K     0K     0K     0K  --   - S   0% apache2
 7337   0.00s   0.00s     0K     8K     0K     0K  --   - S   0% apache2
 7369   0.00s   0.00s     0K     0K     0K     4K  --   - S   0% apache2


```

And this is the overloaded situation:

```

PRC | sys  14.00s | user   0.36s | #proc    338 | #zombie    0 | #exit      0 |
CPU | sys    764% | user     20% | irq       1% | idle     11% | wait      3% |
cpu | sys    100% | user      0% | irq       0% | idle      0% | cpu000 w  0% |
cpu | sys     99% | user      1% | irq       0% | idle      0% | cpu001 w  0% |
cpu | sys     97% | user      3% | irq       0% | idle      0% | cpu002 w  0% |
cpu | sys     98% | user      2% | irq       0% | idle      0% | cpu003 w  0% |
cpu | sys     97% | user      2% | irq       1% | idle      0% | cpu005 w  0% |
cpu | sys     90% | user     10% | irq       0% | idle      0% | cpu007 w  1% |
cpu | sys     97% | user      1% | irq       0% | idle      0% | cpu006 w  2% |
cpu | sys     86% | user      2% | irq       1% | idle     11% | cpu004 w  1% |
CPL | avg1   8.22 | avg5    7.09 | avg15   5.62 | csw      260 | intr      76 |
MEM | tot    3.9G | free   50.4M | cache   1.7G | buff    0.5M | slab   43.7M |
SWP | tot    2.1G | free  995.1M |              | vmcom   3.8G | vmlim   4.0G |
PAG | scan  61632 | stall      0 |              | swin       0 | swout      0 |
DSK |         sda | busy      4% | read      12 | write      3 | avio    4 ms |
DSK |         sdb | busy      3% | read      13 | write      7 | avio    3 ms |
NET | transport   | tcpi      31 | tcpo      10 | udpi       0 | udpo       0 |
NET | network     | ipi       32 | ipo       10 | ipfrw      0 | deliv     31 |
NET | eth0     0% | pcki      48 | pcko      15 | si   38 Kbps | so   17 Kbps |

  PID  SYSCPU  USRCPU  VGROW  RGROW  RDDSK  WRDSK  ST EXC S  CPU CMD     1/1
 6234   1.82s   0.01s     0K     0K     0K     0K  --   - R 100% apache2
 6184   1.76s   0.03s     0K     0K     0K     0K  --   - R  98% apache2
 5993   1.77s   0.02s     0K     0K     0K     0K  --   - R  98% apache2
 6100   1.74s   0.04s     0K     0K     0K     0K  --   - R  97% apache2
 6186   1.71s   0.01s     0K     0K     0K     0K  --   - R  94% apache2
 5954   1.64s   0.05s     0K     0K     0K     0K  --   - R  92% apache2
 6229   1.62s   0.04s     0K     0K     0K     0K  --   - R  91% apache2
 5940   1.65s   0.00s     0K     0K     0K     0K  --   - R  90% apache2
  261   0.25s   0.00s     0K     0K     0K     0K  --   - S  14% kswapd0
 6422   0.01s   0.12s     0K     4K    28K     4K  --   - S   7% apache2
 5763   0.00s   0.04s     0K     0K     0K     0K  --   - S   2% mysqld
 6437   0.03s   0.00s   264K   264K    12K     0K  --   - R   2% atop
 5084   0.00s   0.00s     0K     0K     0K     8K  --   - S   0% kjournald

```

How can i find out what's causing this problem?
How can i find out why apache start to read that much and what file it's reading?

---

